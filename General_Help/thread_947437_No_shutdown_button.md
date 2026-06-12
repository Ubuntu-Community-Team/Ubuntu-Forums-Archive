---
title: "No shutdown button?"
date: 2008-10-14
forum: General Help
---

### Post by Los Frijoles on 2008-10-14
I have Ubuntu 8.04 installed on my work computer. For some reason, however, there is no shutdown or restart button in the Logout/Lock/Switch/etc screen which normally has a shutdown button. The only way I am able to shut down the computer correctly is to log out and then press the power button. On my server which also runs Ubuntu 8.04, there are shutdown and restart buttons. I currently am using the Glossy blue theme (orange started to hurt my eyes), but I am not sure that is really the problem since switching back to Human didn't fix it. I would really like my shutdown and restart buttons. Any suggestions?

---

### Post by alberto ferreira on 2008-10-14
Maybe you have tempered with the energy services?

See if those services are activated (acpi, apmd)

If that's not the cause one alternate way to shutdown your computer fast is opening a terminal in your session, and writing "sudo init 0".

---

### Post by iponeverything on 2008-10-14
See if you can re-add it to your task bar..

Right click on the taskbar -> "+ Add to Panel" 

Go down to "Power Button"  Applet and go to "add"

---

