---
title: "Radeon HD 6770"
date: 2012-04-12
forum: Hardware
---

### Post by Gannin on 2012-04-12
It's time to upgrade my graphics card.  I've been using nVidia for as long as I've been using Linux, but I saw an article on Phoronix lately that showed the ATI / AMD cards giving better OpenGL performance than nVidia.  So, I'm thinking about upgrading to a Radeon HD 6770 card.

My question is, when going from using nVidia cards in Linux to using ATI / AMD cards in Linux for the first time, is there anything I need to watch out for?

I always download and install the nVidia drivers from the nVidia website manually.  Is manually installing the ATI / AMD drivers just as easy?  Does the ATI / AMD installer automatically update the xorg.conf file like the nVidia installer does?

---

### Post by ronaldbrijo on 2012-04-12
I have an AMD card, and installing the driver (Ubuntu 11.10) is always easy, just go to the Proprietary Drivers gui and activate the driver. Ubuntu automatically downloads and installs the driver 1st time.

---

### Post by Redblade20XX on 2012-04-12
Just follow this wiki : [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)  ;)

-Red

---

### Post by ronaldbrijo on 2012-04-12
To add to my earlier post...

U will also get the Catalyst Control Centre installed. This allows you to customise your graphics to suit your system... Works identical to the windows version!!

---

### Post by Gannin on 2012-04-12
> **ronaldbrijo said:**
> I have an AMD card, and installing the driver (Ubuntu 11.10) is always easy, just go to the Proprietary Drivers gui and activate the driver. Ubuntu automatically downloads and installs the driver 1st time.

I appreciate the reply.

With my current nVidia card, I prefer manually installing the driver from the nVidia website, and that's also how I'll be doing it with the AMD driver.  I prefer doing that over using the Proprietary Drivers tool, just to make sure I have the latest version when I want it.

I've seen some videos of the AMD driver installation and it looks pretty simple and it looks like you can actually do it while you're still running the X server, which you can't do with the nVidia driver manual installation.

I was just asking if maybe there was some extra information that I should be aware of ahead of time :).  Again, thanks for the reply.

---

### Post by ronaldbrijo on 2012-04-12
Ive personally struggled to do the manual install. I've found the AMD driver is not packaged in a way to easily install.

---

### Post by Gannin on 2012-04-12
As I understand it, to do the manual install, you just download the .run file, set it to executable, then run it and go through the installation gui.  Just like the nVidia manual install except it uses an actual gui instead of a text-mode gui.

---

### Post by ratcheer on 2012-04-12
I have found that the best way to install the driver from the AMD site is to create .deb packages from it and then install them with dpkg. The instructions are given in the link [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

I have the same card (6770), btw. It works very well.

Tim

---

### Post by SeijiSensei on 2012-04-12
How well do the Radeon's support HD video?  With NVIDIA's VDPAU interface, even machines with slow CPUs can offload H.264 decoding to the video card and smoothly display 720p or 1080p content.  Is there an equivalent interface for ATI cards?  I've heard about VAAPI, but I don't know if it's as well supported as VDPAU.

Of course if the OP has a recent machine with a multi-core processor, this isn't an issue.

---

### Post by Gannin on 2012-04-12
> **ratcheer said:**
> I have found that the best way to install the driver from the AMD site is to create .deb packages from it and then install them with dpkg. The instructions are given in the link [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

I have the same card (6770), btw. It works very well.

Tim

What would you say the main advantage of creating and installing the .deb packages is over their normal automatic install?

---

### Post by Claus7 on 2012-04-12
Hello,

first of...

[LIST=1]
[*]the driver now is called fglrx, which is included in the so called Catalyst package or ccc (which stands for catalyst control center)
[*]you can install the latest and gratest from amd website (a new release appears almost every month or so)
[*]you have to **uninstall** the previous drivers, **before** you decide to move on and install the next release
[*]I have done it in desktop many times, so I think that the same will be in laptops as well, so you won't face many problems (I guess)
[*]how you can do it? Like this:
[http://ubuntuforums.org/showpost.php?p=11320620&postcount=30](http://ubuntuforums.org/showpost.php?p=11320620&postcount=30)
(xorg file provided there, might not needed from you)
[*]you do not have to 'shut down' your desktop environment, as in nvidia, while installing the driver
[*]you have to restart after the installation though
[*]while you are issuing the commands you will install some deb files that you have created, which you can safely erase in the end
[*]the procedure can be accomplished easily by terminal, if you issue the commands slightly differently than mentioned in the link provided, you (might) get a graphical environment as well
[*]more or less these would suffice I guess...
[/LIST]

Good luck to your new adventure,
Regards!

---

### Post by ratcheer on 2012-04-12
> **Gannin said:**
> What would you say the main advantage of creating and installing the .deb packages is over their normal automatic install?

The ability to easily uninstall them, and the fact that the package manager knows about them.

Tim

---

### Post by QIII on 2012-04-12
Install from the repo and do 

```
sudo aticonfig --initial
```

Before you shut down.

ATI supports H.264 and hardware acceleration on Linux, despite rumors to the contrary.  You just have to add a couple more packages from the repos.

Can't remember off hand (I'm on my cell riding the train home from work), but I'll try to remember to edit this post with the four additional packages required.

---

### Post by QIII on 2012-04-12
> **SeijiSensei said:**
> How well do the Radeon's support HD video?  With NVIDIA's VDPAU interface, even machines with slow CPUs can offload H.264 decoding to the video card and smoothly display 720p or 1080p content.  Is there an equivalent interface for ATI cards?  I've heard about VAAPI, but I don't know if it's as well supported as VDPAU.

Of course if the OP has a recent machine with a multi-core processor, this isn't an issue.

It works very well.  I use XBMC with VAAPI (XvBA backend) enabled.

---

### Post by Gannin on 2012-04-12
> **QIII said:**
> Install from the repo and do 

```
sudo aticonfig --initial
```

Before you shut down.

ATI supports H.264 and hardware acceleration on Linux, despite rumors to the contrary.  You just have to add a couple more packages from the repos.

Can't remember off hand (I'm on my cell riding the train home from work), but I'll try to remember to edit this post with the four additional packages required.

I haven't heard of using that command before.  What does it do?  And what happens if you don't use it before restarting?

---

### Post by QIII on 2012-04-12
It generates a basic xorg.conf (a configuration file) which the driver needs but does not exist by default.

Problems can range from difficult screen issues to complete inability to load your DE.

---

### Post by QIII on 2012-04-12
After installing the driver, add these from the repositories:

vainfo, xvba-va-driver, libva-egl1, libva-glx1

In the terminal, type 

```
vainfo
```and you should get something like this back if everything is working:

```
$ vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

```

That will indicate that you are getting hardware acceleration.

---

### Post by iowabeakster on 2012-04-12
Excellent info guys. I too have had some difficulties with the ATI driver install.  I spent a number of hours reading up and finding instructions on doing this.  

I am nearly in the same boat as OP.  I have been manually installing my proprietary driver from Nvidia on my desktop PC for a while, so I am used to doing that.  Ya know...Shut down X server... sh the Nvidia.run file... reboot.

My wife just got a new laptop (asus B43), and it has an ATI (6470 though) and I have installed Ubuntu (12.04) on it.

I've been through two of the methods mentioned above (1.  from repositories 2. download and run the install script from ATI).  No problems in the installation.  Ran the: aticonfig --initial -f... and reboot.

On reboot, I get stuck in low graphics mode (actually fail safe graphics don't work either.. ha ha).  So I drop to root command line and remove the xorg.conf file to get any sort of anything working again (restore to default driver).   This is where I am currently... my patience wore thin.  I'll try to get it working again sometime soon.

 So if you are like me... note the location of the Xorg.conf file created by the: aticonfig --initial -f command.  Remove it and you can get default graphics driver working again if you need.

---

### Post by Gannin on 2012-04-12
> **QIII said:**
> It generates a basic xorg.conf (a configuration file) which the driver needs but does not exist by default.

Problems can range from difficult screen issues to complete inability to load your DE.

That's strange... I talked to some others that used the automatic install file and they said it automatically updated their xorg.conf for them.

---

### Post by 3Miro on 2012-04-12
First: as already mentioned, you need to uninstall the Nvidia driver **before** you remove the Nvidia card and boot the machine with the ATI card.

Second: if you have a desktop and all that you do is work, the default ADM drivers work just fine. In fact, I wouldn't bother with the proprietary ones. For power consumption and wine games, you do need the prop driver. Note that for wine games, Nvidia is still better.

Third: if you install the proprietary drivers, I would recommend using the "additional drivers" tool as it is the recommended default method. Manual installation works too, but it is more work, you are doing the work, so do what you want.

Fourth: the issues with 12.04 could be due to the release being still in Beta. I would try the stable 11.10 first or wait for the final release of 12.04. Also, you can start another thread and/or report a bug.

---

### Post by Gannin on 2012-04-13
Actually, as I've been looking at things and doing more research, I think I might upgrade to a 6850 card instead of a 6770 card.  The 6850 card seems to have a good little bump in performance for not much more money.

For instance on PassMark, the 6770 card has a score of 1749, whereas the 6850 has a score of 2751.  I also saw some other benchmarks showing the 6850 to have a higher framerate than the 6770.

My current card only has a PassMark score of 349, so to me, the 6770 would seem fantastic and the 6850 amazing :).

---

