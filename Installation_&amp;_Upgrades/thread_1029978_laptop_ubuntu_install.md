---
title: "laptop ubuntu install"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by Messyhair42 on 2009-01-03
I'm attempting to install Ibex on my dell inspiron 1000 laptop. i already have windows xp on and i'm willing to take it or leave it. i have the disk in the drive and my bios is set to boot to the cd drive. i've tried this a few times already and everytime i start the computer something different happens, sometimes windows boots or it takes me to the bootloader, sometimes i get through the ubuntu screen where i choose to install, the first time i got all the way to the partition menu before it locked up, now after the ubuntu screen i get error messages such as 
```
buffer I/O error on device sr0, logical block XX
end request: I/O error, dev sr0 sector
```
and i'm not changing anything between attempts, just power on/power off

i'd be happy if i could fix this and like i said i don't need windows.

---

### Post by smurfgod on 2009-01-04
dban the whole damn thing.that will whipe out your hdd.put in boot disk and your on your way.

smurf:D

---

### Post by abn91c on 2009-01-04
> **Messyhair42 said:**
> I'm attempting to install Ibex on my dell inspiron 1000 laptop. i already have windows xp on and i'm willing to take it or leave it. i have the disk in the drive and my bios is set to boot to the cd drive. i've tried this a few times already and everytime i start the computer something different happens, sometimes windows boots or it takes me to the bootloader, sometimes i get through the ubuntu screen where i choose to install, the first time i got all the way to the partition menu before it locked up, now after the ubuntu screen i get error messages such as 
```
buffer I/O error on device sr0, logical block XX
end request: I/O error, dev sr0 sector
```
and i'm not changing anything between attempts, just power on/power off

i'd be happy if i could fix this and like i said i don't need windows.

reset the bios back the way it was, on dells you dont have to access the bios to boot from the cdrom. Just reboot the laptop when the dell logo appears look in the right upper corner for the prompt to press**[COLOR="Red"] f12[/COLOR]**, you have to be quick it is there for about [COLOR="red"]5 seconds[/COLOR]. then select at the next screen boot from cdrom. 
Those errors are usually from a bad disk, burn at lower speed, make sure the disk is scratch free and clean, use a CDR if you can. Also reboot to wwindows and THEN restart from the windows to the live cd. do not hardboot/poweroff

---

### Post by Messyhair42 on 2009-01-04
I took smurfgod's advice and dban'd the notebook, but durring the ubuntu install i still end up at the same place. buffer i/o error... i'm thinking of requesting professional help since i'm at a dead end.

---

### Post by abn91c on 2009-01-04
> **Messyhair42 said:**
> I took smurfgod's advice and dban'd the notebook, but during the ubuntu install i still end up at the same place. buffer i/o error... i'm thinking of requesting professional help since i'm at a dead end.
you did not need to reinstall, now you are stuck, those I/O errors are usually a bad cdrom burn or from scratches dirty disks. I also have an inspiron 1000 and like I said you need to reset the bios back the way it was and use the Dell f12 option to get to the cd and if they are not gone use the dell diagnostic utilities. Too many users when they cant help you they will tell you to reinstall when 90% of the time is not needed. read here: [http://ubuntuforums.org/showthread.php?t=1010875](http://ubuntuforums.org/showthread.php?t=1010875)

---

### Post by smurfgod on 2009-01-04
i just wanted to say sorry.i have always just dban and reinstall.sorry if i didnt help..

smurf   :(

---

### Post by Messyhair42 on 2009-01-05
i thought it might have been the disk after my last attempt so i burned a new disk with kubuntu heron and it barely does anything. i'm not going to give up, have faith in linux

---

### Post by Messyhair42 on 2009-01-06
i have two more ideas i could try. the first being the more painful. i could install windows XP AGAIN and use wubi, or i could turn a usb key into a boot disk. i'm more tempted to try the second but i dont think my laptop can boot to usb (one of my boot options is USB diskette, but does that mean any usb-bootable device?)

---

### Post by abn91c on 2009-01-06
> **Messyhair42 said:**
> i have two more ideas i could try. the first being the more painful. i could install windows XP AGAIN and use wubi, or i could turn a usb key into a boot disk. i'm more tempted to try the second but i dont think my laptop can boot to usb (one of my boot options is USB diskette, but does that mean any usb-bootable device?)

yes on the inspiron 1000. I use wubi and kubuntu 8.10 in mine, if you have 512mb ram it will be faster that XP. You will not get desktop effect because the SIS video card will not support it however KDE4 plasmoids will not be affected.There are many guides in the forums on how to make an USB install key.

---

### Post by eatberrys on 2009-01-06
Is the ISO your burnning from good ?

---

### Post by Messyhair42 on 2009-01-06
I know my disk is good b/c i just used it to install ubuntu on another desktop, i also have the Heron release of Kubuntu but my laptop dosen't want to read that disk (my optical drive is in bad shape and dosen't like to cooperate often, especially with burned cds). what i'm more interested in is what the error messages i'm getting mean, if it's a bad spot on my hard disk or something else.

---

### Post by abn91c on 2009-01-06
no the HDD is probably Ok, I've seen those errors trying out live cd's and always was a bad disk, most of the time with cDRW's also burn at lower speed. Aslo try cleaning out the inside of the cd/dvddrive, maybe the laser lens is dirty

---

### Post by Messyhair42 on 2009-01-07
Ha, i blasted the cd drive with canned air and it fixed the major problem, install still wouldn't work b/c i got language/timezone etc. error code 127. and at one point i still got the buffer I/O error screen but it went directly to live session desktop.

I cleaned out four and a half years of dust from that machine, and it makes a difference, especially with how it reads cds

---

### Post by Messyhair42 on 2009-01-07
it's working better but still funny.
i got ubuntu almost installed, the install stalled at 94% for several hours, i could hear my cd drive clicking, trying to find the disk so i stopped it, it wouldnt restart so i used dban again and whenever i try the ubuntu disk it tells me delldiag does not exist. i tried my kubuntu disk and it gets by that fine, except the kubuntu installation always stops before the installation is complete. what's up with this?

---

### Post by Messyhair42 on 2009-01-09
I'm going to try a new .iso CD with kubuntu. what i was wondering is if there is a way to install GRUB before kubuntu?

---

### Post by cmay on 2009-01-09
i have had a lot of trouble with the iso of ubuntu lately and there is a known bug in the installer. but i found out that if i use the unetbootin utility it works flawlessly so if you have any chance of getting your iso on an usb stick and boot from this using unetbootin or any of the tutorials on pendrivelinux.com could maybe work too. i think maybe it could be the solution  you are lookin for. other than that i am blank on ideas to help you. sorry.

good luck.

---

### Post by Messyhair42 on 2009-01-09
unfortunatly it's an older laptop and can't boot from a usb stick, i might try the old cd version b/c it uses less memory

---

### Post by galenanderson on 2009-01-09
I have also seen this happen because of an error on a disk. Try burning a new disk and start over.

---

### Post by Messyhair42 on 2009-01-10
Is it possible to use another computer's disk drive to install b/c i've done everything else i can think of and it wont complete the install?

---

### Post by Messyhair42 on 2009-01-25
i couldn't get ubuntu or kubuntu to complete a successful installation so i tried openSuse and got a completely differnet error. when i tried Kubuntu it couldn't configure the boot loader. when i tried OpenSuse it couldn't create swap. i may just have to live with windows, sad story but true.

---

### Post by Guille Damke on 2009-01-25
Hi
Two things that may help. First, make sure you have free space in your disk (I'm sorry, I know it sound stupid, but we have to discard these simple things first). Also, run the scandisk tool in Windows on the disk that you want to install Ubuntu, then try the install again. 
Can you post the message that you got? It can help people to figure out the problem.

---

### Post by Messyhair42 on 2009-01-25
i used dban on the laptop to clear it completely so i dont have windows anymore. when i try kubuntu it gets to about 85% of installation and stops while it says "configuring boot loader" and when i try opensuse...actually i was writing this while trying to install opensuse and it worked, my laptop runs again.

---

