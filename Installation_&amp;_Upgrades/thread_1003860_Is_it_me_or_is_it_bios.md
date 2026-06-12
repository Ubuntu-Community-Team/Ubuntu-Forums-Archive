---
title: "Is it me or is it bios?"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by theweakend on 2008-12-06
I recently got my hands on a used computer and decided, heh what better thing to do with it then install ubuntu on it, little did i know this would end up making me feel like a complete idiot. so i i get downloading the new ubuntu 8.10 iso. I'm excited, ok i follow [this]("http://lifehacker.com/software/mac-os-x/mac-tip--how-to-burn-an-iso-or-dmg-file-to-disc-251758.php") guide to burn my iso (i mostly come from a linux/windows background) and thats done ok now the computer. i booted hit "del" and required the bios password huh well not knowing the password i just opened the box and took out that little cell battery and went for a smoke and came back popped it back in and rebooted and hit "del" again first thing i did was hit "Load Optimized Defaults" in my "Phoenix - AwardBIOS CMOS Setup Utility" and arranged the boot order to floppy cdrom hdd0 hit "Save & Exit Setup" popped in my ubuntu install cd and was given the "Boot from CD :" prompt i hit enter odd it didn't work (i use a usb keyboard i thought it might be worth mentioning because this is a old computer with ps2 ports in the back, does it even support usb keyboard and mouse i would think so because those were the usb devices used to install windows on it) instead i am thrown a rather retched "GRUB loading, please wait... Error 15." heh ok thats all good it brings back memories form my gentoo days. But the fact of the manner is this What ever live cd i put in does not boot tried gparted tried kubuntu and ubuntu and the issue remains i even tried different boot orders with the bios but again no dice. If anyone of great knowledge knows how to fix this very simple (and embarrassing) issue then please let me know because this was just going to be a simple 2 day project so i have a computer to develop on but now its turning into a 2 day mistake, and sorry no i have know clue what hardware it has as i can't boot to give you a lspci and yes it works as i have seen it run with windows and linux at some point in my life. Thanks in advance.

P.s. yes i do like to tell stories

---

### Post by kerry_s on 2008-12-06
go into your bios and check the settings 1 by 1, turn on the legacy usb support, select no for plug & play aware os, etc...

did you check the disk? it should be option on the installer, it might be as simple as a bad burn.

---

### Post by theweakend on 2008-12-06
thanks for the replay 

pnp off by default

just checked the iso and the md5 was correct

still no dice :(

i seen a setting for "USB keyboard" i thought i had it for sure that time, but no luck

any other ideas are greatly appreciated

---

### Post by frankleeee on 2008-12-06
What is the ram on this computer.

---

### Post by theweakend on 2008-12-06
good question, it has 256mb which may be an issue...

---

### Post by frankleeee on 2008-12-06
> **theweakend said:**
> good question, it has 256mb which may be an issue...

So with that ram you will have to use the alternative iso download. Since I am not a true geek it was hard to read your post and find the actual problem. It sounds like your using the Alternative from your description is this so. So I notice you say live CD that will not install with that amount of ram.

---

### Post by theweakend on 2008-12-07
Well turns out ram had nothing to do with it the cd rom was fried thank you for all your help, i greatly respect a forum that replies the day i post.

---

