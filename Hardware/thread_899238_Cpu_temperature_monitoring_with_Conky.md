---
title: "Cpu temperature monitoring with Conky"
date: 2008-08-24
forum: Hardware
---

### Post by jay buddhika on 2008-08-24
Hello Folks could anybody give me the scripts required to configure

a) CPu Temperature 
b) RPM of system fan and casing fan
c) Hardisk temperature

Conky should display the figures in the following formats

Current   Minimum   Maximum

---

### Post by Sam Lars on 2008-08-24
For CPU, I use this code:
```
${execi 5 acpi -t | grep "Thermal 1: ok, " | cut -c21-24}°C
```
For HD, I use this code:
```
${execi 5 netcat localhost 7634 | grep "320JI|" | cut -c27-28}.0°C
```
For the fan, you could use something similar to my CPU code, using a command that will list your fan speed.
I'm not sure how you want the max/min to be done.  I'm sure you could run a script through Conky that would remember the values... and you have me interested enough to try it.
For a list of variables you can use in Conky, see [this page]("http://conky.sourceforge.net/variables.html").

---

### Post by tturrisi on 2008-08-24
Depends on what cpu you have, else the cut numbers will vary.  Also, Conky has inbuilt variables to display cpu & fan speeds. For my core2 laptop I use:

${execi 300 sensors | grep Core}

---

