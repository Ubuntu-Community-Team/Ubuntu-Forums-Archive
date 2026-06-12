---
title: "Ubuntu 9.10 Install Problem (Please Help!)"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by SkillenUK on 2009-10-29
Hi,

I have used Ubuntu 9.04 for a few months and have attempted to install 9.10 today on my laptop (i&#8217;m a fairly new user but know a bit now, I can use the terminal etc). I have a duel boot with Windows XP on the first partition (NTFS) and I wanted to clean install Ubuntu so in the installation I selected to manually configure partitions. I selected to format the Ubunto 9.04 partition as &#8216;ext4&#8217; and set the mount point to &#8216;/&#8217; (which I guess is root). On the next screen it showed that it would format this partition and format the swap partition. The install appears fine and when I boot I get the Ubuntu boot select (I forget the name of it but it now shows that it&#8217;s a beta version with Ubuntu 9.10). When I boot to Ubuntu the screen turns black except for a flashing white curser at the top left. My USB mouse initialises (the light on the bottom turns on) and nothing else happens, no hard disk activity at all. I have checked the CD for errors and tried installing again but no luck. I can get to the terminal by selecting the recovery mode and booting using the live CD option works fine. My laptop spec (off the manufacturer website) is as follows...


  **CPU** Intel Celeron M 440 (1.86 GHz)
  **BIOS** Phoenix BIOS. Press F2 to enter
  **Chipset** Mobile Intel 943GML Express
  **Memory** 1GB DDR2 667MHz SODIMM (2 memory slots. Max 2GB)
  **Hard Drive** 80GB Hitachi HTS541680J9SA00
  **CD Drive** Optiarc DVD RW AD-7530A
  **Screen **15.4" Widescreen TFT (1280x800)
  **Video Card** ATI Radeon Xpress 200M (256MB shared) *
  **Sound Card** Realtek High Definition Audio
  **Network Card **Realtek RTL8139/810x
RaLink RT2561/RT2661 802.11a/b/g Wireless LAN **
  **PC Card** 1 x ExpressCard/54 slot (also supports ExpressCard/34)
  **Ports** 1x Microphone
1x Headphone
1x VGA
3x USB 2.0
1x Kensington Lock
1x LAN
  **Touchpad** Synaptics Touchpad
  **Battery **4UR18650F-QC-PL1A (14.4v 2200mAh)
CGR-B/458 (14.4v 2200mAh)
  **Dimensions **36 x 258 x 358 (HxWxD in mm)
  **Colour **Grey/Black
  **Weight** 2.7kg
  **Made By **Quanta AL-096 PL5C


I'd appreciate any help anyone can give me, thanks,


Chris.

---

### Post by celtic426 on 2009-10-29
You said when you select ubuntu from grub the screen goes blank.  Does this happen immediately or does the system start booting and then turn black after a few seconds?  

If it boots up and then turns black when gdm is supposed to load then that probably means its an issue with your graphics/xorg config.

---

### Post by dummy910 on 2009-10-29
have you tried selecting the **Recovery Mode** option for Ubuntu in you Grub Screen, as that will load a menu of troubleshooting tools. At 1st, I would select the top choice there, I think it's named *_boot normal_* or something like that, just to see if you can even get to a desktop. If not, you can reboot the same, into RecoveryMode and select from that menu *Check for Broken Packages*, and the system will phone home and repair any packages that may have been twisted some how(as long of course as your internet connection is on).

Do this 1st and post back with your results.

---

### Post by SkillenUK on 2009-10-29
Thanks for replying quickly!

The issue does happen immediately. I tried selecting recovery mode and I said before I got in to the terminal. I guess what I meant is I was given the command prompt (never had to use recovery mode before so I didn't know what to expect). I have installed again twice since then and now I see several things loading then it stops at the line...

[33.0463372] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

and I get another flashing pointer underneath. So I guess it does look like a video problem. I'm not sure how to go about fixing this (is it worth downloading the CD image again although the CD check reports no errors?), as I said I can boot using the live CD option so I should be able to make any changes from there. Can I some how run the broken packages script through the terminal from a live boot?

I didn't really expect it to help but I have tried reinstalling using 'ext3' (I also wanted to explore the partition options and advanced options available during installation more so I tried this). Everything is the same as before though.

---

### Post by raven01 on 2009-10-29
I have an issue with 9.10. im using jaunty and never have had this issue.

When running the live cd it goes thru its boot procedures but before it hits the desktop it says video mode not supported.

any ideas?

---

### Post by SkillenUK on 2009-10-30
Sorry Raven01 i can't help as i'm new to this myself. Can anyone offer some advice to either of us?

---

### Post by cudus79 on 2009-10-30
SkillenUK,

I think it is a problem with the ATI video card drivers, try this:
Go to System > Administration > Hardware drivers and enable the ATI proprietary drivers.

This is assuming you have installed the package xorg-driver-fglrx.

---

### Post by SkillenUK on 2009-10-30
OK, but i can only boot from the Live CD at the moment as described above. I'm guessing i can change it through that but i'm not sure how.

---

### Post by cudus79 on 2009-10-30
1. Boot in recovery mode
2. then choose the option "try to boot normally"
3. when prompted, enter your user and password to start terminal session
4. run sudo apt-get --reinstall install xorg-driver-fglrx 
5. then restart, this time try to boot as usual

It did the trick for me... Hope it helps

---

### Post by SkillenUK on 2009-10-30
Thanks to everyone who has taken time to try to help but I think I should go back to 9.04 and try 9.10 again when a newer and more stable build is available. Basically I still can't boot to Ubuntu 9.10 from the GRUB screen (it still immediately turns to a black screen with a flashing curser in the top left).

As far as the recovery mode goes it seems to load a few items (I see the scrolling white text) then it freezes most times. I have found that where it freezes seems to change (and I have been leaving it for a few minutes each time to see if it will continue but it doesn't). I have reached the menu once and I selected to repair any broken files then booted as normal to get to the terminal and tried running 'sudo apt-get --reinstall install xorg-driver-fglrx' as suggested by cudus79. This downloaded about 75mb of data and seemed to work but still no change when I boot to Ubuntu as normal.

I have installed about 5 times in total now through trying different things, it's just a shame because I have totally converted from Windows after trying 9.04 and I was really looking forwards to trying 9.10. The only way I can get to a desktop is by booting the live CD option (which works every time BTW). I may try installing 9.04 then upgrading, if this works it will be a compromise until I can try the clean install again.
   
  I’m slightly disheartened because 9.04 seemed quite solid and stable, thanks again,
   
  Chris.

---

### Post by alanwall on 2009-10-30
> **SkillenUK said:**
> Thanks for replying quickly!

The issue does happen immediately. I tried selecting recovery mode and I said before I got in to the terminal. I guess what I meant is I was given the command prompt (never had to use recovery mode before so I didn't know what to expect). I have installed again twice since then and now I see several things loading then it stops at the line...

[33.0463372] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

and I get another flashing pointer underneath. So I guess it does look like a video problem. I'm not sure how to go about fixing this (is it worth downloading the CD image again although the CD check reports no errors?), as I said I can boot using the live CD option so I should be able to make any changes from there. Can I some how run the broken packages script through the terminal from a live boot?

I didn't really expect it to help but I have tried reinstalling using 'ext3' (I also wanted to explore the partition options and advanced options available during installation more so I tried this). Everything is the same as before though.

I am still a Ubuntu newbie and am having problems with my install and saw this post and as I have an ATI card looked in the xorg repo and saw xdmx-tools. It's a tools for multihead graphics cards so you may want to install that. Hope that helps ?

---

### Post by SkillenUK on 2009-10-30
Well the thing that's got me stuck is that I can't boot to a desktop (without using a Live CD and if I use that I don't know how to affect the installation on the hard disk) and I can't really use recovery mode either (only managed to get to it once). If I could access something I'm sure this would be an easy problem to fix but I litrally get nothing when I try to boot to Ubuntu as normal.

---

### Post by SkillenUK on 2009-10-30
Oh does anyone know where I can get the 9.04 image again because I seem to have lost the CD?

---

### Post by virtudtierra on 2009-10-30
So, fglrx works on UBUNTU 9.10??
I've Ubuntu 8.10, and I still 've the hope it, someday, ubuntu 9.10can work on ATI XPRESS 200M....

so... works ubuntu 9.20 on ATI Xpress 200M...

best regards...

Jorge


> **cudus79 said:**
> SkillenUK,

I think it is a problem with the ATI video card drivers, try this:
Go to System > Administration > Hardware drivers and enable the ATI proprietary drivers.

This is assuming you have installed the package xorg-driver-fglrx.

---

### Post by VDSA on 2009-10-30
hi

not sure if this is the right thread so pls let me know if i should be posting elsewhere, thx

downloaded ubuntu nbr yesterday and made a live usb. i booted from that on my 901 and was really impressed with how good the os looks and the fact that my wireless connected without a hitch

unfortunately, when i installed it to an external hard drive using the build in installer from the ubuntu desktop i had a problem. the install seemed to go okay except for one issue. half way through, a red icon (exclamation mark inside an explosion?) in the top panel appeared and a small error message came up. not sure what it was (foolishly i assumed it was unimportant) so i continued with the install. (I still don't know if it relates to the non-booting). When i rebooted, the boot went fine till part way through. The white ubuntu logo came up and then disappeared after 10ish seconds. The screen just went black from there without any visual signs of life (except a dim backlight from the panel)

nothing that i tried worked except for hard rebooting or ctrl-alt-del which only rebooted to the same issue :(

any help would be appreciated. i'm kindof new to linux, but hoping to learn. happy to answer any questions regarding set up etc

eee pc 901 - windows xp - 12GB - with no mods

---

### Post by SkillenUK on 2009-10-31
I said that I may try installing 9.04 again then updating through the update manager. I have tried that today, the update looked OK until I was around 50% in to the updating packages stage. The screen flickered and I had a message saying that I was now in a 'low graphics mode'. The hard disk was still active so I left it. Around 15 minutes later the screen turned blank and nothing else happened. I reset the computer now I can boot to either...

Ubuntu 9.10, kernel 2.6.31-14-generic
Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
Ubuntu 9.10, kernel 2.6.28-11-generic
Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.10, memtest86+

also Windows XP.

If I boot using the top option (31-14) I get a 'starting...' message and nothing else, it appears to pretty much be the same issue I had before. If I boot the 28-11 option it kind of works (well I'm in that now). It seems less than perfect, Firefox was completely crashing the computer so I've reinstalled that now it's OK. But the graphics related options do not seem right. For example I can only have the Visual Effects set to none (normal or extra will not work). I have tried repairing packages in the recovery mode as well but it reports that nothing has been updated. I have installed the X.Org ATI driver through the software centre but this hasn't changed anything. Now that I can get to a desktop I'm thinking this should be fixable. Does anyone have any suggestions that can get me running normally from here?

Sorry to keep on dragging this thread out more but I am really keen to try 9.10 properly.

Chris.

---

### Post by dummy910 on 2009-10-31
From what I've read, the ATI drivers from ATI are not ready for the prime time that is Ubuntu 910.

The box I type this reply from has an **ATI Technologies Inc RV350 AP [Radeon 9600]** installed, and I have yet to tweak-install anything ATI or mess with a single charactor in my xorg.conf file.

By using the default xorg.conf file that the 910 upgrade installed on this machine, I can have all the 3d graphics I want, as in the 3d rotating cube, openGL in games, and 3d screensavers, wobbly windows, you name it.

Here's my stock 910 xorg.com file:
```
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
Identifier	"Configured Monitor"
EndSection

Section "Screen"
Identifier	"Default Screen"
Monitor	 "Configured Monitor"
Device	 "Configured Video Device"
DefaultDepth	24
EndSection

Section "Module"
Load	"glx"
EndSection

Section "Device"
Identifier	"Configured Video Device"
Driver	"ati"
EndSection
```

of course, dont forget to either reboot or restart your xserver if you make any changes to your xorg.conf file ;)

---

### Post by bingung99 on 2009-10-31
> **SkillenUK said:**
> 
   
  I’m slightly disheartened because 9.04 seemed quite solid and stable, thanks again,
   
  

I agree that 9.04 is stable...9.10 is a disappointment...I did an upgrade via the Update Manager....after the installation, my PC restarted again and again...I lost the 9.04 and my confidence with Ubuntu....Hopefully the team fix tis quick....:(:(

---

### Post by VDSA on 2009-11-16
it never did work properly on my external :confused:

but i took the plunge and installed it straight to the ssd which surprisingly, worked fine :popcorn:

thx

---

