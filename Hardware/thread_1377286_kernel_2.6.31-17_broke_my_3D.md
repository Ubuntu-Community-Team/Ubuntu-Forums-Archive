---
title: "kernel 2.6.31-17 broke my 3D"
date: 2010-01-10
forum: Hardware
---

### Post by clevertomato on 2010-01-10
I just got a new Dell Studio 1555 with ATI 4570. After a lot of research and work, I got 3D working with ATI Catalyst 9.11 drivers. I got lid behavior and brightness keys working by using "noapic" on my grub menu entry. That was kernel 2.6.31-16. Now, after update manager upgraded me to kernel 2.6.31-17 my 3D doesn't work at all anymore. Compiz is installed but nothing works (ie. Cube).

Any ideas? ...suggestions?

---

### Post by derekmbarnes on 2010-01-10
Did you check Hardware Drivers to see if your FGLRX was still activated?

---

### Post by andzaa on 2010-01-10
Hi,
I'm new to Ubuntu and I have the same system, except ATI driver 9.12; sorted out brightness via noapic as well. After installing 31-17 Firefox would not scroll the page smoothly but rather re-paint the screen every time I scroll or page up/dn. Guess this could be because of 3D acceleration.

For now I'm selecting 31-16 at Grub screen and it works well.

How do I check for "Hardware Drivers to see if your FGLRX was still activated" and how do I re-activate if it got de-activated? (and why would it get de-activated?)

Thanks,
Andrei

---

### Post by clevertomato on 2010-01-10
Andzaa: Same behavior for me with the scrolling. Very choppy, which seems to be counterintuitive to using the manufacturer's drivers for getting supposedly the most out of the GPU features.

Regarding: > How do I check for "Hardware Drivers to see if your FGLRX was still activated" and how do I re-activate if it got de-activated? (and why would it get de-activated?)

This refers to System/Administration/Hardware Drivers option. I don't know how they would get deactivated without the user. However, when I install the Catalyst drivers from the ATI site (like you and I are talking about), it is not reflected in the "Hardware Drivers" dialogue window even though it is still the fglrx driver. AFAIK, if you don't install proprietary drivers with the "Hardware Drivers" utility, it doesn't know anything about them.

Hope that sheds some light on it for you Andzaa. As for me, I'm still left with my original question of the post... Hopefully someone can help out with it.

Oh, and when I do "fglrxinfo" in a terminal window under 2.6.31-16 I get normal results. When I do it under 2.6.31-17 it shows errors. I can post the exact output if anyone is interested. In the meantime I'll have to boot to -16 kernel, which is do-able, but a hassle, and doesn't really address the heart of the problem.

---

### Post by clevertomato on 2010-01-11
This doesn't really address the cause of my original problem, but I have things working again. Here's what I did:

I unistalled the Catalyst drivers via terminal since that's how I installed them to begin with:```
sudo aticonfig --initial -f
cd /usr/share/ati/
sudo sh ./fglrx-uninstall.sh
```Then I reinstalled fglrx, this time via terminal using apt-get:```
sudo apt-get install xorg-driver-fglrx fglrx-amdcccle
```Rebooted, chose kernel 2.6.31-17 (still using "noapic" in grub to get brightness keys and lid behavior working), and voila. Things seem to work again. AFAIK, the ATI drivers intalled by this method are Catalyst 9.10 but I'm not certain.

We'll see how long this lasts until it gets broken again with another update. Hopefully it won't.

---

### Post by andzaa on 2010-01-12
Hi shawnboy,

I decided to try the same, but got into trouble. Uninstallation went well, but installing xorg-driver gave an error message in the middle but completed nevertheless.
Upon reboot I was getting error messages of 2 different kinds. 

Since I had no idea how to go about those specific messages I ended up completely reinstalling from CD (many thanks to the guy who suggested a separate /home back then)
Since the only reason for ever going through that tortured manual installation of AMD driver was brightness control, I decided not to bother again. Was able to fix this by adding "noapic" on the "default" line in Grub (as in thread 1313390 )

Spent the evening, but finally it all works. Hopefully, it will work longer because less bells and whistles installed now.

Cheers,
Andrei

---

### Post by clevertomato on 2010-01-12
Andzaa, too bad you had more trouble than I did fixing it, but I'm glad it sounds like you have things as you want now.

The reason I am using the proprietary ATI drivers instead of the open source is to get my suspend/resume working properly & also because I enjoy some of the visual wow factor of 3D (I never play 3D games on my PC).

Happy Linuxing.

---

### Post by markbuntu on 2010-01-12
The usual reason why the driver stopped working after a kernel update is because there is more than one set of kernel modules present and the kernel builder is unable to decide which ones to use so it builds none of them.

The reason for this is that old drivers and their kernel modules were not removed before installing a new driver. It is very important to have only one driver and one set of kernel modules present on your system.

I always remove old drivers before installing new ones and have not had a kernel update fail for over a year using 5 different linux distributions and 3 different ubuntu distros.

---

### Post by clevertomato on 2010-01-12
Markbuntu: I get the concept of removing old drivers before installing new ones, but when you talk about "kernel modules" and "kernel builders" ...well... I'm afraid I'm a little lost.

Would you care to explain more and / or point me to something that would explain what you're talking about for folks who don't have a lot of experience with Linux?

Shawn

---

### Post by andzaa on 2010-01-13
shawnboy: I did activate the "proprietary ATI/AMD driver" offered in "Hardware Drivers" although it doesn't seem to offer any status/configuration controls like the Catalyst did.
So presumably, I do have 3D acceleration. (the only games I ever play are tetris, mahjong and solitair :o)

What kind of "visual wow" are we talking about?

This laptop doesn't seem to have Suspend button and I set the lid to go Hibernate. This seems to work OK. I do get occasional coloured patterns on wake up, but that doesn't bother me (as long as it doesn't damage hardware, of course!)

markbuntu: do you mean performing some manual preparation before letting update manager install new kernel?? That does not sound right imho

Thanks everyone anyway: it works and I feel better and know more than before

Andrei

---

### Post by clevertomato on 2010-01-13
Andzaa: I'm not completely certain right now, but if you activate the ATI/AMD drivers via "Hardware Drivers" it **may not** install the ATI Catalyst Control Center automatically. If you don't have the "Catalyst Control Center" somewhere on your menu (either under Applications/Other or System/Preferences), then maybe it didn't. If you want to try to install that (which shows you info about the ATI/AMD 2D/3D features and allows you to make some adjustments), try doing:```
sudo apt-get install fglrx-amdcccle
```

(the amdccc part is AMD Catalyst Control Center)

The nice little visuals I was referring to are things like drop shadows on windows and things you can set in Compiz Config Settings Manager (sudo apt-get install compizconfig-settings-manager) like "wobbly windows," the "Desktop Cube" effect (CTRL-ALT-click-and-drag-mouse across desktop to see), etc. I don't always go for the bells and whistle like that, but since I have a brand new laptop, it has plenty of resources to spare for a little eye candy.

It's good that your lid closure behavior works properly. I struggled with that on mine for a while. I, too, have short moment when booting up or resuming where random color lines are flashed on the screen very briefly. It shouldn't be that way (in a perfect world), but I can easily live with that, like you said.

Shawn

---

