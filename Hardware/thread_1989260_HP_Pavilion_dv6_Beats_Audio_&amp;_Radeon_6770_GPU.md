---
title: "HP Pavilion dv6 Beats Audio &amp; Radeon 6770 GPU"
date: 2012-05-28
forum: Hardware
---

### Post by SageO on 2012-05-28
So this is the exact laptop I have [http://www.frys.com/product/6979847?site=sr:SEARCH:MAIN_RSLT_PG](http://www.frys.com/product/6979847?site=sr:SEARCH:MAIN_RSLT_PG)

I got rid of windows and threw ubuntu on it but now I can't hear out of any speakers (normal or beats audio speakers).
Also, I want to know how to utilize my HD Radeon 6770.
My brightness settings don't work either.
The laptop has an integrated intel graphics as well as the 6770.
Please help, thanks :)

---

### Post by aaricus on 2012-05-28
I have the same laptop and the same problems, no luck trying to solve them thus far.  Brightness is full blast, Audio is working but doesn't sound right - it was much louder under Windows.  I think my graphics are running through discrete Intel still - radeon is not working.

---

### Post by aaricus on 2012-05-28
I found this but it seems rather complicated for me.  [http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html](http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html)

---

### Post by SageO on 2012-05-29
> **aaricus said:**
> I have the same laptop and the same problems, no luck trying to solve them thus far.  Brightness is full blast, Audio is working but doesn't sound right - it was much louder under Windows.  I think my graphics are running through discrete Intel still - radeon is not working.

> **aaricus said:**
> I found this but it seems rather complicated for me.  [http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html](http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html)


I was able to fix the brightness problem with this post: [http://ubuntuforums.org/showpost.php?p=11445890&postcount=3](http://ubuntuforums.org/showpost.php?p=11445890&postcount=3)

After rebooting my sound seems to have returned, but I still don't believe this is my beats audio.

The "Additional Drivers" options say that the driver is activated but when I try to open the catalyst control I get this error.
```
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
 

 No AMD graphics driver is installed, or the AMD driver is not functioning properly.
 Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.
```I tried installing it manually as well following this guide [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


No such luck.

---

### Post by anonymous5 on 2012-05-29
> **SageO said:**
> So this is the exact laptop I have [http://www.frys.com/product/6979847?site=sr:SEARCH:MAIN_RSLT_PG](http://www.frys.com/product/6979847?site=sr:SEARCH:MAIN_RSLT_PG)

I got rid of windows and threw ubuntu on it but now I can't hear out of any speakers (normal or beats audio speakers).
Also, I want to know how to utilize my HD Radeon 6770.
My brightness settings don't work either.
The laptop has an integrated intel graphics as well as the 6770.
Please help, thanks :)

I have the same laptop also. Right now I'm only using the integrated intel HD 3000 GPU. I powered off the discrete GPU. The advantage is that there's less power consumption, and the laptop does not heat, and you won't hear the fan spinning anymore.
Here is how to turn it off : "sudo echo OFF > /sys/kernel/debug/vgaswitcheroo/switch". If you don't want to type it at each startup, you can make a script of it, place it in /etc/init.d/, make it executable and run "update-rc.d name_of_script defaults". The laptop should not be heating so much now.

For the bightness problem, I suppose you have grub2 installed. Here's what to do :
open the file "/etc/default/grub" and add the acpi_backlight kernel option like this :

GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor quiet splash"

now save the file, and run "update-grub" and restart.

---

### Post by SageO on 2012-05-29
> **anonymous5 said:**
> I have the same laptop also. Right now I'm only using the integrated intel HD 3000 GPU. I powered off the discrete GPU. The advantage is that there's less power consumption, and the laptop does not heat, and you won't hear the fan spinning anymore.
Here is how to turn it off : "sudo echo OFF > /sys/kernel/debug/vgaswitcheroo/switch". If you don't want to type it at each startup, you can make a script of it, place it in /etc/init.d/, make it executable and run "update-rc.d name_of_script defaults". The laptop should not be heating so much now.

For the bightness problem, I suppose you have grub2 installed. Here's what to do :
open the file "/etc/default/grub" and add the acpi_backlight kernel option like this :

GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor quiet splash"

now save the file, and run "update-grub" and restart.

Yep, I've fixed the brightness problems but I would still like to use my HD 6770M GPU.

---

### Post by Djerun on 2012-06-16
First hello to everyone this is my first post. I had the same problem with the graphics too. Last week I reinstalled Ubuntu. Now I'm on 12.04. After I installed the AMD post-release drivers, I got an error message "jockey blabla" something like this. I rebooted. The AMD card was working but I couldn't open the Catalyst Control Center. I opened a Terminal and typed:"sudo aticonfig --initial". After a second reboot all works fine now and you can switch the graphics in the Control Center. (I haven't tested it but it's in the options.) It might help somebody.

---

### Post by SeijiSensei on 2012-06-16
> **SageO said:**
> Yep, I've fixed the brightness problems but I would still like to use my HD 6770M GPU.

In the [BIOS]("http://ubuntuforums.org/showthread.php?p=11244073#post11244073") you can choose "fixed" graphics which should make the ATI adapter visible to Linux.  

You should probably also browse [this thread](http://ubuntuforums.org/showthread.php?t=1930450).

---

### Post by N0oki3 on 2012-06-16
Hello the guys. First of all. Check your BIOS if you have option in BIOS about hybrid graphics. If you do, set default(fixed hybrid graphics and not **dynamic** Radeon graphic. If you don't have that option than you **have to update your bios to latest version to get this option!** if you HAVE latest version of BIOS and you **cannot** set fixed hybridg graphics than you cannot use radeon graphic card !

Current solution for hybrid graphics intel/amd is this[guide](http://ubuntuforums.org/showthread.php?t=1930450) follow OP (post #1).

If you have 32-bit ubuntu precise (12.04 LTS) than after installing prerequisite packages (step 1) you have to apply this [patch](http://ubuntuforums.org/showthread.php?t=1969827) 
afterward continue with from guide 
```
sudo dpkg -i fglrx*.deb
```

---

### Post by Qlippoth on 2012-07-07
AMD/ATi also released a new Catalyst driver set for Ubuntu. I had no issues and the fan noise and battery life is (near) infinitely better!

I have NOT tried using the dGPU, I don't need it since Ubuntu is for work purposes.

- Qlippoth

---

