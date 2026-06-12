---
title: "Windows XP Pro &amp; Ubuntu 5.04 Dual Boot Question"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by I3roknI3ottle on 2005-06-08
Currenty I have 3xdrives in my computer. 2xHardrives, 1xCD/DVD Drive

1x 80GB with Windows XP
1x 80GB with Ubuntu

Motherboard = Chaintech 7NJL6

How would I have to set things up towhere when I boot up it ask me if I want to go into windows or ubuntu.  I know this is possible because I've done it with Mandrake 10.1 & Windows, and Ive had Windows on both hardrives and it asked me what windows to boot too.  Any help appreciated.

---

### Post by PhilippWollermann on 2005-06-08
[QUOTE=I3roknI3ottle]Currenty I have 3xdrives in my computer. 2xHardrives, 1xCD/DVD Drive

1x 80GB with Windows XP
1x 80GB with Ubuntu

Motherboard = Chaintech 7NJL6

How would I have to set things up towhere when I boot up it ask me if I want to go into windows or ubuntu.  I know this is possible because I've done it with Mandrake 10.1 & Windows, and Ive had Windows on both hardrives and it asked me what windows to boot too.  Any help appreciated.[/QUOTE]
 Hi!

What is your current situation? Are you able to boot both operating systems, or can you only boot Ubuntu / only Windows? If you can boot both, how do you switch between them?

Philipp

---

### Post by 25738 on 2005-06-08
i have the same problem. i dont think you can do it unless yuo
comple your kerenl.

ok.

bye.

[http://www.ubuntuforums.org/ewreply.php?do=newreply&noquote=1&p=204917#](http://www.ubuntuforums.org/ewreply.php?do=newreply&noquote=1&p=204917#)
Whistle

taht was supoosed to be a simlie but they dont wrok no my computer.
rr

---

### Post by PhilippWollermann on 2005-06-08
[QUOTE=25738]i have the same problem. i dont think you can do it unless yuo
comple your kerenl.[/QUOTE]
Why would you have to recompile your kernel? This should be one simple GRUB re-configuration.. :)

---

### Post by mohaham on 2005-06-08
you dont have to recompile the Kernel to get a dual boot option..
Please explain your situation further so that others can help you.
Do u have GRUB installed on the MBR
if so you just need to edit /boot/grub/menu.lst  file to dual boot..
or u can install grubconf utility to edit using GUI.

---

### Post by TeeJay on 2005-06-08
[QUOTE=PhilippWollermann]Hi!

What is your current situation? Are you able to boot both operating systems, or can you only boot Ubuntu / only Windows? If you can boot both, how do you switch between them?

Philipp[/QUOTE]


You might try here [http://ubuntuguide.org/#addwindowsentrygrubmenu](http://ubuntuguide.org/#addwindowsentrygrubmenu) it has info on adding boot options for grub.

---

### Post by Curlydave on 2005-06-08
Get your Linux HD to be primary. (For me whicher was plugged in first was primary, so I unplugged my winHD, booted up, shut down, plugged it back in and the Linux HD was primary.)

Install GRUB onto the MBR of your Linux drive.

Open /boot/GRUB/menu.list, and find the section pointing to your windows drive. Add the following lines below it:

> map (hd0) (hd1)
map (hd1) (hd0)

(I'm sorry for the generic, crappy instructions. This is what did it for me, and I did it upon the installation of linux. This probably won't work exactly for you, and you may be using a single partitioned HD. I do not know how to install GRUB post install. Sorry)

---

### Post by I3roknI3ottle on 2005-06-08
currently when i switch between Windows XP and Ubuntu I unplug the IDE cable from one to another.  But I want to be able to just select what operating system to boot too.

---

### Post by crane on 2005-06-08
[QUOTE=I3roknI3ottle]currently when i switch between Windows XP and Ubuntu I unplug the IDE cable from one to another.  But I want to be able to just select what operating system to boot too.[/QUOTE]


Did you insyall windows, then istall Ubuntu? Or did you install one, unplug the ise cable, plug ing the other adn the install?

Duel booting with ubuntu and windows has always been painless for me.

---

### Post by I3roknI3ottle on 2005-06-08
I did the second option, I had Windows XP installed on my 80GB hardrive, and was reading up on linux, I unplug my hardrive and hooked up my second 80GB hardrive and Installed Ubuntu on it.

---

### Post by PhilippWollermann on 2005-06-09
Umm.. I see one problem approaching: You have installed Windows, the harddisk was plugged in as primary harddisk. Windows thinks, it's installed on the primary harddisk now. You have installed Linux after you swapped the harddisks, and thus you installed Linux on the primary harddisk *too*. So all devices in fstab, grub.conf, etc. refer to /dev/hda or (hd0). If you connect both harddisks, you have to reconfigure one OS - either tell Windows, that it's now running from the secondary master (I guess the only place you have to change is C:\boot.ini, but I'm not sure) or change fstab and the grub menu.lst on Ubuntu. It would have been easier, if you had both disks plugged in during the installation of Linux.. ^^

Philipp

---

