---
title: "Ubutu 8.10 new install problem with keyboard"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by danfs on 2009-10-12
I have just installed Ubuntu8.10 to a usb external hard drive. I have several issues. this is the 1st time I have tried linux. When I 1st put it up I selected the std USA keyboard. I have a HP zd7140us laptop. The numeric keyboard portion is not recognized. I have gone to systems preferences and tried to pick one that looke like it might work and have not found one. I looked at the hardware web site for this particular model and did not see any notes on it. The wireless will not work. The light never comes on when I boot up. There was something about this but it was unclear to me. The last item is when I installed it the Ubuntu repartitioned (probably my error) the entire disk that was not in use as an Ubuntu partition. Would I be better off redoing the installation completely? How can you do this? I can repartition the hard drive in XP which is still functioning but I suspect that might give me boot up problems.

---

### Post by hal10000 on 2009-10-12
> The numeric keyboard portion is not recognized.
Did you press the [NUM] key?. In the settings it can be configured to lock this key on login.

> The wireless will not work
Can you tell anything about manufacturer and/or model of your card?
Open a terminal window and type:
[COLOR="Red"]lspci[/COLOR] (if you have a pci wireless card)

or

[COLOR="Red"]lsusb[/COLOR] (if your card is usb)

post the output of the command(s) here (you can mark the output with your mouse and paste it with the middle moude button)

> he last item is when I installed it the Ubuntu repartitioned (probably my error) the entire disk that was not in use as an Ubuntu partition. Would I be better off redoing the installation completely? How can you do this? I can repartition the hard drive in XP which is still functioning but I suspect that might give me boot up problems

Post the output of the commands 
[COLOR="Red"]mount [/COLOR] and [COLOR="Red"]sudo fdisk -l[/COLOR] (this is a lower-case L, not a one) so we can see how your harddisk is partitioned.

---

