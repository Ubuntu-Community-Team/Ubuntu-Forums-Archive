---
title: "Problems with ASUS X51R notebook"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by r!ots on 2007-11-19
Hey folks,

first of all a big thumbs up. the new ubuntu 7.10 is once again great. i just love it, it's so much better than windows. especially since the ati radeon x1100 was detected and installed smoothly with ubuntu whereas it doesn't work in w2k.

anyhow i got some problems with my new (1 month old) ASUS X51R-AP167D notebook with the following specs:

[INDENT]processor: intel core duo T2450@2.00GHz
memory: 1024 MB DDR2-RAM 667MHz
hard disk: 120 GB SATA 5200 rpm
graphics: ati radeon X1100 with up to 128 MB shared VRAM
wlan: 802.11b/g
[/INDENT]

1. from time to time the notebook freezes when it's idle. the screensaver is running and suddenly it freezes and can't be woken up again. only possibility left is a hard reset which is very annoying, since there were always some programs with unsaved data running in the background. is it a problem with the power managment or might this be a hardware problem?

2. the suspend and the hibernate function don't work either so i turned them off. would you know how to get them to work properly?

3. how do i get the cpu-frequency-scaling to work? when i try to add the applet to the panel i get the following message:

```
CPU frequency scaling unsupported
You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

```

4. compiz doesn't work. when i try to enable it, it tells me that it couldn't be enabled. any ideas on that one?

5. some .pdf's weren't printable, they just stopped after the first page. i tried it with both evince and acroread - same thing. my printer is a hp photosmart c4180, setup with hplip and works alright apart from the pdf-printing.

6. the last thing is minor and i don't even know whether it has something to do with ubuntu. my wlan-connection behaves quite strange, i usually have a connection somewhere between 30 and 50 % at 54 mbps. problem is the download rate varies a lot. often my download starts at 1,4 mbps and then drops down to 30 kbps and below and doesn't go up again. i use an atheros-driver for the wlan-card and the router is a d-link di-524. has this something to do with my internet connection or with the configuration of the wlan-drivers?

well, any help would be highly appreciated. if you need more details, just ask and i will try to provide them. i would be very grateful if anyone could help me.
thx.

---

### Post by bill516 on 2007-11-19
I have an Asus Z96J.  Sounds as though we have a couple of the same 7.10 issues.  Like you I have an ATI card, in my case an ATI Mobility 1600X.

Neither suspend nor hibernate work.  In fact if I try to implement either one of those they will lock up the machine so that the only thing I can do is reboot.

Compiz Fusion also does not work, despite downloading the suggested ATI driver, so I am running without 3D on the desktop.

I've done a bit of snooping and I am beginning to think that you and I may have troubles attributable to the ATI drivers.  Not a good thing for me, since the 1600X "card" is hard-wired to my motherboard.  Do you have  the alternative of swapping it out?

I have no experience with frequency scaling and I do not run a screen saver.

Printing works well using an HP 882C Deskjet.

Your WLAN download rate variance sounds like an internet problem.  My  Intel card works quite well, but my rates are all over the place, apparently depending on traffic connections.  I have three machines in the house running XP with different wired and wireless cards.  This is true for all of them.

Good luck!

---

### Post by r!ots on 2007-11-20
hey bill516,

thx for your answer. at least concerning my internet connection it helped.
and no, i don't think that i can swap my graphics card. even if i could i wouldn't be willing to. i already spent enough money on the notebook that's why i want it to work properly. i think  desktop effects aren't that important but still it would be nice to be able to use them.
if you find a solution that works for you, plz let me know.

---

### Post by r!ots on 2007-11-26
Does anyone know how I can change the list from which the screensavers are randomly chosen? I noticed that the screensaver freezes the very moment I want to wake it up and that it mostly (maybe only) happens with very fancy screensavers (maybe those who use openGL). So I want to remove them and only keep some simple ones. How can I accomplish this?

When I try to use the normal desktop effects I get a message that the 'Composite extension is not available' although it is installed. Why isn't ubuntu able to use it?

Another thing just came to my mind: At first I had Ubuntu Feisty Fawn installed and if I'm not mistaken then hibernate and the suspend functions worked quite well. Same thing with the screensaver. Why did it work with the old ubuntu but doesn't with the new version? Where can I report this to someone from the ubuntu-team??

---

### Post by r!ots on 2007-12-03
Doesn't anyone know a solution for my problem(s)?

---

### Post by knocz on 2008-01-25
I have as Asus with a ATI Radeon mobility x1600 and I've got it working great (640FPS in fullscreen, 4200fps windowed..)

This works to install the ATI driver and solve your compiz problems

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

but thats all I can help you with..

---

### Post by Gag_Halfrunt on 2008-02-18
> **r!ots said:**
> 
3. how do i get the cpu-frequency-scaling to work? when i try to add the applet to the panel i get the following message:

```
CPU frequency scaling unsupported
You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

```


I had the same problem on my X51R and solved it by using a generic kernel rather than the 386 one.
```
sudo apt-get install linux-image-generic
```

After that, I just had to load the module acpi-cpufreq via
```
sudo modprobe acpi-cpufreq
```

You can make this module autoload on startup via
```
sudo echo 'acpi-cpufreq'>>/etc/modules
```
but test it first!

---

### Post by r!ots on 2008-02-25
First of all, thanks for your help guys.

I guess it's time for a quick update.

I got all 3D-acceleration issues solved by following the above mentioned [guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") and am now using the ATi Catalyst 8.02 drivers. I'm not using compiz, cause I don't think the integrated GPU is strong enough for that. Apart from that it works great.
I even got suspend/hibernate working by editing my */etc/default/acpi-support*:
```
SAVE_VBE_STATE=false
POST_VIDEO=false
```.

I fixed the cpu frequency scaling problem by partly following this [guide]("http://ubuntuforums.org/showthread.php?t=597998") and by adding the line '**acpi-cpufreq**' to */etc/modules*. I'm using a generic kernel as well.

So right now I'm really happy with my ubuntu-configuration.
Based on my experience I made a site at the ubuntu Laptop Testing Team page:
[https://wiki.ubuntu.com/LaptopTestingTeam/AsusX51R]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusX51R")

Have a nice week.

---

