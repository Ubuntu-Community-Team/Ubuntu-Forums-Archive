---
title: "LiveCD hangs during boot with nVidia GeForce FX 5200 AGP"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by jinjanjaa on 2009-05-24
hello every1,

i hav bin having this prob since i tried booting gusty and it continues till jaunty to-date. ubuntu livecd hangs during the boot process when the progress bar starts filling up. it hangs sumwhere around when the progress bar is 1/4th filled. when the splash is disabled it hangs when ubuntu loads hardware drivers and it emits sum junk of code. sometimes the junk of code stops while sumtimes recurring junk of code keeps coming in until i restart. nothing else works.

hardy works fine for me. miraculously it doesnt hang during hardware drivers loading stage.

the problem is due to my graphics card geforce fx5200 because ubuntu boots perfectly well when i boot from my on-board card. i want to ubuntu to work with my fx 5200 card for activating compiz-fusion and other graphics involving stuff. especially i want to use jaunty and following releases without having any problems.
 
i hav tried variety of things like adding "acpi=off"
"agp=off" "nolapic" etc. i hav tried safe graphics mode. i hav tried many more routine things. i hav searched a thousand times abt this issue, over the internet. a few forums had the issue posted with no solutions. 

my specs:
nVidia Geforce FX 5200 AGP
Pentium IV processor dual-core 2.80, 2.79 GHz
768 MB of DDR RAM
Mercury PI865GM Motherboard with Intel 865 Chipset 96mb memory

Thanks in advance

---

### Post by jinjanjaa on 2009-06-09
sum1 pls answer........???

---

### Post by OpenFish on 2009-06-09
the “alternate installer” cd is ur best bet not nearly as plesant expiriance as the live cd but will almost surtanly work

btw i'm shore u can find it but just in case

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by jinjanjaa on 2009-06-09
I am really sorry that i forgot to mention  this in my first post.......

i tried the alternate install too. it ud install well but wont boot. it hangs during boot after install. givs a kernel panic or emits a recurring junk of code.

the problem is with the kernel bcoz hardy (and its kernel) works perfectly well with live cd, install, boot etc. 

thx to openfish for a reply... but suggest me something else pls.

---

### Post by OpenFish on 2009-06-09
ummm..

```
 givs a kernel panic or emits a recurring junk of code.
```

emits a recurring junk of code.. such as.. i know a recurring junk of code can be scary but its there 2 help!

i dont want to be/seem rude but when my nVidia card was shiny and new i used to have to install with a alternat cd then it would boot try to load Xorg fail then go to a tui and i would get it to load the drivers then start X and gnome and away i would go in to shiny high spec compize 

the nVidia Geforce FX 5200 AGP ant that new tho.. so i'm thinkin ubuntu should be able to find the drivers..

sorry i'm not able to help but i'm not shore what to suggest..

---

### Post by diskord on 2009-06-13
I am having the exact same issue with the FX 5200 PCI card.

I have onboard video on the motherboard, if I remove the FX 5200 it is able to install and boot just fine, as soon as I put the 5200 back in the machine it has a kernel panic during the "Loading Hardware Drivers" portion of the boot.

---

### Post by jinjanjaa on 2009-06-14
i am not even able to get a clue on why this happens......

@ diskord
actually hardy works just fine for me but all others fail.....
is that the same 4 u diskord???

@every1
something about the hardy's kernel helps it to boot. but other kernels are problematic. Once i actually upgraded from hardy to intrepid via update manager and intrepid was able to boot thru the old kernel. So the problem is with the kernel and not the release

srry i think i shud hav mentioned this in the first post....

---

### Post by jinjanjaa on 2009-11-29
Hello every1,
the problem was very simple. i need to switch acpi off NOT in ubuntu command line but in the BIOS. wenever we enter acpi=off in the boot options the bios settings supersede them which means acpi is on even if specified off in ubuntu boot command line.

now i switched off acpi in the bios and all ubuntu versions work. however am on a dual boot with xp and to boot xp i need acpi off.
but am not able to switch off ubuntu with acpi=off. anyone know any fix or workaround pls tell me.

THANKS TO EVERYONE WHO REPLIED!!!!!!:P:P:P

---

### Post by Paulis321 on 2010-12-04
I had the same problem after buying a Nvidia 7600GT 512MB (AGP) card. My motherboard is Biostar 865GV Micro 775. It has an onboard Intel extreme graphics 2 chip which goes upto 96MB. I had no issues with it and I was able to install Ubuntu with it.But when I disabled it(and gave the priority to my agp card) and tried Ubuntu 10.04 and 10.10, both gave me a kernel panic and some hexadecimal values on the screen. 

So after few workarounds I found the solution. I have seen this issue in so many forums. So if you happen to find it please be kind enough to share it with others as well,

1. First you need to install Ubuntu 10.04 or 10.10 from your onboard VGA. (and Switch ON the ACPI from BIOS)

2. Now in the desktop goto System > Administration > Additional Drivers

3. It will eventually update its driver database will show up proper drivers for your card. Click on Nvidia Accelerated Graphics Driver[Current] (Recommended) and activate it. It will automatically download the drivers and will ask for you to restart your system.

4. Hold on there. Now open up a terminal and run this command,

[CENTER]```
gksudo gedit /etc/modprobe.d/blacklist.conf
```[LEFT]5. Now add the following line to it and save it.
[CENTER]```
blacklist intel_agp
```[LEFT]6. Now restart your computer and after booting ubuntu it'll automatically drop you to a shell. Now run the following command,
[CENTER]```
sudo nvidia-xconfig
```[LEFT]7. Now simply do a sudo reboot and reboot your machine and goto your BIOS setup.

8. Now disable you onboard vga and give priority to your AGP card when booting (this might be different from your BIOS setup) and shutdown your system

9. Plug your monitor's cable to your AGP card and boot up your machine.

[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]
10. Voila! You'll see you AGP card's working finally!

Please make sure to share this with others who are having the same problem. Good Luck!

Sahan

---

### Post by jinjanjaa on 2010-12-06
Thanks a lot Paulis321! Your solution absolutely works!! But I'd like to better your how to as follows:

1. Turn off ACPI in BIOS
2. Open *"/etc/modprobe.d/blacklist.conf"* in *gedit* with root permissions
3. Add line *"blacklist intel_agp"* anywhere on the file. Save file
4. Reboot
5. Turn on ACPI in BIOS
6. Save and Boot


There is no need to change cables and change the card settings in BIOS. Simple ACPI disabling and enabling would do.

---

### Post by Bahokan on 2010-12-26
Paulis, 

I have a Biostar 865gv micro 478, almost similar to yours. And Nvidia GeForce FX5200. For the last 2 days, I have been struggling to install Ubuntu 10.10 with no success. I saw your post and the problems you had are exactly the same as mine. A bunch of error text on a black screen. Having read your post I tried to use the onboard card and disabled Nvidia in the Device Manager. However, after re-starting the computer, the screen went completely black until XP Welcome screen, after that point it went back to normal. How did you manage to use the onboard card and did you do anything in BIOS to get it work?

---

