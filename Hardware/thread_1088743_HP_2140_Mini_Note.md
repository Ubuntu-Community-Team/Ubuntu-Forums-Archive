---
title: "HP 2140 Mini Note"
date: 2009-03-06
forum: Hardware
---

### Post by xang on 2009-03-06
Just wanted to report my findings...

I just received my new 2140 Mini Note. Of course, I immediately installed Ubuntu 8.10.
Everything worked out of the box save for..wireless.

I installed the restricted driver, but it could not connect to any access point. I saw several wireless networks, but it would not connect. That being said, I disabled the restricted driver and followed the instructions contained within this site:

 [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133")

After reboot..worked like a charm! 

I really like the design of the netbook. It is aesthetically pleasing, and the keyboard is the best of any netbook I have seen and used. Screen is good, and the speakers are decent as well.

Just my two cents for anyone who is considering buying this product...

---

### Post by 0z0 on 2009-03-06
Hp mini note has a good review but MSI WInd with six cells battery (battery last upto 8 hours) is what i am looking forward.

good luck.

---

### Post by xang on 2009-03-06
> **0z0 said:**
> Hp mini note has a good review but MSI WInd with six cells battery (battery last upto 8 hours) is what i am looking forward.

good luck.

I bought the 2140 Mini Note with a six cell battery, and it shows 8 hours of battery life as well :)

---

### Post by 0z0 on 2009-03-06
> **xang said:**
> I bought the 2140 Mini Note with a six cell battery, and it shows 8 hours of battery life as well :)

if its six cells it would last that long :);for me a laptop should have a long battery life,easy portability and not so bad config which almost todays mini laptops have. mini laptops rocks :D

---

### Post by bartenst on 2009-03-07
@Xang, thanks for sharing your experience with the HP 2140! I am also looking forward to buying this device. Could you please tell us what configuration you have chosen?
- resolution: 1366 x768 vs. 1024 x 576
- harddisk: SSD vs. SATA-drive
- RAM? 

Thanks a lot in advance!

Regards,
Dom

---

### Post by dixon on 2009-03-11
Hi,
I'm considering buying HP 2140 Mini. Can you tell me how loud is the fan in ubuntu and what's the battery life in two scenarios:
a) watching movies (with wifi turned off)
b) browsing internet (with wifi turned on)
?
How is the battery life comparing to WXP? Because my HP 6720s has worse battery life in ubuntu than in XP. I'm bit afraid about battery life and loudness in ubuntu....

---

### Post by xang on 2009-03-11
I am on vacation in Costa Rica this week. Just dropped by an internet cafe for a quick look. I will post my findings after using it all this week on the plane, watching movies, etc. More to come! :)

---

### Post by markagraber on 2009-03-11
Hi, I have been running the 2140 with ubuntu for a couple of weeks.  Everything is working fine......except......the screen resolution is a problem because some dialogue boxes are too big for the screen.  It makes navigating and setting up some software problematic (K9Copy, for example).  Haven't found a solution yet.  It is enough of a pain that I might wait for the new version.

Otherwise, very quick.  I have both Wine and VM running so I can run a Win native software I must have in the VM (UpToDate) and some other stuff in Wine.
Battery life is 6-7 hours with 6 cell.  The fan doesn't run often when running on battery and there is a hardware set in the Bios to turn the fan off when plugged in unless the computer gets too hot.  USB LiteOn DVD works fine.

Overall, a "B".  Not quite the perfect machine mostly because of the screen resolution. Otherwise it is wonderful.
Mark

---

### Post by dixon on 2009-03-12
> **markagraber said:**
> the screen resolution is a problem because some dialogue boxes are too big for the screen. 

Have you tried also ubuntu remix? You should have more place on the screen with UNR...

---

### Post by jmontelius on 2009-05-10
Also have a 2140 and sofar I'm pleased. Installed 9.04 without any problems from a usb stick. 

Wireless worked out of the box, Skype is ok even with builtin video, no problem, Bluetooth works ok.

External monitor is ok but on one projector I can not get the screen to work in parallel with the projector. I guess the screen can not render 800x600? On another projector mirroring works, but the lcd is down to 640x480 which is then hard to navigate. 

Suspend works ok.

---

### Post by Valde_91 on 2009-05-11
Hi! I've just bought an Hp 2140 and I installed ubuntu 9.04 and everything works out of the box. To do the install properly I've to disable the option "dual core" in the bios (intel atom N270 are single core!).

My only problem is that the fan is always on. I've disabled the bios option "fan always on when AC" but nothing changed. Then I installed powernowd: my processor is scaling, but the fan is still always on.
By touching the case it seems that my machine isn't warm at all.

I don't have a dual boot with xp, because I've bought the one with Suse, and now I've only ubuntu 9.04 installed, so I don't know if the fact that the fan is always on is normal or not.

Any suggestion?

thanks Valde_91

---

### Post by robllewellyn on 2009-05-14
Just a quick post to report my findings with the HP2140 mini note and 9.0.4 remix

Install was fine from a USB stick

Few mini icon issues in appearance, but changed to a different theme and most have been resolved.

Wireless is fine no issues, although it is using an external driver, but with no issues

Lid close doesn't turn off the screen as reported elsewhere

I did have issues with a text puke when I booted with the power supply plugged in.

I have since dual booted with Win7 beta and for some reason (dont know if connected) I can now boot ubuntu remix with power supply in

With sticking win7 on after Ubuntu I had to do some work with grub to get GRUB and ubuntu to boot first (Win7 was booting direct each time as it must have overwritten the boot order) I now have the grub OS list to select an OS to boot. A few changes to the menu.lst file as documented elsewhere has allowed everything to work.

I have the two OS on seperate partitions (I used Gpart booted from a livecd environment on a USB stick) and Win7 doesnt seem to have any issues with being on hd0,1 rather than some reports that windows must be on 0,0 to work.

What I would say is, if you plan to dual boot, its a far easier process to stick windows on first and then install ubuntu if you have the option. I hadnt done enough research and just went for ubuntu first.

Video is fine, bbc iplayer works fine in firefox with flash, but doesnt work when you install the iplayer desktop client. Playback is jerky, audio seems ok.

I have disabled dual boot in the bios as well documented elsewhere

I havent updated the bios to 0.3 as yet, still on 0.1 HP bios that came with the machine, so cant comment on that

Just the 1gig of RAM and it works a treat, all good for about 2 weeks now.

OPenoffice 3 works great for what I need, I live in a browser most of the time anyway and oddly the only thing I miss with using google docs is outline numbering for legal docs!

Skype works, video camera and audio all good with some changes to audio settings from default. IM all works for AIM in pidgen

All in all, as this is my first exposure to ubuntu (and linux distros) I;ve been able to get it working how I want it with minimal understanding of terminal and linux.

---

### Post by dixon on 2009-05-14
Is your internal microphone working out of the box? Somebody mentioned here the mini is working with skype well. I can't get my microphone working (ok I can - upgrading to alsa 1.0.19), but is the mic working for u guys out of the box?

---

### Post by Valde_91 on 2009-05-14
To Dixon:

My microphone worked out of the box. i tested with the sound recorder application. But I changed the encoding to wave. Because .ogg was't working.

Did you check your settings on the volume control application?

bye bye!

---

### Post by dixon on 2009-05-14
> **Valde_91 said:**
> To Dixon:

My microphone worked out of the box. i tested with the sound recorder application. But I changed the encoding to wave. Because .ogg was't working.

Did you check your settings on the volume control application?

bye bye!

Yeah, I checked volume settings and everything before updating to alsa 1.0.19 and I couldn't get it work. I don't get it. Could you please post screenshot of your volume control sliders?

---

### Post by Valde_91 on 2009-05-14
For the lid issue:

I tested the ability of the acpi module to detect if my lid was or not open by coding in a terminal:
```
cat /proc/acpi/button/lid/*/state

```

Where * is for the directory that contain the state and info file. In my case C136.

With the lid open it returned 
```
open
```
 When I tried with the lid almost closed (I must be able to reach the enter button with my finger, so I closed the lid as much as possible) the answer was:
```
closed
```

So the acpi is capable to recognize if the lid is open or not. And very strangely Monday I used all day my 2140 and when I close the lid stand-by works! I thought that the kernel upgrade solved the issue. But when I used my 2140 yesterday the bug was back: closing the lid don't put the machine in standby. But when I tested the acpi with the line above, the acpi module was able to detect if the lid was open or not.

So I tried to repeat all the things that I've done Monday: booting without AC adapter, activating powernowd and powertop, but I was unable to solve the bug.

Any suggestion on how to debug this issue?

bye bye Valde_91

---

### Post by Valde_91 on 2009-05-14
> **dixon said:**
> Yeah, I checked volume settings and everything before updating to alsa 1.0.19 and I couldn't get it work. I don't get it. Could you please post screenshot of your volume control sliders?

I'll do this evening. I haven't the 2140 with me now.

bye bye
Valde_91

---

### Post by Valde_91 on 2009-05-15
Voilà! This is my volume control screenshot.

BTW a renabled dual core option in bios. Ubuntu started ok. I don't I've checked now if everything is working, but my 2140 is faster. It's possible that the dual core option, in reality enable Hyper Threading (Atom processor have the HT technology). For example before renabling this option often when I played music and browse the web I could hear some hanging in the music, but now the hangings are gone!

Bye bye
 Valde_91

---

### Post by dixon on 2009-05-15
> **Valde_91 said:**
> Voilà! This is my volume control screenshot.

BTW a renabled dual core option in bios. Ubuntu started ok. I don't I've checked now if everything is working, but my 2140 is faster. It's possible that the dual core option, in reality enable Hyper Threading (Atom processor have the HT technology). For example before renabling this option often when I played music and browse the web I could hear some hanging in the music, but now the hangings are gone!

Bye bye
 Valde_91
My volume control looks bit different (I've mic, internal mic, capture and all are muted - I cannot unmute them) :\ Is it really the default ubuntu 9.04 installation? What bios version do you have?

---

### Post by Valde_91 on 2009-05-15
> **dixon said:**
> My volume control looks bit different (I've mic, internal mic, capture and all are muted - I cannot unmute them) :\ Is it really the default ubuntu 9.04 installation? What bios version do you have?

I dixon!

I don't have made any bios update for the moment, but I'll check the version this evening.

For the mic, this is my default installation. The only thing that I do is checking the internal mic in preference.

Did you have a dual boot? Have you the possibility to test if your mic works?

Bye Bye Valde_91

---

### Post by Valde_91 on 2009-05-15
Another thing,
which devices are listed on your volume control? 

bye bye

---

### Post by GeoJono on 2009-05-15
I have had my 2140 for a few days now.  I installed 9.04 Remix to dual boot with XP Home.  I haven't tested everything (I'm still learning Ubuntu), but I like it all so far.

As mentioned by others, I also have the text-puke problem if the AC power is connected.  I even tried it with the AC cable connected to the 2140 but not to the wall: same problem.  I know that the AC adapter will hold some power for a few minutes after disconnecting it from facility power, so I let it sit for over 6 hours before I tried it: still the same problem.

Not a big deal, really, as I can boot into Ubuntu without AC power and then connect it after the boot is completed.  No problems so far, so it must only be the boot process that doesn't like the AC power port to have anything in it.

I have been playing around with the interface and I like the regular desktop better than the remix desktop, so I've changed it to the normal Ubuntu desktop.  I like that I can customize the top and bottom panels with the items I want to have there.

Altogether, I haven't done a whole lot with it yet.  I am new to Ubuntu and new to Linux, but excited to learn more.  I'm glad these forums are here to help with that.

Jono

---

### Post by atrus on 2009-05-15
Filed:

HP 2140 Internal Microphone doesn't work
[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795)
- update, loading the sda-hda-intel module with model=laptop gets the mic working. Unclear how to make this change persist across reboots currently.

HP-2140 won't boot with dual-core enabled
[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376728](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376728)

HP 2140 Lid Close Not Detected
[http://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/376793](http://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/376793)

---

### Post by atrus on 2009-05-16
I've been tracking a few 2140 issues with ubuntu, and for some of them have workarounds:

HP 2140 Internal Microphone doesn't work
[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795)
- update, loading the sda-hda-intel module with model=laptop gets the mic working. Unclear how to make this change persist across reboots currently.

HP-2140 won't boot with dual-core enabled
[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376728](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376728)
- update: VERY IMPORTANT: Enabling dual-core on the laptop enables Hyper-Threading. It's not quite dual-core, but it's a major improvement in performance, as linux effectively sees 2 CPUs.
- As it turns out, the machine only crashes on boot-up if the power supply is plugged into the notebook. IF you boot up with the power plug NOT inserted into the laptop, it'll boot successfully, at which point you can plug it back in.

HP 2140 Lid Close Not Detected
[http://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/376793](http://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/376793)

---

### Post by dixon on 2009-05-17
I've just confirmed all three bugs. I hope it will be resolved soon. It's shame for ubuntu netbook remix that it's not working fine on this netbook. There're like 10 common netbooks on the market, ubuntu should be running without a hitch at least at the most common netbooks :\

2Valde: options snd-hda-intel model=laptop made my mic working, but I cannot still get how is your mic working out of the box :\ I think the mic is common problem across all 2140s except yours :\

---

### Post by atrus on 2009-05-18
> **atrus said:**
> Filed:

HP 2140 Internal Microphone doesn't work
[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795)
- update, loading the sda-hda-intel module with model=laptop gets the mic working. Unclear how to make this change persist across reboots currently.

**Update:** This seems to break the built-in speakers.
> 

HP-2140 won't boot with dual-core enabled
[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376728](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376728)

**Update:**You can boot with dual-core enabled as long as you don't plug in the AC power until the machine has actually booted up.

---

### Post by wintrmute on 2009-05-21
I totally failed to get a HP Mini 2140 to boot off USB with either the 9.04 NBR, or with the standard ISOs.. Until I updated the BIOS.
Plugging/Unplugging the AC power made no difference. Nor did adjusting the fan or dualcore options in the BIOS.

So it seems that F.01 BIOS is buggy. I updated to F.03 BIOS from HP's site, and then everything worked just fine! I wasted so much time.. I'm surprised no-one else has reported this.

---

### Post by robllewellyn on 2009-05-25
I set up a dual boot with Win7 for my mini recently and the power issue went away. It loads grub, I select my os, it loads. V odd. With both dual core enabled and disabled.

Mic worked out of the box, I had to select the non default settings in Skype to get it working though. Dont have it in front of me at the moment.

Has anyone upgraded to F.03 firmware from ubuntu and if so how did you do it? Its fooled me until now. I think all the HP downloads are windows based, not sure.

Any other strange things anyone has noticed?

I cant get the BBC iplayer to work as a desktop application (I'm in the UK, dunno if you guys are? You might not be able to use iplayer anyway as its a BBC thing and only available in the UK or over a UK based VPN!)

Look forward to hearing of new 2140 stuff.

---

### Post by agazzo on 2009-06-01
any news or improvement about close lid and dual core bug?

i finally got the mic working by changing default audio input/output in gstreamer-properties :D

---

### Post by str3zz on 2009-06-02
Hello all,
 
I've recently purchased HP Mini HP2140 for my girlfriend. As I were not satisfied with pre-installed SLED10 I've decided to go for UNR.
I were searching for a workaround for the bugs:
HP 2140 Internal Microphone doesn't work
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795)
 
HP-2140 won't boot with dual-core enabled
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376728](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376728)
 
HP 2140 Lid Close Not Detected
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/376793](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/376793)
 
at the begining I've updated the BIOS to F.03 (from F.00) - mainly for the fix in version F.02: [link_to_hp_fixed_in_f.03]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=sk&prodTypeId=321957&prodSeriesId=3872994&swItem=ob-70605-1&prodNameId=3872996&swEnvOID=2020&swLang=13&taskId=135&mode=5")
of course it didn't helped me.
 
The final workaround/solution seems to be Linux kernel 2.6.29 (or higher) for me. With 2.6.29 (2.6.29.4) I have to problem which starting with AC plugged in; also microphone works and as just tested (after crosschecking powere settings) also system goes to standby when I close the lid.
 
I had some issues (even to get the WLAN/wifi working with 2.6.29 (also 2.6.30.x) as it was not working out of the box after kernel upgrade - there are no "linux-restricted-modules" available yet for 2.6.29/2.6.30 kernel realeases (at least I were not able to find it).
 
This was also the issues when I did test upgrade to karmic as the wifi card is:
BCM4322 - 432b - N class
```

08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```wifi which is not supported by b43 (see:[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)) (somehow karmic wants to apply b43 driver for this adapter)
 
I think it might be useful for someone to have some steps I did to get it working.
 
- install 2.6.29 kernel - I followed the steps mentioned at:
[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)
```

mkdir new_kernel;cd new_kernel
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629_2.6.29-020629_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629-generic_2.6.29-020629_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb
sudo dpkg -i linux-*

```(restart the system and boot new kernel)
 
then I thought get the STA module installed using the "module-assistant" (I found it at: [http://ubuntuforums.org/showthread.php?p=7373236](http://ubuntuforums.org/showthread.php?p=7373236)), but the broadcom-sta was just not in the list of available modules. At least I did the "prepare" there for modules compilation"
```

sudo apt-get install module-assistant
sudo module-assistant prepare

```
 
- the I downloaded the Broadcom STA driver from:
_[COLOR=#606420][https://launchpad.net/debian/sid/+source/broadcom-sta/5.10.91.9-1](https://launchpad.net/debian/sid/+source/broadcom-sta/5.10.91.9-1)[/COLOR]_
the 32-bit driver:
_[COLOR=#606420][https://launchpad.net/debian/sid/+source/broadcom-sta/5.10.91.9-1/+files/broadcom-sta_5.10.91.9.orig.tar.gz](https://launchpad.net/debian/sid/+source/broadcom-sta/5.10.91.9-1/+files/broadcom-sta_5.10.91.9.orig.tar.gz)[/COLOR]_
downloaded also debian patches for this STA drivers version from:
[http://patch-tracking.debian.net/package/broadcom-sta](http://patch-tracking.debian.net/package/broadcom-sta)
unpacked, applied patches and followed the steps from README.txt
steps:
```

mkdir wifi;cd wifi
# download all needed files
wget https://launchpad.net/debian/sid/+source/broadcom-sta/5.10.91.9-1/+files/broadcom-sta_5.10.91.9.orig.tar.gz
wget http://patch-tracking.debian.net/patch/series/dl/broadcom-sta/5.10.91.9-1/01-hidden-essid.patch
wget http://patch-tracking.debian.net/patch/series/dl/broadcom-sta/5.10.91.9-1/02-license.patch
wget http://patch-tracking.debian.net/patch/series/dl/broadcom-sta/5.10.91.9-1/03-2.6.29.patch
mkdir hybrid;cd hybrid
# unpack the driver
tar zxf ../broadcom-sta_5.10.91.9.orig.tar.gz
cd broadcom-sta/
# patch the driver
patch -p1 < ../../01-hidden-essid.patch
patch -p1 < ../../02-license.patch
patch -p1 < ../../03-2.6.29.patch
cd i386/
# make the module
make -C /lib/modules/2.6.29-020629-generic/build M=`pwd`
# copy it to modules location and load the module
sudo cp wl.ko /lib/modules/2.6.29-020629-generic/kernel/drivers/net/wireless/
sudo depmod -a
sudo modprobe wl

```
 
Afterwards I were able to see my wifi adapter in ifconfig/iwconfig output and configure my connection via the "Aplet NetworkManager" in UNR.
 
in order to make sure the wl module is loaded after the reboot I've added wl to /etc/modules (not sure if it's needed)
```

sudo echo wl >> /etc/modules

```
 
hope it helps someone.
 
EDIT:
regarding the lid close and suspend to ram:
it worked well (after first hibernation) and also when I've set the password protect when the screen saver is activated (when the laptop came up from standby display was locked and I were asked for the user password)

---

### Post by agazzo on 2009-06-04
@ str3zz

thank you very much for sharing info regarding how to get wireless working in kernel 2.6.29++
i've been trying for almost 2 days to get it working

i'm doing the steps you wrote, will report back in an hour
i hope the wireless is working :D

thanks!

update : THANKS MAN! YOU'RE THE MAN!
now i finally got the WIFI working and able to boot in hyperthreading support ;)
now it's only the close lid option that hasn't been solved, the lid goes blank after first hibernation, but if i reboot the same problem occurs again :)
any resolve in this one?

---

### Post by Valde_91 on 2009-06-05
Thanks str3zz!

My Wirless work again now.

Valde

---

### Post by Nunatak on 2009-06-06
Hi all,


I just wanted to install UNR 9.04 on my new Hp2140 via USB, doesn't
work. I turned off dual core in the bios, turned off the vent,
increased boot time to 5 and upgraded bios to F3 via usb stick. Nothing
helps. After pressing f9 I choose boot from usb, that's where it stops.
Screen is black but for the menu option f10 to enter bios, when I do
that it changes the word to entering bios or some such and then stops.
I tried several usb sticks, no change, bothe ports, no change.

Btw just borrowed an external usb-cd drive from a friend. It can see
the regular ubuntu cd and boot, but unfortunately the remix is not available on
cd. Anyone have any hints. I have been reading forums for hours and
talked to the support twice to no avail.

---

### Post by agazzo on 2009-06-06
> **Nunatak said:**
> Hi all,


I just wanted to install UNR 9.04 on my new Hp2140 via USB, doesn't
work. I turned off dual core in the bios, turned off the vent,
increased boot time to 5 and upgraded bios to F3 via usb stick. Nothing
helps. After pressing f9 I choose boot from usb, that's where it stops.
Screen is black but for the menu option f10 to enter bios, when I do
that it changes the word to entering bios or some such and then stops.
I tried several usb sticks, no change, bothe ports, no change.

Btw just borrowed an external usb-cd drive from a friend. It can see
the regular ubuntu cd and boot, but unfortunately the remix is not available on
cd. Anyone have any hints. I have been reading forums for hours and
talked to the support twice to no avail.

have you used imagewriter to make the unr bootable from usb?
also, my 2140 won't boot from usb if USB drive is set to 1st boot order in BIOS, change the order to second solved it.

---

### Post by Nunatak on 2009-06-07
Hi I used Disk Imager for creating the USB-Boot Stick as per the instructions on the official site. Besides the very same stick works just fine with my collegues HP 2133.

I also tried your bios setting: set USB Hard Disk to second in the boot order, doesn't do anything. Did you have dual turned off as well? 

The strange part is that with the stick inserted I can't even enter the bios via F10 on bootup. The machine just freezes on black screen.

Should I install regualr Ubuntu via CD? Or is that a bad idea for a netbook? Presently it runs Suse 10.

---

### Post by Harlort on 2009-06-07
Thanks Str3ss! Appreciate your posting. 

I've been following your instruction down to where I create the
hybrid folder. But then I'm stuck on the unpack part. the tar command you have written point to a file that I don't have...?
And how do I do the patch, tried that but doesn't work. When is the Broadcom-sta folder created.
I'm new to this and I would really like my wireless to work.
All support is appreciated.
Rgds 
[FONT=monospace][/FONT]

---

### Post by agazzo on 2009-06-08
@ Nunatak
Yes, I have the dual boot disabled in bios
the bios should've detected the USB boot with dual boot turned on, but default kernel in Jaunty UNR won't boot (kernel panic) with dual boot turned on
have you tried running regular ubuntu with usb using [unetbootin]("http://unetbootuin.sourceforge.com")? maybe your UNR image is corrupt/bad

@ Harlort
download this file ==> [http://mirror.hosef.org/debian/pool/non-free/b/broadcom-sta/broadcom-sta_5.10.91.9.orig.tar.gz](http://mirror.hosef.org/debian/pool/non-free/b/broadcom-sta/broadcom-sta_5.10.91.9.orig.tar.gz)
then put that file in hybrid folder
then just continue with the script that str3zz has written before

---

### Post by str3zz on 2009-06-08
> **Nunatak said:**
> Hi I used Disk Imager for creating the USB-Boot Stick as per the instructions on the official site. Besides the very same stick works just fine with my collegues HP 2133.
 
I also tried your bios setting: set USB Hard Disk to second in the boot order, doesn't do anything. Did you have dual turned off as well? 
 
The strange part is that with the stick inserted I can't even enter the bios via F10 on bootup. The machine just freezes on black screen.
 
Should I install regualr Ubuntu via CD? Or is that a bad idea for a netbook? Presently it runs Suse 10.
 
regarding the boot from USB stick I do have few recomendations:
- you should plug the USB stick, when the laptop is switched off (when you plug it in during the boot it happends quite often, that the HP BIOS will hang)
- I would recomend to start booting with unplugged power cord (if you have lan cable connected you should also unplug it for the boot)
- check your BIOS firmware (to be on the safe side)
 
I didn't change boot order when I were booting from the USB - I just hit F9 and choose "USB hard drive" from the menu. It might happened, that system freeze during linux kernel boot - only recomendation is - stop the system "push the power button for 5 seconds" and power it on again. I did boot from USB stick more times ussualy I were able to start up at maximum 5th attempt.

---

### Post by str3zz on 2009-06-08
> **Harlort said:**
> Thanks Str3ss! Appreciate your posting. 
 
I've been following your instruction down to where I create the
hybrid folder. But then I'm stuck on the unpack part. the tar command you have written point to a file that I don't have...?
And how do I do the patch, tried that but doesn't work. When is the Broadcom-sta folder created.
I'm new to this and I would really like my wireless to work.
All support is appreciated.
Rgds 

 
Hi,
 
in general the steps are writen for copy & paste
I found a typo in the steps - thanks for feedback!
I've downloaded so many drivers that there was mess from it at the end
The driver I've doenloaded from:
[https://launchpad.net/debian/sid/+source/broadcom-sta/5.10.91.9-1/+files/broadcom-sta_5.10.91.9.orig.tar.gz](https://launchpad.net/debian/sid/+source/broadcom-sta/5.10.91.9-1/+files/broadcom-sta_5.10.91.9.orig.tar.gz)
so correct step should be
```

wget [https://launchpad.net/debian/sid/+source/broadcom-sta/5.10.91.9-1/+files/broadcom-sta_5.10.91.9.orig.tar.gz](https://launchpad.net/debian/sid/+source/broadcom-sta/5.10.91.9-1/+files/broadcom-sta_5.10.91.9.orig.tar.gz)

```
 
I'll edit/fix my previous post

---

### Post by rudlavibizon on 2009-06-30
str3zz, have you tried this with 2.6.30? Will it work? 

Thanks

Bane

---

### Post by atrus on 2009-06-30
My broadcom-sta stuff builds and works w/2.6.30 fine. YMMV.

---

### Post by rudlavibizon on 2009-07-01
> **atrus said:**
> My broadcom-sta stuff builds and works w/2.6.30 fine. YMMV.

Hmm, I had errors with the 2.6.30 patch.

---

### Post by rudlavibizon on 2009-07-03
The errors are from not patching with 3rd patch before 4th. The drivers build fine but don't work. How did you upgrade to 2.6.30? Can you point me to the repo/packages you used?

---

### Post by awells527 on 2009-07-03
str3zz: that tutorial worked **perfectly** on getting my wireless working!  Thanks!!

---

### Post by senectus on 2009-07-05
Am going to MS TechEd this year, and this year they're giving this laptop away for free :-)
[http://www.msteched.com/australia/Public/windows-7-experience.aspx](http://www.msteched.com/australia/Public/windows-7-experience.aspx)

I can't wait the blow away Win7 and put Ubuntu on it ;-)

---

### Post by cika_mike on 2009-07-07
Hi guys! 
I have exactly the same problem with my 2140 as 'Nunatak' (previous page). 

This model also comes with the SuSE distribution. I tried with several USB flash drives, but the device can not boot NBR, or any other OS. 

Is someone resolved this problem?
Thanks!

---

### Post by agazzo on 2009-07-13
regarding the close lid issue... has anyone successfully found the solution?
whenever i want to turn the screen to blank, i run **/etc/acpi/screenblank.sh**
i assigned a shortcut to directly execute that script

anyone knows how to make ubuntu execute that script by detecting whether the lid is closed or not?
i've tried configuring /etc/acpi/events/lidbtn and /etc/acpi/lid.sh but nothing works
i also tried running /etc/acpi/lid.sh while the lid is closed, and they works! the problem might be in the lidbtn but i'm not sure... =/

oh and btw... for** broadcom-sta issue in kernel 2.6.30**
just use **[this]("http://ubuntuforums.org/showpost.php?p=7252017&postcount=6")** patch from Amaranth, it worked perfectly in my machine

---

### Post by Aragwain on 2009-07-20
My microphone works out of box. I have 2140 for 1 week and I had a problem with wireless (fixed with ndiswrapper) and I had a problem with booting, but I fortunately changed the "Dual Core Boot" in BIOS, and now everything works fine. If anyone knows how to make the "Dual Core" work, please contact me (chmiela.st@gmail.com). I think Hyperthreading would make my machine more faster.

---

### Post by atrus on 2009-07-20
> **Aragwain said:**
> If anyone knows how to make the "Dual Core" work, please contact me (chmiela.st@gmail.com). I think Hyperthreading would make my machine more faster.

This question has already been answered. In summary, there's fixes in newer kernel versions, and workarounds for older kernel versions.

---

### Post by Aragwain on 2009-07-22
I did what str3zz said to do and now, I have problems with startup and WiFi (low speed of connection), but I gave up. I returned to 2.6.28 and I work without HT. Wireless works with ndiswrapper. On Wikipedia (Polish) it is written, that it usually gives less than 20% of better performance. So I give up.

My microphone works out of box. In Skype I am using these settings:

In: HDA Intel (hw:Intel,0)
Out: pulse

It works. But I had to change also microphone volume in volume settings. Just changed device to "Capture: HDA Intel - AD198x Analog (PulseAudio Mixer)" and on tab "Recording" set the volume to 4/5 of height. It is good to use it in quiet home. Both switches under the slider are enabled.
In gstreamer-properties I have both In and Out ALSA and device is "Default".

---

### Post by Sörnäinen on 2009-07-28
> **str3zz said:**
> hope it helps someone.

It DID help. I had one problem since the generic-folders are having an "04" added to the name - i had to edit these lines by hand. But then it worked smooth. 

Thank you very much for this effort - the HP is much snappier now WITH hyperthreading active, and the fan is not blowing up all the time, what also should prolongue the battery lifetime, will have a look at that. 

Will this become a problem again with upcoming updates?

---

### Post by jambel on 2009-08-07
Hi, 

I've installed 2.6.30.4 kernel and followed the str3zz tutorial (great tutorial btw) for wifi.
After an [COLOR=SeaGreen]lshw -C network[/COLOR] I got:
> 
description: Network controller
product: BCM4322 802.11a/b/g/n Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:08:00.0
version: 01
width 64 bits
clock: 33Mhz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0 module=ssb
then I run iwconfig but no wireless extensions found.
> 
lo    no wireless extensions.

eth0    no wireless extensions.

pan0    no wireless extensions.
Any ideas?

thanks

---

### Post by jambel on 2009-08-08
*[SIZE=1]I really don't understand how it's possible to see the devise without any problems and don't have an assigned logical name wlan0 or something on iwconfig???[/SIZE]* :confused:

I get it now, cause of incorrect driver. :cool:

---

### Post by jambel on 2009-08-08
I attach a screenshot if that helps
[http://www.mediafire.com/?sharekey=7bef25b283f3be67d956df2962098fcbe04e75f6e8ebb871](http://www.mediafire.com/?sharekey=7bef25b283f3be67d956df2962098fcbe04e75f6e8ebb871)

---

### Post by jambel on 2009-08-10
UPDATE:
 I follow these steps:
> 
sudo modprobe -r ssb
sudo modprobe -r wl
sudo modprobe wl
sudo service NetworkManager restart
and everything works fine!!

BUT when I reboot no changes are saved, is there any solution to keep up the wl driver??

---

### Post by jambel on 2009-08-10
_***FIX:***_

I followed this tutorial [http://wiki.debian.org/KernelModuleBlacklisting](http://wiki.debian.org/KernelModuleBlacklisting)
and after [COLOR=SeaGreen]*update-initramfs -u*[/COLOR] and reboot everything worked fine!

---

### Post by jambel on 2009-08-14
I'm attaching my tutorial in case someone still have issues...
**[Ubuntu 9.04 (Jaunty Jackalope) with 2.6.30.4 Kernel on HP 2140]("http://jambelnet.blogspot.com/2009/08/ubuntu-904-jaunty-jackalope-with-26304.html")**

---

### Post by Epaminond on 2009-09-24
Thanks to str3zz my Wi-Fi works!!! ))
Had to modify his script a bit but finally I made it working on 2.6.29.6!

The lid close problem still unsolved. Did anyone find a solution?

---

### Post by senectus on 2009-09-24
weird, it "just works" for my 9.04 UNR install...

---

### Post by Epaminond on 2009-09-25
**2senectus**
Are you talking about the lid problem? How can it be so?! :)

What about agazzo's script? Did anyone find a way to make it detect the lid's state?

---

### Post by agazzo on 2009-10-31
> **Epaminond said:**
> **2senectus**
Are you talking about the lid problem? How can it be so?! :)

What about agazzo's script? Did anyone find a way to make it detect the lid's state?

the lid problem still exist in Karmic Koala...
just assign "**xset dpms force off**" to a key, it'll make the screen goes blank until you press another key (or touch the the touchpad)
hope they got it fixed in Lucid Lynx

---

### Post by str3zz on 2009-11-16
I did 9.04 upgrade to 9.10 on my HP 2140 but for the complete migration to ext4 (and also weird behavior of pulse audio after the upgrade) I did fresh karmic install (using USB stick).

Everything works out of the box (if you forget about first update without wifi - due to broadcom proprietary drivers).

For now I had only one issue which is described here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236)
Workaround is also described there so at the end everything works.

I can only recommend doing fresh install of karmic on HP 2140 - system runs much better (also Skype works as never did).

---

### Post by charlie_barkin on 2010-06-05
I also got a HP Mini 2140 which runs on Ubuntu 10.04 Lucid. And also having a problem on the lid. The screen never shut off when I close the lid and I need to press the fn+f1 botton to suspend it. Does any one got fix for that bug???
:confused::confused::confused:

---

### Post by eliosol on 2012-02-29
Hello I am new to the community, but I have a problem with my hp 2140la I installed ubuntu 11.10 and does not work bluethoo and no wi-fi. I have read almost everyone's contributions and there are broken links. Can you help me please?:confused:

thanks...

---

