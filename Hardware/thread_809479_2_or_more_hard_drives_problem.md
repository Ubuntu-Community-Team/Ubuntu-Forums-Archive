---
title: "2 or more hard drives problem"
date: 2008-05-27
forum: Hardware
---

### Post by Crash 0verride on 2008-05-27
Hi,
Im currently running Ubuntu 8.04 on my 120GB HardDrive and I have run into a problem recently. I have Ubuntu 8.04 on my 120GB HardDrive and a couple of days ago I wanted to put in Windows XP Media Center Edition on my computer for a dual boot so I can use a program that isn't offered under Linux anymore because the developers of the program stop updating it buy the looks of it.
My motherboard is a ASUS a old 2002 and it says it offers the ability to have 4 hard drives but when i plugged in my 2nd 250GB Maxtor DiamondMax Plus 9 3.5 133HD Hard Drive it won't be seen by my computer. My friend has a near same model of it but his has a O/S on it and he plugged it into my computer and it ran fine. so my and my friend cracked it opened to try to find out what was wrong. We didn't find anything out of the question, other than the fact that my motherboard supports 4 hard drives and it has only 3 plugs comming from my power supply. So I unplugged one from my DVD drive and plugged it into my 2nd hard drive. Here is the currrent setup of my computer (The frame going down)

->CD Drive-> Master->Master on Second Ribbon Cable
->DVD Drive-> Slave-> Not Plugged In.->Slave on 2nd Ribbon Cable
->SYQUEST-> Don't know what this does
->Legacy Floppy->Master
->HardDrive 120GB-> Cable Select Enabled-> Master Slot on Ribbon Cable
->HardDrive 250GB-> CS Enabled -> Slave Slot on Ribbon Cable
->HardDrive 60GB->CS Enabled-> Not Attached to a Ribbon Cable/Power Supply

I have checked my BIOS and its not showing up on there but when I boot my computer i hear sounds comming from my hard drive(2nd one) as well as my computer on the ASUS splash screen when booting up is reasonably slower. When it is plugged in..

I don't know if this is enough information to diagnose the problem so just ask me if you need more information.
Right now im using WinXP Professional and Ubuntu on my 120GB Hard Drive and I would like to get the other one working

---

### Post by Crash 0verride on 2008-05-27
Bump

---

### Post by Crash 0verride on 2008-05-28
I still need help.

---

### Post by Crash 0verride on 2008-05-29
Anyone? well...I guess this is unsolved

---

### Post by didac on 2008-05-29
Sorry, do the noises you hear sound ominous? You know, like grinding . . .

Post the output of 

```
sudo fdisk -l
dmesg | egrep sd
```

Also, if you have grub installed, hit any key when the computer is going to boot, select the Ubuntu line, and edit it. Remove "quiet" and "splash" and boot. The booting process will output messages telling you what is going on. You can also read them later on, in case you don't enter the grub command boot line, by typing dmesg

And finally, put the disk jumper to slave, if it is a slave.

---

