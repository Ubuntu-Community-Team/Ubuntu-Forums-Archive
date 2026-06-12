---
title: "Slow computer when running Ubuntu"
date: 2014-07-15
forum: Hardware
---

### Post by n-sallis on 2014-07-15
I have a lenovo y500. It's a fairly nice laptop (i7 processor, 8gig ram...). It cam with windows 8 and was insanely fast with that. it would boot in like 10 seconds, and everything would open really snappy. However, I hate windows 8 and so I threw ubuntu 14.04 on it. (it was actually quite a process because it had a lot of software on it to stop you from putting other os's on it. Anyway, ubuntu is really slow on it. like it ran faster off the live boot than when it's on my hdd. I have all the drivers installed (I chose the newest). Finally I installed win8 on my external (sort of like a live boot) and run it on a usb3.0 port, and that is even quite a bit faster than when I run Ubuntu off the internal drive. Any ideas where to start? I did an hdparm and got 106.43 mb/s as a buffered speed. I don't know what else to check.

Thanks in advance for any help.
Nick

PS. the boot takes about a minute and a half, and once I've logged in it takes quite a few minutes until things are running smoothly.

---

### Post by WinEunuchs2Unix on 2014-07-15
Pressing <Ctrl>+<Alt>+T gives you a terminal window.  From there you can type:

```
gedit /log/var/kern.log
```

and look at the Kernel log.  Press the end key to see the most recent and look for error messages like "waiting 16000 microseconds" or something like that.

The ability to view the Kernel messages is just one of the advantages Unix / Linux / Debian / Ubuntu have over all Windows and DOS products from Micro$oft.

(The only advantage of having no money is no one wants to sue you).

---

### Post by n-sallis on 2014-07-18
there's nothing in that file. It just comes up blank.

---

### Post by Bucky Ball on 2014-07-18
Open a terminal and type 'top'. What is hogging your resources, if anything? Should be at the top of the list frequently and using a lot of resources. Also, at the top of that page, is your /swap being used? What are the CPUs doing? Is the RAM being thrashed? Give us a screenshot if the machine lets you (attach it with 'Go Advanced' and the paperclip icon).

---

### Post by WinEunuchs2Unix on 2014-07-18
My apologies I transposed the first two words.  It should read:

```
gedit /var/log/kern.log
```

When the file opens up press <Ctrl>+<End> to see the most recent entries.  For example my log runs from July 13th to July 18th.

---

### Post by WinEunuchs2Unix on 2014-07-18
That "top" is sure cool.  Wish I'd seen that before downloading System Indicator Load PPA.

---

### Post by Bucky Ball on 2014-07-18
You can also use 'htop'. You may need to install it. It's much the same, but prettier. ;)

---

### Post by WinEunuchs2Unix on 2014-07-18
htop is even cooler.  the fonts don't work out well with my translucent black background and green font.  I'll have to play with it :D

EDIT: I played with it and calling with the -C parameter makes it looks really slick with my colour scheme.

---

### Post by Bucky Ball on 2014-07-18
> **WinEunuchs2Unix said:**
> 

EDIT: I played with it and calling with the -C parameter makes it looks really slick with my colour scheme.

Neat trick. ;)

---

### Post by n-sallis on 2014-07-26
so my swap is running at 8000000kb! I have plenty of room with ram. I have at least 8 gigs if not 16 (don't remember). I guess I should change my swappyness, am I seeing that right?

---

### Post by n-sallis on 2014-07-26
never mind, I was looking at the wrong thing. my swap is at 0. Also, if I run win8 in virtual box in ubuntu it runs fairly well (considering), which leads me to believe that it is a linux related thing. BTW, changing the swappiness didn't help (obviously).

---

### Post by WinEunuchs2Unix on 2014-07-26
Ahhh the system is swapping itself to death.

8GB of swap being used is ALOT.  I had 26 MB of 8 GB swap being used and 2GB out of 4GB of real RAM being used.

Type "sudo swapoff -a" and see if your machine is snappier.

I just did that on my laptop with no ill-effects.  It's not any faster or slower and I have 7 tabs open in google chrome on the built-in display and TV documentary on the External 32" LCD display.

---

### Post by Bucky Ball on 2014-07-27
> **WinEunuchs2Unix said:**
> Ahhh the system is swapping itself to death.

8GB of swap being used is ALOT.  I had 26 MB of 8 GB swap being used and 2GB out of 4GB of real RAM being used.

Type "sudo swapoff -a" and see if your machine is snappier.

I just did that on my laptop with no ill-effects.  It's not any faster or slower and I have 7 tabs open in google chrome on the built-in display and TV documentary on the External 32" LCD display.

OP has confirmed they were looking at the wrong thing and swap is at 0.

---

### Post by WinEunuchs2Unix on 2014-07-27
> **Bucky Ball said:**
> OP has confirmed they were looking at the wrong thing and swap is at 0.

Yes I saw this the second time but not when I wrote the post.  "my blind".

---

### Post by n-sallis on 2014-07-28
I'm thinking it might have to do with either my HDD speed, or my graphics card since my Graphics card since the driver for my GC seamed to mess things up with boot time before (and added some extra screens annd time).

---

### Post by WinEunuchs2Unix on 2014-07-28
Still interested in seeing the output from your /var/log/kernel.log, /var/log/Xorg.0.log and /var/log/dmesg files.  It's starting to sound like a problem with Xorg not being able to handle your monitor's resolution properly on boot.  I have that problem with a second monitor plugged in during boot up leads to a 2 to 4 minute delay before things "calm down".  My temporary solution was to unplug the secondary monitor during boot up but it will be fine tuned eventually.

---

### Post by Linux_Son on 2014-07-29
I learned about HTOP from this thread. Very useful and cool indeed. Thanks

---

### Post by WinEunuchs2Unix on 2014-07-29
It's useful until you add up all the thread process percentages and see it's greater than 100% LOL.

Just exaggerating... it's due to multiple cores and it is still a great utility.  Thanks to Bucky for recommending it.

---

### Post by n-sallis on 2014-07-29
[**[COLOR=#000000]WinEunuchs2Unix[/COLOR]**]("http://ubuntuforums.org/member.php?u=1925810"): do you have any idea how that could be fixed/tweeked? Xorg does seam to be causing a lot of problems, so that might really be it.

---

### Post by WinEunuchs2Unix on 2014-07-30
I spent a couple of hours playing around with dual monitors and xorg.conf.d/10-monitor.conf setup tonight and all I got was a few more grey hairs and a black screen on boot up.  

I did come across a post where xorg and other ubuntu stuff can be reset to initial state without all the modifications I put in.  I'm thinking of trying that because the deeper I dig into apport.log, syslog, kernel.log, Xorg.0.log and dmesg.log the more problems I find to solve.  It's confusing because a lot of websites have instructions that do not apply to the current version so the suggestions do not work and in some cases mess things up I think.

From terminal type in "ls /var/crash" (without the quotes).  Do you see any crash files?  If a crash file is created on bootup that could take a couple of minutes I think.

I'll keep you posted on my experiments to reset Xorg n-sallis.

---

### Post by ian-weisser on 2014-07-30
> **n-sallis said:**
> PS. the boot takes about a minute and a half, and once I've logged in it takes quite a few minutes until things are running smoothly.

That pretty much describes the classic symptoms of two (related) faults:

A long boot is often due to a hardware incompatibility that the kernel spends a lot of time working around or probing or resetting. Like, say, having problems getting a not-quite-compatible video card to work.

A long login is often due to X encountering problems probing, handling and trying to configure the display(s)...like, say, having problems using a not-quite-compatible video card that the kernel claims is available and usable.

That's where I would start looking further.

---

### Post by WinEunuchs2Unix on 2014-07-30
Excellent summary.  That's exactly where I'm at now on my Toshiba Laptop with Toshiba 32" TV via VGA analogue and 1368x768 custom resolution.  The water is muddied by a few keyboard scan code to key code remapping programs in both udev and xorg.  It was further muddied by "What's this compiz? I'll just apt-get remove it... LOL".

The water is muddied by a new Intel Centrino Advanced-N 6235 mini PCI that is spamming dmesg every 15 seconds claiming victory at discovering device 7-2 on USB 1.1 hub that doesn't even exist.  It is muddied by a new wireless keyboard and mouse that gets loaded a bunch of times.  There is an existing keyboard and touchpad that work ok.  Oh yeah it's muddied by a USB 3.0 powered hub that has no name :(.

  But muddy waters help us appreciate clean lakes :D.

---

### Post by n-sallis on 2014-08-01
so there were 3 crash reports, but non of them were from startup (freecad crashed on me and they are from there). None of the other logs exist. I don't know if I need to turn them on or what, but /var/log... didn't work, it couldn't find the directory.

---

### Post by ian-weisser on 2014-08-01
> **n-sallis said:**
> ...but /var/log... didn't work, it couldn't find the directory.

Huh, *what* couldn't find /var/log?

If you open a terminal and try the following, what happens?
```
ls /var/log
```

---

### Post by WinEunuchs2Unix on 2014-08-01
OK a little WIP update... I used gedit /var/log/Xorg.0.log and found these entries:

```

[    30.977] (**) Option "xkb_rules" "evdev"
[    30.977] (**) Option "xkb_model" "pc105"
[    30.977] (**) Option "xkb_layout" "us"
[    31.207] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[   202.117] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   202.147] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   381.321] (II) intel(0): resizing framebuffer to 2648x800
[   381.322] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   381.356] (II) intel(0): switch to mode 1368x768@60.0 on VGA1 using pipe 1, position (0, 0), rotation normal, reflection none
[   381.374] (II) intel(0): switch to mode 1368x768@60.0 on VGA1 using pipe 1, position (1280, 0), rotation normal, reflection none
```

We see that Xorg is reusing a cached keyboard table to save time.  However it is taking 350 seconds to load the 3 different tables.  I had been playing around using googled advice to map MS Wireless 2000 keyboard to Toshiba Satellite 300 Fn+F6 and Fn+F7 hotkeys to turn screen brightness down and up.

When you look at the cached keyboard table directory you see:

```
/var/lib/xkb$ lsREADME.compiled                                      server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
server-04CEA3533386D6DAA8EBF50A4D55AB44748BB412.xkm  server-CE474029094E0F5C00580F52F6E6C89070D30F64.xkm
server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm  server-E9ACA9BA56449A36A253B88BFB5E6377D19B6218.xkm

```

Bug reports from 2012 say you can simply delete these files, so I delete all of them (except README.compiled) with "[COLOR=#333333][FONT=monospace]sudo rm -f /var/lib/xkb/server*" [/FONT][/COLOR]and hope for the best.

Strangely the file "README.compiled" is misnamed.  It should be called "README.im_not_compiled_im_a_text_file" LOL

On your system checking the time stamps could lead you to unique problems on your system.

---

### Post by WinEunuchs2Unix on 2014-08-02
In the end I ended up yanking the Intel Centrino Advanced-N 6235 802.11 bgn 300 Mbps mini PCIe Wifi Network Adapter out of the motherboard and putting the original Intel 3945 abg (Golan) 54 Mbps mini PCIe Wifi Network Adapter back in.  

Now "gedit /var/log/Xorg.0.log" looks like this:

```

[    11.252] (**) Option "xkb_rules" "evdev"
[    11.252] (**) Option "xkb_model" "pc105"
[    11.252] (**) Option "xkb_layout" "us"
[    12.848] (II) intel(0): EDID vendor "SEC", prod id 14145
[    12.848] (II) intel(0): Printing DDC gathered Modelines:
[    12.848] (II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz eP)
[    19.459] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.980] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.015] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.068] (II) intel(0): resizing framebuffer to 1368x800
[    21.075] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    21.092] (II) intel(0): switch to mode 1368x768@60.0 on VGA1 using pipe 1, position (0, 0), rotation normal, reflection none
[    21.232] (II) intel(0): resizing framebuffer to 1280x800
[    21.241] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    23.140] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
```

Instead of 381 seconds (6 minutes) we are looking at 23 seconds for the initialization to complete.  Another factor is to unplug the D-Sub VGA cable to the flat screen TV during cold boots so compiz doesn't generate errors.

The Advanced-N 6235 was known to cause errors by spamming dmesg with "New USB Device 7-2 found...." every 14 seconds.  It may have also caused the USB S/PDIF audio driver to not load properly.

Now back to solving the OP's slow booting problem when he posts some log info.

---

### Post by WinEunuchs2Unix on 2014-08-02
Just upgraded to Kernel version 3.15.7 which was released 5 days ago.  I had put off upgrading until Ubuntu came out with an pseudo-official announcement but gave up waiting.  3 or 4 websites had come out with their own announcements and instructions so I followed a couple of them.  One of the website's instructions generated error messages so I reinstalled (before rebooting!) using another website.

After reboot the Xorg.0.log file showed additional speed improvements.  This was anticipated because part of the Kernel changelog shows fixes to various Intel Kernel modules / microcode and my machine is heavily branded "intel inside".

Comparing to the two previous posts you can see the faster load times below:
```

[    12.335] (**) Option "xkb_rules" "evdev"
[    12.336] (**) Option "xkb_model" "pc105"
[    12.336] (**) Option "xkb_layout" "us"
[    14.974] (II) intel(0): resizing framebuffer to 2304x800
[    14.984] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    14.996] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 1, position (0, 0), rotation normal, reflection none
[    15.005] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 1, position (1280, 0), rotation normal, reflection none
[    23.436] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.618] (II) intel(0): resizing framebuffer to 2648x800
[    24.618] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    24.660] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 1, position (1280, 0), rotation normal, reflection none
[    24.685] (II) intel(0): switch to mode 1368x768@60.0 on VGA1 using pipe 1, position (1280, 0), rotation normal, reflection none
[    26.901] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    77.375] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    77.408] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm

```

The "(II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm"lines mentioned in the post 2 comments ago are still there but they are regenerated ones and it is unknown if they made things better but, they didn't make things worse.

Booting with the external flat screen TV plugged in still generates an error message called "Giant wall of text dialog when resolution switch fails" in numerous google searches.  This error is also described in a different bug report by goggling "[COLOR=#333333][FONT=monospace]Could not apply the stored configuration for monitors".[/FONT][/COLOR]  

People recommend removing files in "~/.config" directory to resolve the error.  Unfortunately like 90% of the recommendations this applies to a previous Kernel / Ubuntu version and the in this case the directory does not exist. The error is inconvenient but a low priority on my very big tweaking To-Do list.

Switching back to the native Intel Wireless 3945 abg (Golan) adapter gives a solid 54Mbps speed.  The other adapters (internal and USB adapter) might report 65 Mbps, 114 Mbps and even 300 Mbps through iwconfig when in reality throughput was zero.

I am stubborn and am now looking at getting a tale top antenna wifi that can plug in through the USB 3.0 adapter or native USB 2.0 laptop ports.

Although the last three posts on this thread lead to success the details will likely have ABSOLUTELY NOTHING to do with your case.  Consider this a framework on how to find the cause of errors and deal with them.  Consider this a warning on what type of pitfalls you might encounter on your journey.

Keep in mind Ubuntu 14.04 is bleeding edge technology of the year.  Soon I will try Ubuntu 12.04 which has 5 years of Long Term Release support.  First I have to get that new Yumi Install working to the 64 GB USB 3.0 flash drive / thumb drive / portable pen drive.  Maybe a slightly older version of Linux would be more acceptable to an average user?  Time will tell.

---

### Post by WinEunuchs2Unix on 2014-08-03
A few hours after upgrading to Kernel 3.15.7 the latest version 3.15.8 was installed and the earlier speed improvements were even faster:

```

[    10.768] (**) Option "xkb_rules" "evdev"
[    10.768] (**) Option "xkb_model" "pc105"
[    10.768] (**) Option "xkb_layout" "us"
[    13.369] (II) intel(0): resizing framebuffer to 2304x800
[    13.384] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    13.404] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 1, position (0, 0), rotation normal, reflection none
[    13.421] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 1, position (1280, 0), rotation normal, reflection none
[    26.894] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.826] (II) intel(0): resizing framebuffer to 2648x800
[    27.838] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    27.860] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 1, position (1280, 0), rotation normal, reflection none
[    27.924] (II) intel(0): switch to mode 1368x768@60.0 on VGA1 using pipe 1, position (1280, 0), rotation normal, reflection none
[    30.244] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    39.948] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    40.000] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
```

Kudo's to the Linux Kernel Team :)

---

### Post by n-sallis on 2014-08-04
So apparently none of those logs (including boot.log and the nvidia upstart log) are filled (they are literally empty). That seams weird to me snce I'd expect at least boot.log to have something.I've looked through quite a few of the log files with nothing showing up. Your log files cerrtainly look very different. Any ideas?

---

### Post by WinEunuchs2Unix on 2014-08-04
On my system "/var/log/boot.log" doesn't have any useful information and is very small.  I don't have Nvidia graphics hardware so I have NO "[COLOR=#545454][FONT=arial]/var/[/FONT][/COLOR][COLOR=#545454][FONT=arial]**log**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#545454][FONT=arial]**nvidia**[/FONT][/COLOR][COLOR=#545454][FONT=arial]-prime-[/FONT][/COLOR][COLOR=#545454][FONT=arial]**upstart**[/FONT][/COLOR][COLOR=#545454][FONT=arial].[/FONT][/COLOR][COLOR=#545454][FONT=arial]**log**[/FONT][/COLOR]" log file.

Other people have reported bugs on freezing using Ubuntu 14.04 and the Nvidia graphic drivers.  You can start looking for solutions here: [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1288572](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1288572) This bug report references 4 or 5 other bug reports that you can also link to.

Sorry I can't be of much use since I can't test the Nvidia software configuration recommendations in the bug reports.

---

