---
title: "new guy needs a lil help"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by anothauser on 2009-02-05
Hi I am new to linux and I tried the Ubuntu Live cd. I loved it so I did the install on my laptop. It installed fine. I downloaded the updates for Ubuntu and while it was in the middle of installing, my laptop battery died. I plugged it in and tried to reboot but it wouldn't let me.

Is there a safe mode so I can try to reinstall the updates?

---

### Post by dstew on 2009-02-05
When you reboot, do you get the grub menu?

---

### Post by donkyhotay on 2009-02-05
Shortly after you first turn on your computer you will see a screen making mention of the GRUB bootloader. When you  see that press 'esc'. You will then see an option for recovery mode. Be aware that this will be CLI (command line interface) only. If you don't know what to do there try
```
sudo apt-get update
sudo apt-get upgrade
```
which will update everything available. If when doing so you recieve an error message advising you to type something along the lines of 'dpgk-reconfigure' or something similar to that (can't remember the exact wording) then type the command exactly as the computer tells you to then try the commands I gave you again.

---

### Post by anothauser on 2009-02-05
Thanks for the help. Esc did the trick. Problem solved. :D

---

