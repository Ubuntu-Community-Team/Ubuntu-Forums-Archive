---
title: "Overheating in Toshiba Satellite A300"
date: 2010-01-04
forum: Hardware
---

### Post by DreamerHxC on 2010-01-04
Hey everybody,

I just installed Ubuntu Karmic and I noticed that the temperature is very high (around 50ºc) compared to the same system using Windows 7 (44ºc).
Is there any known problem with Karmic and ACPI or false temperature or something? I did not configure anything special, so maybe I'm missing something.

Thanks a lot in advance!

---

### Post by hornedfiend on 2010-01-27
Hi, 

I've got the same problem with my A300 PSAGUE. I can't use Ubuntu because of this issue. The area around and the pad is so hot it burns my hands. Windows 7 doesn't cause this issue. Anybody got any ideea?

Thanks.

---

### Post by ahmadz1991 on 2010-03-27
Same problem here... the laptop becomes really hot, and a BBQ smell comes out :( 

any help please.

---

### Post by pricorp on 2010-05-03
On a Toshiba U500, I suspend and start the computer again. Once restarted, the fan start working and maintain a temperature around 43°C.

Here is the terminal command to suspend:

sudo pm-suspend

HTH

---

### Post by cbecker78 on 2010-05-03
the solution in 9.1 was to install lm-sensors and add "acpi_OS=Linux" after quiet splash in the grub options.  Will probably be the same for 10.04.  You may have to excape the quotes with triple slashes, ie \\\

---

### Post by kayovas on 2010-05-16
I have same problem with Toshiba Satellite Pro A300

> **cbecker78 said:**
> the solution in 9.1 was to install lm-sensors and add "acpi_OS=Linux" after quiet splash in the grub options.  Will probably be the same for 10.04.  You may have to excape the quotes with triple slashes, ie \\\

There isn't menu.lst in Ubuntu 10.04 [where to place]("http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html") "acpi_OS=Linux". :(

PS. Sorry for my bad english.

---

### Post by strikoo on 2010-05-16
sudo gedit /etc/default/grub

Find this line:
GRUB_CMDLINE_LINUX=""
and change it to:
GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"

Save

sudo update-grub
sudo reboot

It should work now after reboot.

---

### Post by kayovas on 2010-05-18
@[strikoo]("http://ubuntuforums.org/member.php?u=453333")

Thank You Very Much! Grate community, grate distro!

---

### Post by kayovas on 2010-05-27
Unfortunately, it doesn't work. :( I still have the same issue with CPU fan and overheating.  I did everything like strikoo mentioned... :(

---

### Post by strikoo on 2010-05-29
> **kayovas said:**
> Unfortunately, it doesn't work. :( I still have the same issue with CPU fan and overheating.  I did everything like strikoo mentioned... :(

you need to understand that toshiba doesn't support linux

---

### Post by kayovas on 2010-10-05
I've tried Mandriva and a friend of mine has tried Fedora - no problem with the CPU's fans!
Maybe, just maybe, the problem is in Ubuntu.
Now, I'm with Ubuntu RC 10.10 and the problem is still there...:(

I like Ubuntu, but...

---

### Post by tadaskr on 2010-10-06
I have Toshiba satellite a300 and i used 10.04 and 10.10 with acpi_osi=Linux everything working and my laptop fan working nice. but in 10.10 laptop is cooler than in 10.04. maybe there is problem with your laptop

---

### Post by kayovas on 2010-10-11
@[tadaskr]("http://ubuntuforums.org/member.php?u=1120893")
Thank you! It works!

---

### Post by hornedfiend on 2010-10-11
Ubuntu 10.10 seems to have solved the overheating problem. My CPU is now at 43-44 degree when idle, and 56-57, max 60 in some thread. 70 in full load. It's fine now! Yey! Finally!

---

### Post by kuric on 2011-10-20
> **hornedfiend said:**
> Ubuntu 10.10 seems to have solved the overheating problem. My CPU is now at 43-44 degree when idle, and 56-57, max 60 in some thread. 70 in full load. It's fine now! Yey! Finally!

I wouldn't consider this fine. Close to 60ºC isn't a good average temperature, that's too high. Same thing on my netbook too, so I'll let Ubuntu far, far away from it.

---

