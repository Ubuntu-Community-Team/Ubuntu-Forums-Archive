---
title: "Problems With Grub"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by hotrod1 on 2006-01-23
Well I am a fairly experienced Windows guru but now I want to explore the world of Linux and I want to try learning on Ubuntu. Anyway, when I try to install Ubuntu and then I restart I get an error that Grub can't load or something around that and it hangs there. I was able to narrow it down to a problem with the MBR since the only way I am able to fix the problem is by copying over the default MBR from my XP cd. I did some searching around and I tried to follow one post that said to use the command grub-install /dev/hda but that didn't work out. I really apreciate the help and I can't wait to start exploring Linux. P.S I attached a copy of Grub's menu.lst file.

---

### Post by lha on 2006-01-24
Can you post the output of "sudo fdisk -l"? (Use linux fdisk.)

Information on how you installed and tried to get dual-booting would be useful.

What kind of problem you encountered when reinstalling grub?

---

### Post by hotrod1 on 2006-01-24
I know now what the problem is and what aproximately I have to do but I need to know how to edit my /boot/grub/device.map in the shell in the rescue mode of the installation cd. What I tried to do was mount my floppy drive then install grub on it but when grub asked me if the contents in the device map were correct, I canceled the installation of grub becuase it only listed my floppy drive and main paritition that I use for XP so I would just have to add my Ubuntu parition to the device list and then I should be done but I am not sure how to do so. Thanks

Mike

---

### Post by lha on 2006-01-25
[QUOTE=hotrod1]I know now what the problem is and what aproximately I have to do but I need to know how to edit my /boot/grub/device.map in the shell in the rescue mode of the installation cd. What I tried to do was mount my floppy drive then install grub on it but when grub asked me if the contents in the device map were correct, I canceled the installation of grub becuase it only listed my floppy drive and main paritition that I use for XP so I would just have to add my Ubuntu parition to the device list and then I should be done but I am not sure how to do so. Thanks

Mike[/QUOTE]

```
sudo nano /boot/grub/device.map
```.

---

