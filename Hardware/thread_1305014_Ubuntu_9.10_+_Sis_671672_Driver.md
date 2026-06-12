---
title: "Ubuntu 9.10 + Sis 671/672 Driver"
date: 2009-10-29
forum: Hardware
---

### Post by andydch on 2009-10-29
Anybody has the driver?

Thanks

---

### Post by afalope on 2009-10-30
yeah, im looking for this too, the one i had for 9.4 was one from 8.10 i think and that worked but its not working anymore

---

### Post by typhoon22 on 2009-10-31
Same here, I have this .deb package:

xorg-driver-sis671_0.9_i386

If you change your xorg.conf to include the driver "sis" it does have some additional info in the xorg.0.log about where the driver came from, who wrote it etc... but after 2 hours of trying to work out what was wrong i don't want to break my laptop again :(

If I'm man enough I'll do it later and put the info up.

I've checked Barros Lees blog too. He's done the windows 7 3d driver, but no-one has had a driver out of him since Hardy.

Edit: not Jaunty...errm at least 8.10 though, whatever creature that was :P

---

### Post by typhoon22 on 2009-10-31
By the by...Can someone post up an xorg.conf for me that enables the 1280x800 res for the VESA driver please?

This screen res is driving me nuts. I've edited my conf, but it still only gives me 800x600. Currently my xorg.conf reads:

Section "Device"
    Identifier    "Configured Video Device"
        Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
    Depth 24    
    Modes "1280x800" "800x600" "640x480"
    EndSubSection
EndSection

thanks

---

### Post by Elzigzag on 2009-11-08
Have you tried this one? <http://nacho.larrateguy.com.ar/2009/07/11/drivers-de-sis-771671-para-xorg-1-6-mandriva-2009-1-ubuntu-jaunty-9-04/> I'm on Ubuntu 9.10, the Koala creature and it works. Although no 3D but at least screen resolution is acceptable.

---

### Post by E-mol on 2009-11-08
You will never (!) get 3D with this card.. sorry, i have tried 1,5 year by now.. found a portugese 3D-driver for linux, but it whas old and buggy. Or maybe you will.. :)

For some days ago i got this link on my mail from a good friend:
[http://barroslee.blogspot.com/2008/02/sis-linux-3d-driver-supported.html]("http://barroslee.blogspot.com/2008/02/sis-linux-3d-driver-supported.html")
If you can live with an older dis it could be something maybe :)
And.. this link: [http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads]("http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads") might be usefull too.
I have stopped my work with the computer I had with this card, but it was okay for normal computing when i sold it; music, dvd, net and Diablo II ;)
It was with Ubuntu 9.04 at the end, before that 8.10.

But keep fighting if you can, maybe it will be possible one day.
Until then try to compile the driver youself.
The big guru in this game is Barros Lee. His blog can be usefull for you. It is the first link.
The second link have a lot of different stuff for sis.. some of it was usefull for me :)

Hope I have helped a little.. Good luck guys :)

---

### Post by andydch on 2009-11-08
When using Jaunty, i applied xorg-driver-sis671_0.9_i386.deb. It worked but 2D.
One week ago, I found one article somewhere in this forum if xorg-driver-sis671_0.9_i386.deb can be applied into Karmic, too. But, I have to configure xorg.conf to be like below

Section "Device"
    Identifier     "Device0"
    Driver         "sis671" 
EndSection

And then, It Works!!! :KS:KS:KS
The resolution can 1280x800

:D:D:D

---

### Post by Elzigzag on 2009-11-09
Yeap, there are many 2D drivers (or at least a couple of them) working on Ubuntu 9.10 Karmic Koala. Some of them require some xorg.conf editing, one of of them seems to nedd no editing at all. Anyway we all arrive a 1200x800 resolution and that's all of it. 
Of course 3D ain't vital, you can do it without it. But it's distressing not to be able to run the laptop to its best (well, best, I guess I should have avoided this sh*tty SiS card). 

There are so many people all around the world, I just can't stand the idea that 3D keeps forbidden for all of us.  We're disappointed...

---

### Post by finatai on 2009-11-11
I used this driver on Ubuntu 9.10:

[http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671_0.9_i386.deb](http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671_0.9_i386.deb)

To install run:

sudo dpkg -i xorg-driver-sis671_0.9_i386.deb

then restart the PC.

You have to edit your xorg.conf, Karmic Koala does not use it by default so you have to generate this, to do so run:

sudo stop gdm 

then 

sudo Xorg -configure

This will generate an xorg.configure.new file copy this to /etc/X11/xorg.configure

Start X and change your screen resolution

sorry but im not good enough writing in english ...

---

### Post by azedddine on 2009-11-13
i used the sismedia driver (it's disponible in the same website) and xorg.conf is automatically configurated, i think that this driver is better than that other [http://ncc-1701a.homelinux.net/~linu...1_0.9_i386.deb](http://ncc-1701a.homelinux.net/~linu...1_0.9_i386.deb)

---

### Post by osana412 on 2009-11-16
My Laptop is Zyrex, assembling in Indonesia, when I use Windows 7, the resolution can be 1366x768 (wide screen) but when using ubuntu (I using xorg-driver-sis671_0.9_i386.deb),  I never get the correct resolution, my screen blank. How can it? Now I use Vesa (change the xorg.conf) but still same, the resolution not good (screech, only 1024x768 ). Can somebody help me? Thnx b4.

---

### Post by haseeF4000 on 2010-01-29
E1zigzag :thank you for give me the pointing.I am just suffering the resolution of ubuntu9.10.
thanks,man

---

### Post by MichealH on 2010-02-01
is there a 64 bit version for jaunty to run on karmic?

---

### Post by Elzigzag on 2010-02-01
> **haseeF4000 said:**
> E1zigzag :thank you for give me the pointing.I am just suffering the resolution of ubuntu9.10.
thanks,man

I'm glad you made it. Congratulations! That's the way we all have learnt! (and are still learning ;))!!!

---

### Post by E-mol on 2010-02-01
> **MichealH said:**
> is there a 64 bit version for jaunty to run on karmic?

Karmic is the newest "stable" release of Ubuntu. Jaunty was the one before. You can get them both in 64-bit, thats what I'm using. 
If it is something with a 64-bit driver I can't help you, but you can try compile your own version. Theres some good guides aroundm one I have used is [http://ubuntuforums.org/showthread.php?t=323939]("http://ubuntuforums.org/showthread.php?t=323939").

E-mol

---

### Post by purct on 2010-02-04
> **MichealH said:**
> is there a 64 bit version for jaunty to run on karmic?


I am running karmic 64-bit on a ASUS K5DC laptop. the SiS driver that came with Karmic doesn't find the my video card so I have downloaded one from [http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads](http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads)

but had no luck so I am currently using VESA Driver @ 1024x768 ...

It appears that the reason I can't get SiS671 driver to work is that my laptop LCD is failing to supply EDID information.  If I plug and EDID compliant screen into the laptop the driver works.  

The driver detects that I have and LCD display (see Xorg extract below) but max and pref. res is 0x0. 

EXTRACT XORG:

(II) Module "ddc" already built-in
(--) SIS(0): Detected SiS307LV video bridge (Charter/UMC-1, ID 7; Rev 0xe1)
(--) SIS(0): No CRT1/VGA detected[B]
(--) SIS(0): Detected LCD/Plasma panel (max. X 0 Y 0, pref. 0x0, RGB24)[/B]
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): CRT1 gamma correction is enabled
(II) SIS(0): Separate Xv gamma correction for CRT1 is disabled
(II) SIS(0): CRT2 gamma correction is enabled
(--) SIS(0): Memory bandwidth at 32 bpp is 1006.35 MHz
(--) SIS(0): Detected LCD PanelDelayCompensation 0x00 (for LCD=CRT2)
(--) SIS(0): Detected LCD PanelDelayCompensation 0x00 (for LCD=CRT1)
(--) SIS(0): 302LV/302ELV: Using EMI 0x6a0d7039 (LCD)
(--) SIS(0): CRT2 DDC probing failed
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 340 MHz
(II) SIS(0): Replaced entire mode list with built-in modes
(II) SIS(0): Correcting bogus CRT2 monitor HSync range
(II) SIS(0): Correcting bogus CRT2 monitor VRefresh range
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): Monitor0: Using hsync range of 30.00-80.00 kHz
(II) SIS(0): Monitor0: Using vrefresh range of 59.00-61.00 Hz
(II) SIS(0): Monitor0: Using vrefresh value of 71.00 Hz
(II) SIS(0): Clock range:  10.00 to 340.00 MHz
(II) SIS(0): Not using default mode "800x600" (unknown reason)
(II) SIS(0): Not using default mode "800x600" (unknown reason)
(II) SIS(0): Not using default mode "800x600" (unknown reason)
(II) SIS(0): Not using default mode "800x600" (unknown reason)
.
.
.[B]
WW) SIS(0): Mode pool is empty[/B]
(EE) SIS(0): **************************************************
(EE) SIS(0):                       ERROR:
(EE) SIS(0): No valid modes found - check VertRefresh/HorizSync
(EE) SIS(0):                   END OF MESSAGE
(EE) SIS(0): **************************************************
(II) UnloadModule: "sis671"


ddcprobe & get-edid fail, here is the getedid output:

[I]
get-edid: get-edid version 2.0.0

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0xc2d66 "SiS"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination does not support DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged[/I]

I have tried configuring xorg.conf with modelines VertRefresh & HorizSync etc, but it doesn't work.


In Windows 7 the screen is configured as generic monitor and the EDID information is set in registry(it appears that manufacturers can override invalid/non compliant hardware by configuring an INF file). 

Is there a way to send EDID information into SIS Driver or XOrg?  it appears that some X drivers (for example NVidia) can override/ignore EDID.  But I haven't found any such Option for SiS671



Thanks

---

### Post by bejostobbo on 2010-02-05
I found sis671 driver for Ubuntu 9.10
Res : 1280*800
Hope can help.
Download link :
[http://sharecash.org/download.php?file=366437](http://sharecash.org/download.php?file=366437)
or
[http://uploading.com/files/1cc9be67/xorg-driver-sisimedia_0.9-1_i386.deb/](http://uploading.com/files/1cc9be67/xorg-driver-sisimedia_0.9-1_i386.deb/)

---

### Post by purct on 2010-02-12
I have managed to get my ASUS X5DC LAPTOP working on Karmic 64-bit @ 1360 x 768. I had to modify the src-code because Xorg couldnt get Screens EDID information and detected display as 0x0.  have a look at my blog....If I can help i will. ;)

I am looking to modify the driver to accept EDID information from a file at the moment.

---

### Post by jb_barroso on 2010-03-30
SiS M671/M672 driver for xorg xserver 7.5 on Debian / Sidux (Working on Ubuntu 10.04):

[http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/](http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/)

---

### Post by Elzigzag on 2010-03-30
Following comments:
- No, it doesn't provide 3D acceleration support (Says Esteban Ordano)
- Yes, it handles a dual monitor setup (Says Esteban, provides a How-to post in Spanish)

More info? take a visit to his site.
[http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/](http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/)

---

### Post by mhgsys on 2010-05-11
Best to link everyone to here; [http://ubuntuforums.org/showthread.php?t=958967&page=45](http://ubuntuforums.org/showthread.php?t=958967&page=45)


The most active thread on sis 771/671 containing lot's of contributing users. (like you purct.. great work on the recompiled driver for asus)

Link contains info for running sis 771/671 on 8.04 / 8.10 / 9.04 /9.10 /10.04..

---

### Post by guyver2095 on 2010-05-17
The driver exists and works fine in 2d , the author Mr. Baros Lee is  working on a new version a 3d one, please ask nicely to Mr. Barros Lee  to this email address [email]barroslee@gmail.com[/email]  and he will answer you and send the driver.

greetings from Mexico
Javier García Prieto.

> **andydch said:**
> Anybody has the driver?

Thanks

---

### Post by guyver2095 on 2010-05-17
The driver exists and works fine in 2d , the author Mr. Baros Lee is  working on a new version a 3d one, please ask nicely to Mr. Barros Lee  to this email address [email]barroslee@gmail.com[/email]  and he will answer you and send the driver.

anyway I send the driver that he send to me attached to this message

greetings from Mexico
Javier García Prieto.

> **mhgsys said:**
> Best to link everyone to here; [http://ubuntuforums.org/showthread.php?t=958967&page=45](http://ubuntuforums.org/showthread.php?t=958967&page=45)


The most active thread on sis 771/671 containing lot's of contributing users. (like you purct.. great work on the recompiled driver for asus)

Link contains info for running sis 771/671 on 8.04 / 8.10 / 9.04 /9.10 /10.04..

---

### Post by Elzigzag on 2010-05-17
> **mhgsys said:**
> Best to link everyone to here; [http://ubuntuforums.org/showthread.php?t=958967&page=45](http://ubuntuforums.org/showthread.php?t=958967&page=45)


The most active thread on sis 771/671 containing lot's of contributing users. (like you purct.. great work on the recompiled driver for asus)

Link contains info for running sis 771/671 on 8.04 / 8.10 / 9.04 /9.10 /10.04..


Please, if you're reading and/or posting jump here [http://ubuntuforums.org/showthread.php?t=958967&page=47](http://ubuntuforums.org/showthread.php?t=958967&page=47)

BTW I wonder, if Barros Lee has the 3D driver what's the purpose of having and not delivering it? SiS should deliver it, but doesn't. I don't understand.

---

### Post by timpool on 2010-11-16
somehow i did not getting it solved with this driver and the edited xorg.conf
I am running a SIS Mirage3+ 672MX and the Maverick 10.10.
What went wrong with that?

i tried with vesa, sis671, changed the Modes in the xorg.conf and so on...
What else can i do?

---

