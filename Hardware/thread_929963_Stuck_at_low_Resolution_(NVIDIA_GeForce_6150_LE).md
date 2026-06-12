---
title: "Stuck at low Resolution (NVIDIA GeForce 6150 LE)"
date: 2008-09-25
forum: Hardware
---

### Post by RealG187 on 2008-09-25
On the "family PC" installed Ubuntu 8.04 today and am at 800x600, even with the restricted driver. It was like that as a live CD but I thought I could fix it once I install...

Older versions of Ubuntu got better resolutions on this machine...

I tried
sudo dpkg-reconfigure xerver-org

and got:
> mpg@Sherpat3md:~$ sudo dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080925125247
mpg@Sherpat3md:~$ 


---

### Post by phidia on 2008-09-25
Try "xfix" hardy seems to have issues with some hardware unfortunately plus xorg was changed in that release too.
See the note on that from [this wiki page]("https://help.ubuntu.com/community/Video").

---

### Post by RealG187 on 2008-09-25
> mpg@Sherpat3md:~$ xfix
bash: xfix: command not found
mpg@Sherpat3md:~$ sudo dpkg-reconfigure -phigh xserver-xorg 
[sudo] password for mpg: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080925134851
mpg@Sherpat3md:~$ 
Still no luck...

---

### Post by phidia on 2008-09-25
Frustrating!

From [this]("http://ubuntulinuxtipstricks.blogspot.com/2008/04/faq-hardy-upgrade.html") guide see the method here: > The new Xorg is supposed to be all nice and hotplugable, but dpkg-reconfigure xserver-xorg is no more. /etc/X11/xorg.conf is also now very barebones. This is for the hotplugability. The correct way to configure this new version of X is with the xfix command. Changing resolution is done on the fly with xrandr.

Because xorg was changed there is some confusion (at least for me) on the correct way to configure x. People use the old dpkg command but that doesn't always produce the expected results. I recommend filing a bug report.

---

### Post by RealG187 on 2008-09-25
They shouldn't have changed it, before it was simply type in "sudo dpkg-reconfigure xserver-xorg" and you could fix it

> mpg@Sherpat3md:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
mpg@Sherpat3md:~$ 


---

### Post by RealG187 on 2008-10-12
I still need help, this is annoying

---

### Post by RealG187 on 2008-12-30
I was told about a distro called Mepis that has good hardware recognition.

This page here says:
[http://windoze-blows.spaces.live.com/](http://windoze-blows.spaces.live.com/)

> Mepis 8 Beta 5
This distro is what kept me from going back to Windows. It has great hardware recognition software. Equal to Ubuntu, but community isn't as big, but just as nice.

I hear that Mepis is [based on Ubuntu/Debian]("http://www.google.ca/search?hl=en&q=Mepis+Ubuntu&btnG=Search&meta=") so all my [Deb files (local repository)]("http://bestwikiever.wikidot.com/ubuntu:local-repository") should workm except for a few that are exclusive to Ubuntu (made for Ubuntu specifically).

---

### Post by RealG187 on 2009-02-18
Okay so today I reinstalled Windoze on this machine (family PC=lots of noobs use it so it gets REALLY slow) and I was goolging the drivers for it, I was searching for the Windows driver, but actually found this:

[http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html)

Would this help?

---

### Post by RealG187 on 2009-04-08
I tried that file, it said I cant have Xwindows running so I went to recovery mode. Then it said I should quit because I was is some kinda mode it didn't like, I said no and made it not quit. It then said something about a c header not being installed and quit.

This is so annoying.

If i install the NVIDIA GLX restricted driver I get sent down to an ever lower resolution, although I can get desktop effects it's pointless when you can't even fit a window on the screen!

---

### Post by StuartIanNaylor on 2009-05-10
Hey I am a newbie to linux and ubunrtu juanty is my entrance to the linux arena. I have installed juanty on a netbook, acncient hp PIII but I also have the same problems with the Nvidia 6150. Is it just the 6150 or do all built in graphics card have a problem?

I have also read posts and configured the x-org server the wrong way in fact I have absolutely nothing in the conf files. I cant get a high enough resolution for the wxvga display and haven't a clue what to do lol.

Its typical as you install ubuntu for somebody else and it looks terrible lol

Stuart

Any help for a linux nnewbit would be most appreciated.


> **RealG187 said:**
> On the "family PC" installed Ubuntu 8.04 today and am at 800x600, even with the restricted driver. It was like that as a live CD but I thought I could fix it once I install...

Older versions of Ubuntu got better resolutions on this machine...

I tried
sudo dpkg-reconfigure xerver-org

and got:

---

### Post by jlbr21 on 2009-05-18
So what happened?? I have the same problem and you havent posted anything in a week!

---

### Post by RealG187 on 2009-05-19
> **jlbr21 said:**
> So what happened?? I have the same problem and you havent posted anything in a week!Are you talking to StuartIanNaylor or me?

StuartIanNaylor only has one post, I wonder if they will even come back.

---

### Post by genfish on 2009-06-12
I am currently having this problem with a 6150LE built into an MSI Barebones HTPC. I'm trying to get full HD resolution in Xubuntu. Back around when 6.04 - 7.04 were out, I used to use a tool called envy to setup graphics drivers. It is really simple, as at the time I was working on PC's with badly supported chipsets. I just installed the envy package now and it seems to have updated the driver, and i can get 1024x768 but not full hd yet. If anyone else wants to try envy then do:

sudo apt-get install envyng-gtk

then:

sudo envyng -t

install the driver, reboot.

---

### Post by Bas232 on 2011-02-17
Sorry to bring up an old topic, but I solved it in 10.04LTS.

1. Install 10.04 LTS (you can later upgrade to 10.10 if you want)
(fresh install, but do not install any videodriver!!)

2. Edit  /etc/modprobe.d/blacklist.conf and add:

addblacklist nouveau
options nouveau modeset=0

3. Make a root password: sudo passwd (later needed to enter root mode)

4. Download the latest nvidia driver from nVidia, ends on .run
My case: ```
wget http://uk.download.nvidia.com/XFree86/Linux-x86/260.19.36/NVIDIA-Linux-x86-260.19.36.run
```5. chmod the nvidia driver to 755

6. Reboot and enter Safe Mode, Network-Root-Shell

7. Init 3 first, then run: ./NVIDIA.....run file, and accept the creation fo the xorg.conf.

8. Reboot again, but go into normal mode.

9. Edit /etc/X11/xorg.conf to match this (in my case an Acer V243HQ 1920x1080 LCD)

In section monitor: 

HorizonSync 60.0 - 80.0
VertRefresh 55.0 - 75.0

In Section Screen under Depth 24: 
Modes "1920x1080@60"

10. Reboot again to normal mode.

11. Open the terminal and run in root (not sudo!): nvidia-settings

12. With a bit of luck it detects the modes of your card and you can set the proper ones and save the xorg.conf

13. Apply and/or reboot and the 6150LE should do 1920x1080@60Hz without problems.

Well it worked for me.
I uploaded my xorg that runs with my 6150LE.

Use the nVidia driver for this and make sure the Nouvea drivers and modechanges are BLACKLISTED!! If you forget that the driver will NOT load.

When you update to 10.10 (or kernel updates), then simply go to the ./NVIDIA.....run file, and run it again, then reboot and it works again.

Please let me know if it worked for you too, as it took me a few days to get it working.

---

