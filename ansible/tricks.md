# ansible tricks

###### only for professionals

#### include\_tasks filename *by fact*

this one is great for separating and modulating tasks by os. you can set
include\_tasks filename with *a variable*

    - name: kick off os-based install tasks
      include_tasks: "install-packages-{{ ansible_os_family }}.yaml"

###### gotchas

  - include\_tasks does not allow for list, only one filename arg
    
      - you will receive \`ERROR\! unexpected parameter type in action:
        \<class 'ansible.parsing.yaml.objects.AnsibleSequence'\>\` if
        you try to provide more than one filename to an
        include\_tasks.... task

  - you'll want to set a default if you can for the filename or else if
    your var doesn't match to something it'll fail your play. for me,
    rhel and debian based os'es cover 98%
