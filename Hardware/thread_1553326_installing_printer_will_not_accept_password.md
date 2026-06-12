---
title: "installing printer/ will not accept password"
date: 2010-08-14
forum: Hardware
---

### Post by neptasur on 2010-08-14
Hello,

I am installing a Lexmark printer in Ubuntu 9.10.  I have the driver extracted.  When I run it, a dialog box opens saying that root privileges are required.  I enter my root user password in the dialog box, but it will not accept it.  I logged into the terminal as root using "sudo -i" (and also used sudo su at other times) in the terminal.  I can log in as root in the terminal, but it doesn't change anything with this dialog box for the printer driver.

Any ideas?

Thank you,

Neptasur

---

### Post by clrg on 2010-08-15
Have you tried loading the driver with root privileges directly? For example, "sudo install.sh" or "sudo make install" or whatever command is required in this case.

---

### Post by neptasur on 2010-08-15
I will try that.  It's been a while since I've used Linux commands, so I'll have to figure out the syntax.

Thank you,

---

