---
title: "Can't set my laptop's screen resolution as 1280x768@60 (Clevo M540G)"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by maorc on 2006-06-28
Hi,

I'm trying to set the screen resolution on my laptop (**Clevo M540G**, [http://www.clevo.com.tw/products/M540G.asp]("http://www.clevo.com.tw/products/M540G.asp"))
as **1280x768 at 60Hz**. I'm using Ubuntu 6.06...

I searched through the internet and tried tons of ways but none of them worked for me... :(

My laptop uses Intel's 915GM chipset so I used the **915Resolution** utility to add the desired resolution ( 1280x768 ) to the list.
I also added this resolution to the **"Screen"** section in the **xorg.conf**.
As you probably guess, this didn't work for me. No matter what I do, i can only choose between 640x480, 800x600 and 1024x768 resolutions.

Another thing I know is that I should manually set is my monitors' **HorizSync** and **VertRefresh** values and that they are specific for my monitor. The problem is that I can't find any details about the monitor that is being used by the M540G laptop and therefore i don't know which values to set (even though i tried some).

If anybody knows about a way to get this thing work, I'll be much more than happy to know it! ;)

---

### Post by ajifans on 2006-06-28
Have you tried running?:

sudo dpkg-reconfigure xserver-xorg

It's an automated way of configuring xorg.conf, it might fill in a step that you may have missed.

---

### Post by fast1 on 2006-06-28
You should look in /var/log/Xorg.0.log to detect what happens.
You  maybe have to add the modeline in the Monitor section.
In order to get the right modeline, you may use gtf.

---

### Post by maorc on 2006-06-28
Hi,

Thanks for the quick reply! :)

First, before i'm telling you the results. let me tell you a very strange situation:
**I figured out that if I restart GNOME using CTRL + ALT + BACKSPACE, the desktop shows up with the CORRECT resolution: 1280x768@60!!! How can it be?!?!**
I can only guess that some boot script/settings prevents the system to start using the right resolution. Something that doesn't run when doing a GNOME restart (CTRL+ALT+BACKSPACE)

Anyway, I tried your suggestions and here are the results:

**ajifans:**
I already tried "sudo dpkg-reconfigure xserver-xorg" with many configuration. None of them worked...

**fast1:**
Running "gtf 1280 768 60" genrated the following lines:

  # 1280x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
  Modeline "1280x768_60.00"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync

I'm not sure whether i should add it instead of the HorizSync and VertRefresh lines, or in addition to them???

Anyway, attached is my "/var/log/Xorg.0.log" and my "/etc/X11/xorg.conf" (before adding the line) files.

Thanks again for your help and any more assitance would be really appreciated...

---

### Post by sayanchak on 2006-06-28
I'll give you an example from my xorg.conf

> Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
        Modeline "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
EndSection


So, you need to add the Modline after the VertRefresh line. BTW, my resolution is different, use the Modline that you generated yourself.

---

### Post by maorc on 2006-06-28
Thanks,

I tried that too. Added my custom line after HorizSync and VertRefresh lines and even tried overwriting them. Nothing...

Anyway, do you know anything about the strange situation i'm having?
I can set my resolution as 1280x768@60 **ONLY** after I manually restart GNOME (CTRL + ALT +BACKSPACE).

Thanks,
Maor

---

### Post by Raistlin355 on 2006-06-28
Has anyone noticed that even after you get the screen res you want it still looks small?  I noticed this when I reboot into Windows I can see more threads on the screen at the same resolution.  I wonder why that is?

---

### Post by maorc on 2006-06-28
Actually I haven't noticed... It looks OK for me. I will check it next time I switch back to UBUNTU.

Anyway, do you know anything about my problem?
I really want to start moving to linux, but these annoying problems prevent me from doing so. For now, I have no choice but stick to M$ Windows... :(

---

### Post by Raistlin355 on 2006-06-28
I am terribly sorry!!  I thought you had come up with a solution!  Anyway what I did was all the steps at:
[http://www.wiredfool.com/2005/06/15/widescreenLcdsAndUbuntuLinux](http://www.wiredfool.com/2005/06/15/widescreenLcdsAndUbuntuLinux)

That worked perfect for me, although I have to do a little twaeking of my xorg.conf file.  I'll ask around and see if anyone I know has had similar problems and what they did to fix it.

---

### Post by maorc on 2006-06-29
Thanks for the try. I used the guide and still nothing.

Again, when I log in first time, **I can't choose 1280x768@60**. But then, if I _reboot only the GNOME using CTRL+ALT+BACKSPACE_, the desktop shows up with the **correct resolution (1280x768@60)** and _I can also see it in the list of available resolutions_.

I tried to fool ubuntu and apply the 1280x768@60 resolution while it's availbale, but it isn't stay after the first full reboot.

[COLOR="Red"]PLEASE PLEASE PLEASE. If anyone knows how to fix it, please tell me! :([/COLOR]

---

### Post by xrchris on 2006-06-29
I helped someone the other day with this problem on his Clevo based Rock Pegasus 650  and all that we did was as follows

1 Installed the 915resolution package from the repositories
2 'sudo dpkg-reconfigure xserver-xorg' in terminal
3 Followed the instructions supplied in the Readme file which came with the 915resolution package.
4 rebooted.

It has worked fine since then. 
 
The wiki for the 915reolution package is at [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver) but doesnt say much more than i just posted for Dapper.

---

### Post by maorc on 2006-06-29
**[COLOR="Blue"]THANK YOU! YOU ARE THE GREATEST! IT'S WORKING![/COLOR]**

I can't believe it, three whole days for changing resolution... that's one reason why M$ still rules... :(

Anyway, here are the steps I took in order to make my laptop's (based on the 915 series chipset) screen resolution  as 1280x768@60:

** You should be root before trying any of the below steps (Open terminal ==> type "su" ==> type your root's password)

1. Recovered the original xorg.conf file that was generated after the installation. If you still have problems some of you may want to try running **sudo dpkg-reconfigure xserver-xorg** in order to generate a new xorg.file.
2. Generate a "Modeline" line using the following command: **gtf 1280 768 60**
3. Add the generated line to the "Monitor" section of /etc/X11/xorg.conf file.
4. Since I'm using Ubuntu 6.06, the "915resolution" utility was already installed. If you need to install it, go to [http://www.geocities.com/stomljen/]("http://www.geocities.com/stomljen/").
5. Open terminal as root and type **915resolution -l**. A list of supported modes is shown. After trying various situations, I figured out the best way is to override the 1024x768 mode (which was the default for my laptop). Find the line having the 1024x768 mode and check the mode number. Use the following command: **915resolution xx 1280 768 24** (where xx is the 1024x768 mode number, for example: 45).
6. Now add the following line to the /etc/init.d/bootmisc.sh file: **915resolution xx 1280 768 24** (Again, xx is the mode number). Add it after the **[ -f /etc/default/rcS ] && . /etc/default/rcS** line.
7. Open your xorg.conf file and add the following line at the end of the "Device" section: **Option "ForceBIOS" "1024x768=1280x768"**
8. Remove all modes (excpet 24 bit mode) from the "Screen" section. And in it's sub-section "Display", modify the "Modes" line to be "Modes	1280x768".

For example, after the above changes, my "Device", "Monitor" and "Screen" section of xorg.conf look like this:

.
.
.
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option "ForceBIOS" "1024x768=1280x768"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
	# 1280x68 @ 60.00 Hz (GTF) hsync: 4.26 kHz; pclk: 3.89 MHz
	Modeline "1280x68_60.00"  3.89  1280 1024 1096 912  68 69 72 71  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection
.
.
.

and the beginning of my "bootmisc.sh" looks like this:

#!/bin/sh
### BEGIN INIT INFO
# Provides:          bootmisc
# Required-Start:    $local_fs hostname
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:
# Short-Description: Miscellaneous things to be done during bootup.
# Description:
### END INIT INFO
#
# Version:	@(#)bootmisc.sh  2.85-17  04-Jun-2004  [email]miquels@cistron.nl[/email]
#

[ -z "$DELAYLOGIN" ] && DELAYLOGIN=yes
[ -z "$EDITMOTD" ] && EDITMOTD=yes
[ -f /etc/default/rcS ] && . /etc/default/rcS
915resolution 45 1280 768 24
.
.
.

9. Now save all files (xorg.conf and bootmisc.sh) and restart your computer. Good luck!

**I would like to thank ajifans, fast1, sayanchak, Raistlin355 and xrchris for helping me. It's really great to have such an active community. I couldn't do it without you! Thanks! :)**

---

### Post by cwhill on 2006-07-15
Thank You so much, Maorc!! What a perfect detail of how to get this screen resolution working properly. I have a Gateway 250E and I spent many hours scouring many forums to resolve this and yours worked exactly as described. The best part I was able to follow what your steps were accomplishing. Nice work. Now to get the sound going....

~Bill

---

### Post by Sybux on 2006-08-03
Hi,

I was having the same problem with my Dell Latitude X1.
I've try your method to resolve but I don't where I made a big mistake and my video display all expect graphical interface.

So I've decided to reinstall Kubuntu. I've then install patch for system. Just after I've made a little "sudo apt-get install 915resolution" and the installer have made all change for me. A simple reboot of the station was enough to run in 1280x768 !!

It's nice when it's in the good resolution....

---

