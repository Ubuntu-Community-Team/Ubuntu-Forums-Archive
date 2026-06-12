---
title: "blinkingcursor after install"
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by helmet on 2006-01-20
so i have my main windows install on two seagate 160 in raid 0, and i have another seagate 80 for kubuntu. i boot from the disk, everything goes smooth, finds all the drives, and i do auto setup for partitioning on the 80 gig, makes a 75 ext3 bootable for / and 3 for swap. okay fine with me. install...blah blah blah....reboot, hit F8 on my Asus P5AD2 premium mobo to boot to the 80 gig and it just gives me a blinking cursor. i've tried a bunch of different setting for the sata and Raid stuff in the bios, but no dice. if i boot normally to the raid, it just load windows no problem

what am i doing wrong??


EDIT okay rather my windows doesn't boot at all...i tried the install again and now i get this Grub Error 17 at stage1.5

---

### Post by Mustard on 2006-01-20
Error 17 on grub would mean this..

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

I couldn't say much more, as I'm not sure how to proceed, but I'm hopeful at least knowing what the error means will be helpful in troubleshooting the problem.

---

### Post by helmet on 2006-01-20
well i just unplugged my other 3 hard drives so it only had one place to install grub, the 80 gig with kubuntu on it, which is where i wanted it to go. i did a fixmbr so now my windows boots and my kubuntu. w00t!

---

### Post by helmet on 2006-01-20
well i guess i jumped up and down too soon. i can boot to windows, but when i try to boot to kubuntu, it gives me some fun errors involving mounting. this is after i plugged the hds back in. it would boot fine with them unplugged. i tried disabling them in the bios and using IDE or other settings for them but no dice...

since those hard drives weren't there for install, does it think this is hda when really it's like hdc or something. do i have to edit some files? it does kick me to a command shell

EDIT:well on the install it recognizes everything as sd*, and the hd with kubuntu on it is sdc, underneath two identical drives of the same everything (my raid drivers). with #1 primary, bootable partition and #5 swap partition. i was trying to edit the GRUB lines to make it go to the right drive but i couldn't figure it out. any suggestions??

---

