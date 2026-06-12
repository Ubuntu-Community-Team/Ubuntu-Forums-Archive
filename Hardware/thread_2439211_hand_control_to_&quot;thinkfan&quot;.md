---
title: "hand control to &quot;thinkfan&quot;"
date: 2020-03-24
forum: Hardware
---

### Post by manebule on 2020-03-24
I'm struggling to get thinkfan set up and working on my lenovo x250. I  have it installed, but I'm not convinced it is controlling the fan  speed. If I run: 
$ cat /proc/acpi/ibm/fan 

in the Terminal, I get: 
status: enabled 

But I'm under the impression it should be "disabled" when thinkfan is  controlling things. 

If I run: 

$ sudo thinkfan -n 

I get: 
WARNING: Using default fan control in /proc/acpi/ibm/fan


  How do I hand off control of the fan to thinkfan (where I can adjust the setpoints)?

---

### Post by lovix on 2020-05-09
I am having the same trouble.

---

