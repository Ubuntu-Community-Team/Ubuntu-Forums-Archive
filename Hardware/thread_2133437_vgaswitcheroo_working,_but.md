---
title: "vgaswitcheroo working, but"
date: 2013-04-08
forum: Hardware
---

### Post by evanbas on 2013-04-08
Hello,

I am using HP Pavilion dv3 2315. My laptop have two VGAs, ATI Mobility Radeon HD4550 and Intel Integrated Graphics.
Due to overheating issues, I have to use vgaswitcheroo to turn off ATI.
So far, switching works fine, but when I try to leave a session, i.e logout, the system always crash, I can't switch to another tty and the only option is hard reset my notebook.
**dmesg** show long stack trace, along with last message : **[FONT=comic sans ms]Fixing recursive fault but reboot is needed[/FONT]**

Strangely, the crash won't happen if I turn on ATI again just before logout.

I've tried two different distros, ArchLinux and Ubuntu 13.04 , and the problem occured in both of them.

What should I do to fix this?

---

