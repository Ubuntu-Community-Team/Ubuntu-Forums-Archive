---
title: "Ubuntu 8.04  Full Install on USB FAILS to boot in Vista"
date: 2008-10-17
forum: General Help
---

### Post by rashhashan on 2008-10-17
Ok so i did [what pendrivelinux.com suggested ]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/")and tried to install a full version of Ubuntu 8.04 on a 4gb thumb drive....It suggested for me to....

[LIST=1]
[*]Unplug all internal drives
[*]Plug a USB key 4+ GB into computer
[*]Turn on and boot into the 8.04 install disk
[*]install as usual, and place the boot files in /dev/sda
[*]Reboot into Ubuntu off thumb drive
[/LIST]

i have tried this with back track 3 also

Ubuntu will boot but once it gets past the login screen it wont reach the desktop

And bt3 wont even boot...the Grub error reads Error 17

please help,
thanks:confused:

---

### Post by C.S.Cameron on 2008-10-17
I have installed Ubuntu to flash drive dozens of times.
I never bother with step 4 unless unless I am doing manual partitioning with the internal drives plugged in.
Usually when I encounter the problems you have, I find it is due to a bad install, scratched CD, or faulty flash drive.
Partitioning with 'use entire disk' seems to be the most fool proof.

---

### Post by rashhashan on 2008-10-17
> **C.S.Cameron said:**
> 
Partitioning with 'use entire disk' seems to be the most fool proof.

yea thats what i did...but so you think if i dont specify where to put the boot files...it might work? I tried to do it that way already and it said i had to select a location for the boot files...even using guided mode.
 Do you think it could be the way Vista is?

---

### Post by C.S.Cameron on 2008-10-17
If your flash drive will not boot with your HDD unplugged, Vista probably has nothing to do with it.
Sounds like grub is ok if you get to user name and password.
Have you tried fail safe mode after hitting 'Esc' at grub?
When you get as far as it goes does 'ctrl Alt F1' do anything?

---

