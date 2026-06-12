---
title: "Ubuntu 6.10 on HP Pavilion dv6000"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by n8bounds on 2007-02-16
I recently got a new laptop, a nice Hewlett Packard (HP) Pavilion dv6000.  Ubuntu 6.10 did not give me the correct display resolution (Intel Mobile 945GM/GMS/940GML Express Integrated Graphics Controller) and could not make my wireless card (02:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01) work.  (You might try terminal commands like "sudo lshw" and "lspci" to see if your HP Pavilion dv6000 is similar to mine.)  This is how I fixed it, although YMMV.

This assumes a fresh Edgy (gnome-based) install and a working, wired internet connection.

this is my /etc/apt/sources.list file
```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```
open a terminal and paste this therein:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.original && sudo gedit /etc/apt/sources.list

```
that saved a backup of your existing sources file, then opened it with root privelages for editing.  Now, take everything out of it and paste in what is in mine from above; close then save

open a terminal and paste this therein:
```

sudo apt-get update && sudo apt-get install 915resolution bcm43xx-fwcutter

```
That will fix your resolution (on your next reboot, not immediately--don't panic...and don't reboot yet, you're not done) and gave you the tool you'll need to fix your wireless card problem.  

Now download the archive attached to this thread

(Just so you know, I got it from: [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)  )

Once you have extracted the file to your desktop (be sure to put the file called "wl_apsta.o" out of the archive on your Desktop, or change the code below to reflect its actual location) open a terminal and say:
```

sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o && sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o

```
Don't worry about any unhappy looking errors, I got some too and it works fine.

then say:
```

sudo apt-get install network-manager-gnome network-manager-pptp

```
now save your things and reboot, when you come back there should be a new icon in your system panel that lets you interact with the wireless card...see the screen shot about half-way down this page:

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)


I stole lots of this from this fine post:
[http://www.math.dartmouth.edu/~sarunas/D620F6.html](http://www.math.dartmouth.edu/~sarunas/D620F6.html)

and of course this one:
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by n8bounds on 2007-02-16
I've noticed a few other weird-ities that never afflicted Edgy on my old Dell laptop:

A>  Plugging in headphones does not mute the speakers or send sound to the headphones.  (Works in Windoze)

B> Although the wireless card now works, it can't acurately read signal strengths (it thinks they are all 100%) which is not a huge deal I guess.

C> I haven't testing this thoroughly yet, but either ubuntu is far more wasteful of my battery than Windoze, or it inaccurately thinks the battery is nearly dead when it is not.  (What I mean is, it seems like the battery doesn't last HALF as long, according to the gnome battery meter, as it seems to in Windoze.) More testing will follow.

D> I haven't tested all the fn (function) buttons, but at least the volume control buttons seem to work.

---

### Post by rocknrolf77 on 2007-02-16
Typing from a dv6119 now. My girlfriend's comp. I have the same problem. The soundcard don't work as it should and I haven't figured out the broadcom/ndiswrapper yet either.

Can't understand why broadcom has to behave like that. They are a linux hostile company. I think they should support their costumers anyhow. If you have paid for their hardware, it should work no matter what os you use. 

I hope I can get the wireless working too. Have to use windoze for internet now on wireless. What guide did you use to get the wireless working?

Anyone out there who can help with these problems? :-k

---

### Post by n8bounds on 2007-02-16
My post will guide you through getting the wireless working.  It is a recap of my experience after reading this guide:


[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

I agree with you, of course, regarding Broadcom Corporation.  It's weird that HP chooses their hardware.  They are a linux friendly company in general (at least for servers).

---

### Post by drpaul on 2007-02-17
A number of people [including myself] have got improved audio performance from their HP laptop by installing the latest [or at least a later] version of the Alsa driver.

I'm using the .13 version, and i have the builtin microphone working and get sound from the earphone jack. It still doesn't blank the speakers.

Paul

---

### Post by n8bounds on 2007-02-17
Thanks for the tip!

---

### Post by rocknrolf77 on 2007-02-18
I'm running feisty now on my comp. But I'm not going to update my girlfriends lappie until maybe a week after relase. At least we solve the the worst problems after a short time, unlike vista that was so much money in the making. But thanks for the tip. I'm really looking forward to final feisty. It is a lot of small improvements. Wireless is also getting a lot better.

Almost got the wireless working thanks to the guide you linked to. I have a strange problem left. The comp hangs completely when trying to connect to the wireless network. any ideas?  But at least I'm closer to solving the problem with the lousy wireless card. :)

---

### Post by n8bounds on 2007-02-18
Edgy used to hang my Dell.  I think it went away after I switched to the 386 kernel.  Are you using that one or the generic kernel?  Try switching to the other, whichever you have

Also, look around in /var/log/

there is a messages file and a syslog file which are sometimes telling

make sure there's nothing scarry in dmesg

there's also an xsession log...somewhere..I cant remember where they keep that...

---

### Post by teaker1s on 2007-02-21
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by n8bounds on 2007-02-21
What a treasure of information!  Thank you so very much!

---

### Post by syko21 on 2007-02-24
The updating alsa driver works to make the headphone jack functional. But the volume control keyboard shortcuts only work for the headphone jack then and plugging in a headphone doesn't cut off the sound going to the speakers. Anyone got any ideas?

---

### Post by n8bounds on 2007-02-24
what version did you use?  .13 or the .14rc2?

---

### Post by PsychedelicReaction on 2007-02-25
> **syko21 said:**
> The updating alsa driver works to make the headphone jack functional. But the volume control keyboard shortcuts only work for the headphone jack then and plugging in a headphone doesn't cut off the sound going to the speakers. Anyone got any ideas?

i just bought a pavillon dv2000, how did u compile new alsa version?

i followed the instruction in the wiki but i can't install it, this is the error:

```
checking for built-in ALSA... yes
configure: error: You have built-in ALSA in your kernel.

```

thanks :)

---

### Post by n8bounds on 2007-02-25
Sounds like you didn't remove the old version yet.

---

### Post by syko21 on 2007-02-25
I didn't remove the old version either. I used .13, the instructions on the dv6000 wiki site are unnecessary, simply download the driver run 
```

./configure
make
sudo make install

```
and then restart. But that still leaves the problems of the keyboard shortcuts only controlling the headphone jack and not the overall sound and the speakers not muting when you plug in headphones.

PS> I tried the instructions on the wiki site and they result in the same problem.

Warning: I do not know how to uninstall the updated alsa driver so as to revert things back to the way they were in case you want to go back.

---

### Post by PsychedelicReaction on 2007-02-25
i've successful updated alsa today to 0.13 but nothing has changed...

---

### Post by syko21 on 2007-02-25
odd. Did you follow the instructions on the dv6000 wiki or the ones i posted earlier?

---

### Post by PsychedelicReaction on 2007-02-28
just ./configure, make, make install

---

### Post by syko21 on 2007-02-28
it has to be 
sudo make install
otherwise the install isn't done properly.

---

### Post by azelter on 2007-03-06
I just wanted to add that the driver (r5u870) from [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/) got my webcam to work.
My webcam reports itself as ID 05ca:1870 Ricoh Co., Ltd and was previously unsupported.

---

### Post by syko21 on 2007-03-06
nice find, i installed it and the webcam works perfectly now

do you know of anything to get the xD card reader to work?

---

### Post by teaker1s on 2007-03-07
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-0b198b90ec3b7cc470b197a54622354457513e6c]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-0b198b90ec3b7cc470b197a54622354457513e6c")

---

### Post by syko21 on 2007-03-07
i tried that but it only makes the SD card reader work, not the xD which is what my camera has.

---

### Post by gacinalor on 2007-03-12
hello ciao
i have an HP pavilion dv6000, new one.
and i have the same problems of the other guy (dont remember the username ) anyway
i was following the instruction when 
1- i couldnt understand what to do with the wl.apsta.o file (he's now on my desktop)
2- I put the code on the terminal
this code:
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o && sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o

and then this came out:
sudo: bcm43xx-fwcutter: command not found

everything seemed to work fine until this point. now I dont know what to do.
please help me

im new with linux so im sorry if i dont understand things straight away.

greatings from argentina buenos aires

---

### Post by syko21 on 2007-03-12
ndiswrapper is your friend, its the most reliable method to getting your wireless card working. Follow the instructions here and you should be fine.
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-97a49d82a08115baa8ea6524400fdb07c0bf0d67](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-97a49d82a08115baa8ea6524400fdb07c0bf0d67)

---

### Post by teaker1s on 2007-03-13
:biggrin: ndiswrapper

---

### Post by syko21 on 2007-03-14
I'd just like to post the webcam driver here in case it gets taken down from the blog.

---

### Post by syko21 on 2007-03-14
If anyone has any new significant changes please post them in the related wiki [https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
as well as posting them here to maintain a current stream of information. Thanks.

---

### Post by gacinalor on 2007-03-15
> **syko21 said:**
> ndiswrapper is your friend, its the most reliable method to getting your wireless card working. Follow the instructions here and you should be fine.
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-97a49d82a08115baa8ea6524400fdb07c0bf0d67](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-97a49d82a08115baa8ea6524400fdb07c0bf0d67)


in fact you're right, now my wireless works just fine.
thanks a lot.

---

### Post by n8bounds on 2007-03-15
ndiswrapper ver 1.38, bcmwl5 driver from the sp33008.exe package flying on the  2.6.20-10-generic kernel (fiesty b5).... knetworkmanager displays broadcasted essids and proper signal strength but cannot configure dhcp; iwconfig, iwlist and dhclient work just fine though (bcmwl6 from vista driver provided no joy)

So all you need on fiesty is to install  build-essential  and  cabextract

then get these and follow the guide

[ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)

[http://umn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.38.tar.gz](http://umn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.38.tar.gz)

---

### Post by azelter on 2007-03-16
During updating the windows side of things to vista from XP my webcam firmware was flashed. The result is that the camera which used to report itself as: ID 05ca:1870 Ricoh Co., Ltd and was supported by the r5u870 driver from [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/) now reports itself as ID: 05ca:1810 Ricoh Co., Ltd and is no longer supported by that driver.
I am trying to find out if I can get it to work under linux again ...

---

### Post by teaker1s on 2007-03-16
does the driver have a config file you can alter?

---

### Post by azelter on 2007-03-16
I emailed Sam, who wrote the r5u870 driver. He says:

"That 05ca:1810 device ID indicates a Ricoh UVC camera, but that
requires an init sequence that the linux-uvc driver isn't yet able to
perform.  I'm currently working on adding minimal UVC commands to my
driver to support it, but we'll see where support goes after that."

So I guess I'll hear more soon.
I think currently the r5u870 will not support it.

---

### Post by n8bounds on 2007-03-16
That bites.  I've heard of Windoze flashing the firmware of wireless cards, media card readers and other things in the past.  Is there no way to flash it back to how you had it?

---

### Post by azelter on 2007-03-17
I wanted to flash the firmware. It was needed for the camera to work under vista, and as the main use I have for the camera is in skype I would rather have the camera working under windows than linux (until such time as video for skype in linux becomes available).

---

### Post by n8bounds on 2007-03-18
Ah, I see.  I have good news if you plan to upgrade to Fiesty.  If you have this audio card:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

It is fully supported with no user intervention....

---

### Post by teaker1s on 2007-03-19
running debian etch I updated alsa and now when you plug headphones in the speakers disconnect.

**I've also emailed canonical to ask the proceedure to go about moving  the wiki page to community docs**

---

### Post by syberdave on 2007-03-21
> **azelter said:**
> I emailed Sam, who wrote the r5u870 driver. He says:

"That 05ca:1810 device ID indicates a Ricoh UVC camera, but that
requires an init sequence that the linux-uvc driver isn't yet able to
perform.  I'm currently working on adding minimal UVC commands to my
driver to support it, but we'll see where support goes after that."

So I guess I'll hear more soon.
I think currently the r5u870 will not support it.

I've also e-mailed Sam with Usbsnoop logfiles, but he hasn't responded so I'm unsure if it got eaten by gmail's spam filter or something. I'm also eagerly waiting for a Linux driver for this. (Pavilion dv6253cL)

---

### Post by azelter on 2007-03-23
Regarding the 05ca:1810 Ricoh Co., Ltd webcam device on the dv6000 after the vista recommended firmware update: Sam has revised his r5u870 driver, and, pending further testing, future releases of this driver will support the updated webcam ([http://lsb.blogdns.net/ry5u870/)](http://lsb.blogdns.net/ry5u870/)).
Excellent work Sam!

---

### Post by n8bounds on 2007-03-23
Awesome!

---

### Post by Kobalt on 2007-03-24
Hi guys !

I have one of those dv6000 babies and I use Feisty, here are some news if you guys want some : sound is working perfectly out of the box (headphones stuff as well).I still had to use ndiswrapper to get a proper wifi connection. I don't use my webcam so can't comment on that. And I'm still so sad : the Ricoh card reader is working with a little trick, but only with SD cards (unfortunate MS Pro cards owners like me...)

One thing that one might find useful : I expercienced random crashes after migrating to Feisty, and on each new kernel. I blamed Feisty, being still in developpement... But the problem was that I had flashed my bios with the new version of HP's website back in December. I went to back to their website yesterday and noticed there was a new bios flash utility released on the 1st of March. I ran it (under windows then) and since then : no crashes. 
If someone experienced the same prob that'd be nice to have a feedback, to know if it's a common problem or specific to my machine.

---

### Post by teaker1s on 2007-03-24
yep I had bios issue too

---

### Post by n8bounds on 2007-03-24
I have a dv6205us, just to be specific; and haven't tried to upgrade the bios since I got it.  I am curious tho, if theres a chance doing so might break something; what was breaking prior to that that you were trying to fix by upgrading the bios?

I dont think I'll even attempt bios upgrades unless I get stuck troubleshooting something and cant think of anything else.

---

### Post by teaker1s on 2007-03-25
I went through a battle with edgy and basically the various boot options like "NOAPIC" had zero effect, I did for a time run edgy base and feisty kernel with some success,

---

### Post by Kobalt on 2007-03-25
> **n8bounds said:**
> what was breaking prior to that that you were trying to fix by upgrading the bios?
I had constant freezes, randomly after 15min or 4h... 

There is a potential risk of loosing data flashing your bios, but also a risk of messing up your hardware config leading to a bios reinstall through a floppy drive... 
You'd better be sure it's a bios issue (and backing up of course) before going into flashing. In my case I was pretty sure it was bios related so I went for it. 
The bad point is you need to do it under win, since it's a .exe file to run...

And I still needed, in Feisty, to use *noapic nolapic* options to boot.

---

### Post by led555 on 2007-04-05
hi,

maybe someone can help me, i'm not good at all with linux.  

i've installed ubuntu 7.04, without any problems, ... just had to specify my display resolution of 1024x768x32 on my dv6000 (dv6119us) laptop. 

once i boot my laptop, i get the GRUB menu, select to load ubuntu, and it starts loading.  i get the splash screen with the progress bar... but once the progress bar reaches the end, all i get is a black screen.

when i run the live cd, i don't have any problems with the display, sound, drives, wired network, etc... i do have to specify the display size though, before i run it.  

any ideas what i can do to fix my problem?

thanks in advance.

---

### Post by syko21 on 2007-04-05
yeah 32bit display for reasons i do not know does not like to work. Boot from the live cd and mount your ubuntu partition.
```

sudo mkdir /mnt/ubuntu
sudo mount /dev/**insert hard drive label here** /mnt/ubuntu
sudo gedit /mnt/ubuntu/etc/X11/xorg.conf

```
Then go to the screen section and add the line
```

DefaultDepth    24

```
and then change any instances of
```

Depth 32

```
so that it reads 24.

---

### Post by azelter on 2007-04-05
You don't have to boot the live cd. Just press ctrl+alt+ f1 to get to a non-graphical display. Edit the file as described above (except you don't have to mount the root fs) and then do sudo /etc/init.d/gdm restart once you are done and you should get to your graphical display.

---

### Post by syko21 on 2007-04-05
if you hit alt+F2 you are going to need to replace to use  nano instead of gedit because there will be no gui. @azelter, I recommended the livecd simply because people feel more comfortably with the GUI than CLI and he said he was new to linux.
the new line should read
```

sudo nano -w /etc/X11/xorg.conf

```

---

### Post by azelter on 2007-04-05
Ah, sorry. I've been using vi for so long my brain automatically replaces gedit with vi without thinking. Good point.

---

### Post by jak140 on 2007-04-09
New webcam drivers posted:
[http://lsb.blogdns.net/ry5u870/]("http://lsb.blogdns.net/ry5u870/")

---

### Post by led555 on 2007-04-09
hi,

thank you all for your help, though nothing helped.  i ended up installing open suse 10.2 and everything works well... except the wifi.  

hope future ubuntu versions will be more compatible with my laptop.

thank you!

---

### Post by Kobalt on 2007-04-11
Thank you jak140, my webcam is now working !

---

### Post by rocknrolf77 on 2007-04-18
Upgraded from 6.10 to 7.04 yesterday. Everything is now working a ok.  What a relief :)

---

### Post by debauchery1st on 2007-04-18
I just installed feisty on my dv6119us and I'm having a few usb problems.

I followed advice to get the OS installed and running (noapic), and have even managed to get beryl installed and running beautifully. 

I just can't seem to get USB to work unless the USB device is plugged in on boot. 


anyone have any ideas?

---

### Post by debauchery1st on 2007-04-18
> **debauchery1st said:**
> I just installed feisty on my dv6119us and I'm having a few usb problems.

I followed advice to get the OS installed and running (noapic), and have even managed to get beryl installed and running beautifully. 

I just can't seem to get USB to work unless the USB device is plugged in on boot. 


anyone have any ideas?


Just figured it out:

It seems that I had to add "nolapic" to the kernel boot line as well as "noapic", without BOTH of those parameters, USB fails to work.

update: 
seems, according to [http://ubuntuforums.org/showthread.php?t=406143]("http://ubuntuforums.org/showthread.php?t=406143") , you also need to throw in "irqfixup" at the end of your kernel boot line... without the last option, the usbports will eventually just stop being able to detect hardware (hardware already detected will work until removed).  It took about 10 or 15 minutes for my computer to stop detecting. With the "irqfixup" option, I haven't seen any usbport bugs all day long.


so in one lump sum, my dv6119us boot line looks like this:

kernel          /vmlinuz-2.6.20-15-generic root=UUID=d11ed572-4368-4041-ac7e-68de3462d22a ro quiet splash noapic nolapic irqfixup

(all in one line)

---

### Post by icdkp on 2007-04-22
[I]Hi people!
I upgraded my whole system lately to feisty fawn, and every thing seems now to be working fine. The unique remaining problem is the webcam. Very upsetting, since I need it for video calls with my girl friend... And the worst part is that I'm a newbie in linux...
More exactly, every time I try to test the camera, with Easycam, or simply in kopete, ekiga or amsn, I always become error messages such as "cannot find video device", "/dev/video0 not found" etc. I'm looking for a solution in google since already a month (had the same problem under edgy eft), but my know-how in the field is not good enough to understand any explanation I find... so I can't even describe "technically" the problem...
So please guys, if you can help me fix it :confused: ...
[/i]

I guess you would need these informations:
```
root@laptop:/home/laptop# **lsusb**
Bus 005 Device 003: ID 05ca:1870 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1241:1166 Belkin 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000 

root@laptop:/home/laptop# **lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

```

---

### Post by syko21 on 2007-04-22
Heres what you do. Download this file, [http://lsb.blogdns.net/files/r5u870-0.10.0.tgz](http://lsb.blogdns.net/files/r5u870-0.10.0.tgz) , its the driver for your webcam. Extract it to your user directory and then open up a terminal.
You will probably need some utilities to build the driver
```

sudo apt-get install build-essential linux-headers-`uname -r`

```
Next we'll go to the driver
```

cd r5*
sudo make
sudo make install

```
If you did not get any build errors then continue onward to the last step. If you did please copy the entire section and post it here.
```

sudo modprobe r5u870

```
If it still doesnt work post back here

PS> Every time the kernel is upgraded you will have to repeat these steps.

---

### Post by icdkp on 2007-04-22
> **syko21 said:**
> Heres what you do. 
...

[I]Thanks a lot syko21, now ekiga and amsn give out the video...  However, I still get the same error message (cannot find /dev/video0) when testing the webcam with easycam... And as far as I know, I think I should use it to configure the camera... Since the video quality is very very poor... If you have an idea, it would be great :) 
Once again, thanks dude![/I]

---

### Post by syko21 on 2007-04-22
The driver that was made doesn't play nice with some programs so you will most likely need to find another program to configure the camera. Here is a list of compatible programs

[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-1c7180cbcc04dae94420ec64f775311b0fe93bf2](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-1c7180cbcc04dae94420ec64f775311b0fe93bf2)

---

### Post by firecat53 on 2007-04-30
Have any of you tested the suspend/hibernate features? I just get a black screen, but the computer never goes all the way into suspend or hibernate. I'd LOVE to get that working!!!

Scott

---

### Post by syko21 on 2007-04-30
im waiting for someone to perfect a set of instructions for suspend2 on feisty. I tried doing it myself and ended up fragging my whole system. I'm doing a clean install as we speak.

---

### Post by syberdave on 2007-04-30
Is there anything significant in /var/log/hibernate.log ?

---

### Post by firecat53 on 2007-04-30
I don't have the file hibernate.log anywhere on my system. I haven't even tried hibernate. Just suspend so far. I also am very reluctant to try suspend2 for fear of borking my system. Just don't have time to 'play' right now!

scott

---

### Post by Kobalt on 2007-05-01
The suspend/hibernate just work on my HP dv6120eu, but I had to install the nvidia drivers.
It's not working out of the box with Beryl/compiz running though, you need to log off in order to quit beryl/compiz before suspending or hibernating...

---

### Post by n8bounds on 2007-05-02
It suspends beautifully (usually down in 2 seconds and up in 5) on my dv6205us running beryl/emerald.  I have the intel video card and 2GB of memory.  I've never tried to hibernate from KDM, but when I'm logged in it always hibernates but is about 1/3 chances of coming out of it well.

I don't have a /var/log/hi... anything either... 

Hey can anyone else use there touchpad on/off button?  It SORTA works on mine, but every time it turns the touchpad back on, theres a 5 second delay and it always opens the KDE help window.

When I do it, this shows up in /var/log/messages
```

May  2 21:15:13 kernelpanic -- MARK --
May  2 21:29:04 kernelpanic kernel: [31537.108000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
May  2 21:29:04 kernelpanic kernel: [31537.108000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
May  2 21:29:04 kernelpanic kernel: [31538.044000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 21:29:07 kernelpanic kernel: [31540.628000] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.

```

I'd gladly use the setkeycodes command, but I don't know what <keycode> to tell it....

---

### Post by teaker1s on 2007-05-03
on off button on 6116eu works perfectly with gnome:guitar:

---

### Post by n8bounds on 2007-05-28
go figure

hey, just thought I'd share here, I found my old OEM WinXP disk from HP (the HP part is important).  I was still dual booting for games, so I thought I'd try to downgrade to XP (mine came with Vista).  XP installed from this HP OEM disk and activated, just like it would on any other HP PC that it might have came with.  Anyway, the hard part is HP doesn't help us very much if your model never came with XP on it.  After gathering them from various places over the course of three days, I put all the drivers that XP needs to run on my dv6205us into one place.  Here ya go:

[http://thebounds.net/xpdrivers.zip](http://thebounds.net/xpdrivers.zip)

Cheers

---

### Post by syko21 on 2007-05-28
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&cc=us&dlc=en&product=3224055&lang=en&#](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&cc=us&dlc=en&product=3224055&lang=en&#)
that should help a bit too, I got my dv6000 before the vista crap took over so that support site is still good.

---

### Post by n8bounds on 2007-05-28
yeah thanks for sharing, thats the first place I looked for my own model

[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=3340160&cc=us&lc=en&dlc=en&product=3340160&dlc=en&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=3340160&cc=us&lc=en&dlc=en&product=3340160&dlc=en&lang=en)

the win xp section has peanuts for drivers:

[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=3340160&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=3340160&lang=en)

thats why it was so hard to find what I needed, in my case

---

### Post by syko21 on 2008-03-06
New webcam driver came out but the author's blog went down.

---

### Post by knaveman on 2008-03-12
> **n8bounds said:**
> It suspends beautifully (usually down in 2 seconds and up in 5) on my dv6205us running beryl/emerald.  I have the intel video card and 2GB of memory.  I've never tried to hibernate from KDM, but when I'm logged in it always hibernates but is about 1/3 chances of coming out of it well.

I don't have a /var/log/hi... anything either... 

Hey can anyone else use there touchpad on/off button?  It SORTA works on mine, but every time it turns the touchpad back on, theres a 5 second delay and it always opens the KDE help window.

When I do it, this shows up in /var/log/messages
```

May  2 21:15:13 kernelpanic -- MARK --
May  2 21:29:04 kernelpanic kernel: [31537.108000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
May  2 21:29:04 kernelpanic kernel: [31537.108000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
May  2 21:29:04 kernelpanic kernel: [31538.044000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 21:29:07 kernelpanic kernel: [31540.628000] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.

```

I'd gladly use the setkeycodes command, but I don't know what <keycode> to tell it....



Has anyone figured this out yet? I have the same problem under gnome.

---

