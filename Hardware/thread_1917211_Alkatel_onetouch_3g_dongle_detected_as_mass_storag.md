---
title: "Alkatel onetouch 3g dongle detected as mass storage."
date: 2012-01-29
forum: Hardware
---

### Post by saikrishna.m on 2012-01-29
ubuntu 11.04 fails to switch this from flash to modem automatically.It is working when i manually run usbmodeswitch from /lib/udev/usbmodeswitch.aftrer that i have to reconnect my modem.then networkmanager detects it as  modem only.Is is there any way to do this automatically. Linux geeks please help me.note:iam using tatadocomo gsm sim in this modem.

---

### Post by saikrishna.m on 2012-03-05
dear friends it is working with sakis3g software.

any body can u guide me how to write udv rules for this device,to solve this problem permanently :popcorn:

---

### Post by saikrishna.m on 2012-10-10
i got another solution from this forum .which  is working very fine for alkatel 3gdongle. I think it may also work for other dongle. try your luck

follow the following steps:
open the terminal:
become as a root 
then run this command in terminal:  sudo gedit /etc/modules

At the bottom of the file, make two new lines, like this:
usbserial
option
Then close the editor program and save it. Reboot the computer and hopefully you’ll be right :lolflag:

                                                                                     by 
                                                                                    m.saikrishna
                                                                                    rajahmundry

---

