---
title: "how do i install this?"
date: 2010-09-10
forum: Hardware
---

### Post by snypercore on 2010-09-10
hi,
very new to ubuntu, and i have desktop effects working and half decent gfx with a driver i think i installed through package manager, but the resolution is low and its a little jerky so i thought id try the ATI driver from the ATI site.

however i have no idea how to install it

im running ubuntu 10.4

driver is ati-driver-installer-10-8-x86.x86_64.run

thanks in advance

---

### Post by TNT1 on 2010-09-10
Did you search this forum?

---

### Post by hsoulen on 2010-09-10
> **snypercore said:**
> hi,
very new to ubuntu, and i have desktop effects working and half decent gfx with a driver i think i installed through package manager, but the resolution is low and its a little jerky so i thought id try the ATI driver from the ATI site.

however i have no idea how to install it

im running ubuntu 10.4

driver is ati-driver-installer-10-8-x86.x86_64.run

thanks in advance

Hi,

I don't run ATI but this will probably work:


[LIST=1]
[*]Copy the driver "ati-driver-installer-10-8-x86.x86_64.run" to a folder other than desktop (your home directory is fine)
[*]If you are running gnome (assuming this if you are on a default Ubuntu install) you will need to open a terminal and type "sudo gdm-stop"
[*]You should now be at a command line login prompt, login and then type "sudo su" and enter your password
[*]Change to the folder where you copied the driver in step 1 (example: "cd /home/yourname")
[*]Run the file "./ati-driver-installer-10-8-x86.x86_64.run" Note the "./" is very important
[*]Follow the prompts and enjoy the driver
[/LIST]
Hope this helps, good luck!

Hank

---

### Post by 73ckn797 on 2010-09-10
Did you go to System/Administration/Hardware Drivers and see what is recommended there?

---

