---
title: "Problem in swithching off the graphics card"
date: 2013-04-20
forum: Hardware
---

### Post by Mrunalinee on 2013-04-20
When I tried to follow the instruction in the thread [http://linux-hybrid-graphics.blogspot.in/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.in/2010/07/using-acpicall-module-to-switch-onoff.html), I could not run the following command
git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)
fatal: could not create work tree dir 'apci_call'.: Permission denied
What does it mean?
How can I proceed?
Thank you.

---

### Post by Yellow Pasque on 2013-04-20
It means you're in a directory that you don't have permissions to write to (so either use 'sudo' or change to a directory in your home folder).

---

### Post by marcoDallas on 2013-09-07
Hi, if you want you can do this via graphic interface, just use acpi_call_GUI.

Here's the wiki page: [https://help.ubuntu.com/community/HybridGraphics#acpi_call](https://help.ubuntu.com/community/HybridGraphics#acpi_call)

And here's the website of the program: [http://marcodallas.github.io/acpi_call_GUI/](http://marcodallas.github.io/acpi_call_GUI/)

---

