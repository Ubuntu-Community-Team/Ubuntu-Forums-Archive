---
title: "How would I install downloaded debian Package???"
date: 2008-11-17
forum: General Help
---

### Post by volaer on 2008-11-17
Guys, I have downloaded a driver that I need for my laptop (by searching through the net). It is a debian package that contain all these:

X.Org X server -- Intel i8xx, i9xx display driver and New Intel 4 series chipset support
Main new features included within this release are
* New Intel 4 series chipset support
* Improved 965 exa render performance
* Integrated HDMI support
* SDVO-HDMI support (e.g ASUS P5E-VM board) This package is built from the X.org xf86-video-intel driver module. 

However, everytime I double click the debian package ,to install it, an error will appear that says:

**Error: Conflicts with the installed package 'xserver-xorg-viedo-i810'**

How can I solve this? And how can I install the package?

By the way, my video is Intel 4 series chipset (this is why I think, I need this package)


Here's the detail of the included files of the package:
./
usr/
usr/share/
usr/share/man/
usr/share/man/man4/
usr/share/man/man4/intel.4.gz
usr/share/bug/
usr/share/bug/xserver-xorg-video-intel/
usr/share/doc/
usr/share/doc/xserver-xorg-video-intel/
usr/share/doc/xserver-xorg-video-intel/changelog.Debian.gz
usr/share/doc/xserver-xorg-video-intel/copyright
usr/share/doc/xserver-xorg-video-intel/README.gz
usr/lib/
usr/lib/libIntelXvMC.so.1.0.0
usr/lib/libI810XvMC.so.1.0.0
usr/lib/xorg/
usr/lib/xorg/modules/
usr/lib/xorg/modules/drivers/
usr/lib/xorg/modules/drivers/ch7xxx.so
usr/lib/xorg/modules/drivers/ivch.so
usr/lib/xorg/modules/drivers/ch7017.so
usr/lib/xorg/modules/drivers/intel_drv.so
usr/lib/xorg/modules/drivers/tfp410.so
usr/lib/xorg/modules/drivers/sil164.so
usr/share/man/man4/i810.4.gz
usr/share/bug/xserver-xorg-video-intel/script
usr/lib/libI810XvMC.so.1
usr/lib/libIntelXvMC.so
usr/lib/libIntelXvMC.so.1
usr/lib/libI810XvMC.so
usr/lib/xorg/modules/drivers/i810_drv.so

I do hope that there is someone out there who can help me. Thanks!!!

---

### Post by dcstar on 2008-11-17
> **volaer said:**
> Guys, I have downloaded a driver that I need for my laptop (by searching through the net). It is a debian package that contain all these:
..........
However, everytime I double click the debian package ,to install it, an error will appear that says:

**Error: Conflicts with the installed package 'xserver-xorg-viedo-i810'**

How can I solve this? And how can I install the package?
.........

Remove the conflicting package.

---

### Post by volaer on 2008-11-17
How can I remove the conflicting package???

---

### Post by bigbrovar on 2008-11-17
open **synaptic** and on the side panel select **custom filters** and choose **broken packages**. u will then see the affected package marked in red. right click and remove it. btw its always not a good thing to install vital applications like graphic drivers from outside the repository. bad things can happen

---

### Post by volaer on 2008-11-17
Really??? Well, to be honest it is because I am having some problems in playing video files... my Laptop Hang freezes whenever i play video files including audio visualization,

---

### Post by bigbrovar on 2008-11-17
> **volaer said:**
> Really??? Well, to be honest it is because I am having some problems in playing video files... my Laptop Hang freezes whenever i play video files including audio visualization,
hmm i use the intel's intergrated x3100 cards and everything works quite fine. are you sure its a graphic card issue? in any case am sure with time the updated graphic driver would make it to the repos.

---

### Post by volaer on 2008-11-17
No I am not sure... but so far, I really don't see anything wrong with my ubuntu except for the freezing of my video files. Is there any other reason why it happens?

---

### Post by bigbrovar on 2008-11-17
hmm i wouldnt know .. could be anything
can u describe what happens exactly .. and it might help to check your syslogs for errors

---

### Post by volaer on 2008-11-17
Ok, here's the thing, everything works fine in all my other software programs. But everytime i play video files like avi, divx, mpeg, etc and the like, including the playing of my music files and then uses visualization, all my programs that are running will freeze up, meaning you cannot do anything to them. It hangs up. THe only thing that remains moving is my mouse cursor. Aside from that, nothing more. Even my DVD rom will stop playing the DVD or CD that I inserted. 

I am sure that it is not due to my DVD rom because it works fine even when I play audio cd (of course without using the visualization). 

So that is my main problem. Please note that I don't have any problem in watching online movies that is being played using flash players by websites. But if it becomes my own file, then the problem starts to pop up. 

Any idea what's wrong? By the way thanks for your prompt replies. I really appreciate it.:)

---

### Post by bigbrovar on 2008-11-17
i did some search and i found that it seems to be a bug ... with intel and compiz .. [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/243282](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/243282) the work around there says you should turn off compiz (desktop effect) and try to see if the same problem happens... am still working on a solution that wont require you to do this .. since compiz is the icing on the cake for linux.

---

### Post by volaer on 2008-11-17
Ok... I will turn it off and see what happens. ANd then if you found something better to fix this annoying bug, please help me. Thanks...

---

### Post by volaer on 2008-11-17
Guess, what, I tried disabling the visual effect, and now I got another problem... It blackens out. meaning, when I play a video file, nothing will black out and nothing appears. 

Any more idea?

---

### Post by bigbrovar on 2008-11-17
on unfortunately am running out of ideas my self :( .. Am still googling ...did u try restarting the system to see if it helps.. ? sorry i couldnt be of much help :(

---

### Post by volaer on 2008-11-17
Yes I did that as well. But still nothing works.. Ok.. Thanks anyway.. Maybe I will have to report this problem as a bug. Since I've been looking for solution to this problem, but I have found nothing. 

Thank you very much bigbrovar. you have been of great help already. God bless.

---

### Post by bigbrovar on 2008-11-17
also uc an try installing this incase u dont already have it install 

**sudo apt-get install xserver-xorg-video-intel 915resolution** 

may that would help

---

### Post by volaer on 2008-11-17
Hi, just tried this but I get this message:

Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libboost-regex1.34.1 asc-data
  libsdl-sound1.2 libmikmod2 libphysfs-1.0-0 libsigc++-1.2-5c2
  linux-headers-2.6.24-19 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  915resolution
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.3kB of archives.
After this operation, 127kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe 915resolution 0.5.3-1ubuntu1 [15.3kB]
Fetched 15.3kB in 1s (7902B/s)        
Selecting previously deselected package 915resolution.
(Reading database ... 137023 files and directories currently installed.)
Unpacking 915resolution (from .../915resolution_0.5.3-1ubuntu1_i386.deb) ...
Setting up 915resolution (0.5.3-1ubuntu1) ...
[B]Wrong chipset detected. 915resolution only works with Intel 800/900 series graphic chipsets.
[/B]

My chipset is intel 4 chipset series.

---

### Post by bigbrovar on 2008-11-17
hmm then remove the 915resolution package since it says its not meant for ur graphic card .. sudo apt-get remove --purge 915resolution

---

### Post by volaer on 2008-11-17
Thanks pal, I uninstalled it.:)

---

### Post by volaer on 2008-11-17
Hey pal,

Just want you to know that somehow, it solved my problem of laptop freezing...

Someone advised me to run the gstreamer-properties. Then click the video tab, change the "Auto detect" to  "X - Windows System (No Xv)"

Though the setting is completely functioning and it is really playing my movies but in lower quality, at least it does not hang up. But still inquiring if this is purely a driver problem.:)

Thanks again for staying and looking for answers with me.:) God bless.

---

### Post by bigbrovar on 2008-11-18
hey glad you finally found a solution that worked somehow. u could try changing the values of the gstreamer-properties thingie to see if it improves things .. cheers and god bless you too.

---

### Post by volaer on 2008-11-18
well, it is not really the final solution. It still lies with the driver. As you said, it is some sort of a bug issue. The video is not at its best, but still far better than freezing. Somehow, I can now watch my own video files as long as I use totem.:) 

But of course, it is still Cheers...:)) Thanks again!!!

---

