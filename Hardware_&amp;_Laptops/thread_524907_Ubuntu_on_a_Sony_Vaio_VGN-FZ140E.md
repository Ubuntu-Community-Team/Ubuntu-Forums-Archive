---
title: "Ubuntu on a Sony Vaio VGN-FZ140E"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by dyous87 on 2007-08-13
Hello everyone

I have recently purchased a new Sony Vaio VGN-FZ140E to replace my older Acer Aspire 5672wlmi.

Its specs are as follows:
[LIST]
[*]Intel Core 2 Duo 1.8gigs
[*]200 gig SATA HDD
[*]2 Gigs of RAM
[*]Intel GMA x3100
[*]Intel Wireless 4965 AGN[/LIST]I immediately began working on getting Ubuntu installed on it.  Trust me Windows Vista is no fun to use especially with the Intel Core 2 Duo and 2 gigs of RAM.

I was unsuccessful getting Ubuntu 7.04 to boot with the Live CD as it kept giving me this message:

```

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) help

```

No matter though, I simply tired again using the Ubuntu 7.04 Alternative CD. The installation seemed to all go smoothly and upon restart I was finally greeted with the Ubuntu login screen. The resolution was off so I did:

> sudo dpkg-reconfigure xserver-xorg

I had to select the 'vesa' drivers since the new Intel Drivers for the x3100 are not available through Feisty yet. Going through the configuration utility I was able to choose the monitor's native 1280x800 resolution and when I restarted X it was running at that resolution. 

The resolution is right all though the computer runs a bit sluggish most likely duo to the incorrect graphics drivers. 

I also noticed that the cd-rom drive does not work. When i tried opening up a CD-ROM 1 through places>computer it gave me the error message:

```
mount: special device /dev/hda does not exist.
```

From the terminal I ran:

```
sudo mknod /dev/hda b 3 0
```
 
and after that the cd-rom worked all though that command has to be run everytime the computer is restarted so I just added it to /etc/rc.local.

> sudo gedit /etc/rc.local

I have not tried the cd/dvd burner yet but I believe they are working because after I put in that command, CD-RW/DVD+-RW Drive showed up under computer. 

Now a big problem I was having is getting the wireless to work. The new Intel Wireless 4965agn card is not yet supported by Feisty so I tried following this guide to backport it from Gutsy. 

[http://ubuntuforums.org/showthread.php?t=493095&highlight=intel+4965agn](http://ubuntuforums.org/showthread.php?t=493095&highlight=intel+4965agn)

I followed all the steps and successfully complied the drivers multiple times and on multiple fresh installs but I was unable to get connection after modprobing them. It would either freeze my computer or pick up my wireless network, connect and yet still leave me with no connection.

I even tried installing Gutsy hoping that it would bet better supported and while it now automatically detected my Intel GMA x3100 I still had no wireless and even worse now I had no sound.

I finally reinstalled Feisty Fawn and decided to attempt using ndiswrapper. 

I was successfully able to get my wireless working with ndiswrapper following this guide:

[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty)

After that I just added 
```
sudo modprobe ndiswrapper
```
to my /etc/rc.local.
> sudo gedit /etc/rc.local
in order to make ndiswrapper load on startup.

OK so as of now I have Ubuntu 7.04 installed and wireless running :).

I am going to list what works and what does not work.

What works:
[LIST]
[*]Intel Core 2 Duo ( Ubuntu recognized my dual processors out of the box.)
[*]Sound (Works out of the box)
[*]Native 1280x800 resolution. (Using Vesa drivers)
[*]Wireless (Using ndiswrapper. Follow directions from link above)[/LIST]
What doesn't work:
[LIST]
[*]Intel GMA x3100 accelerated graphics (Drivers not supported by Feisty)
[*]Sony Motioneye web cam
[*]SD Card Reader[/LIST]I am going to be posting my progress as I figure out how to get more things working.

If anyone has this same laptop and wants to contribute to this thread I would really appreciate it.

I hope this thread helps anyone out there who has a Sony Vaio VGN-FZ140E and would like to install Ubuntu on it.

---

### Post by dyous87 on 2007-08-13
It appears that upgrading to the linux kernel 2.6.20-16 will crash your system upon start up. I have reverted back to 2.6.20-15 and everything is working well.

---

### Post by dyous87 on 2007-08-14
I forgot that /dev/hda has to be mounted on startup for the cd drive to auto detect cds therefore I added:

```
mount /dev/hda
```

to the end of my /etc/rc.local file.

It should now look like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo mknod /dev/hda b 3 0

sudo modprobe ndiswrapper 

mount /dev/hda

exit 0
```

---

### Post by dyous87 on 2007-08-15
Is there anyone else out there trying to run this laptop with Ubuntu, or anyone who has been successful getting the x3100 Intel drivers working. No matter what I do I haven't been able to get them to work and I would really like to have accelerated graphics on this.

---

### Post by willynasa on 2007-08-16
Thanks for this thread man, I just got a similar laptop and I will try to follow your guide to install Feisty on it. I'll kep you posted if I can find a fix for the things that don't work. =D>

---

### Post by dyous87 on 2007-08-16
excellent, I hope it helps, good luck and keep me posted.

by the way what laptop do you have if you don't mind me asking?

---

### Post by qfb_ros on 2007-08-18
Hello! I have a Sony Vaio CR160F and also struggling with the 4965AGN wireless card.  I got the video card running nice and smooth using this post:  [http://ubuntuforums.org/showthread.php?t=506744](http://ubuntuforums.org/showthread.php?t=506744)

I will try to use ndiswrapper to get my card working and post my progress.  Good luck!  :)

---

### Post by qfb_ros on 2007-08-18
Woohoo! I got working 4965AGN wifi card on the VAIO CR160F using ndiswrapper.  I had to fresh install Feisty Fawn and also had an "Invalid Driver" message.  Followed this instructions and all went well:  [http://ubuntuforums.org/archive/index.php/t-471794.html](http://ubuntuforums.org/archive/index.php/t-471794.html)

Ubuntu for life!

---

### Post by dyous87 on 2007-09-28
I am now trying to get Gutsy Gibbon Beta installed on this machine after all this time having been unable to get the graphics drivers working with Feisty. Hopefully at this point the wireless will now work with Gutsy Gibbin...i hope.

---

### Post by dyous87 on 2007-09-28
Well, I've installed the newest version of Gitsy Gibbon and wireless and well as accelerated graphics with the intel drivers are both working now! I'll post more on this once i play around a bit.

---

### Post by mayhemt on 2007-10-05
sweet, worked like a charm for wireless... th anks

---

### Post by poamj on 2007-10-09
I own the same notebook. I've tried to use Gutsy, but the installation cd crashes during startup :( Which CD did you download ? Desktop or Alternate ?

---

### Post by dyous87 on 2007-10-09
You need to use the alternative cd. If i was you I would follow by how to on getting it to run with fiesty fawn because in gutsy the wireless is nothing to be desired with horridly slow speeds.

---

### Post by poamj on 2007-10-09
humm.. thanks. I will try both and see which works best :)

---

### Post by dyous87 on 2007-10-09
No problem, let me know if you need any help :)

---

### Post by guido_damico on 2007-10-10
Hey dyous87: great post indeed!

I have only a [newbe] question, when you say:

> **dyous87 said:**
> Hello everyone
[...]
[LIST]
Intel Core 2 Duo ( Ubuntu recognized my dual processors out of the box.)
[/LIST]
[...]


How did you access that ubuntu recognized the dual processor?

I see that the /etc/cpuinfo reports two cpus, but on the other side the system monitor and top only show one, so am not sure how the OS uses it...

I used the amd64 version of feisty.

Thanks, ...and congrats for the choice of laptop! :D

Guido

---

### Post by guido_damico on 2007-10-10
Correction: the system monitor does show two CPUs (they were the same color and I missed it--duh!), still "top"shows only one, so I guess now I have only to find out why, but I am mor confident that I'm fully using the CPUs.

Guido

---

### Post by Projectshifter on 2007-10-18
I'm so glad that I'm not the only one who has struggled with this damn thing.  I've always heard good things about Vaios being reliable, so I bought one to replace my old Compaq (that worked surprisingly well out of the box with Linux).  I just put the final version of Gutsy Gibbon Desktop CD in, it finally boots up, bit it says it's at 640x480, and it only shows in the top 1/4th of my screen!  THe damn thing splits, top left is the desktop, top right is black, bottom left keeps changing with crazy colors anytime I do something, and the bottom right is just gray and weird.  I gave up months ago when Fiesty didn't work at all with any of my wireless and/or video ****, so hopefully this will work!

---

### Post by dyous87 on 2007-10-18
Actually I was able to get fiesty working well. I posted the howto on this thread. I have not tried the final release of Gutsy yet but last I tried when tribe 4 or 5 was released everything was pretty much working well except wireless which worked but it did not show the wifi light and it was painfully slow. The graphics should work right out of the box though.

---

### Post by dyous87 on 2007-11-02
Has anyone be successful in running 7.10 on this machine yet. I am currently attempting to upgrade it now. I am doing a fresh install. I will post how it goes. Wish me luck :)


David

---

### Post by poamj on 2007-11-08
I managed to get Gutsy running on my fz140e.
I've compiled the most recent stable kernel (2.6.23.1), following the procedure found on [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) . Now hibernation and suspend are working ok.

** When you compile a new kernel, the wireless card will stop working. You need to recompile the drivers ([http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/))

Remember to enable and load sonypi and sony-laptop modules. My fn keys are now recognized (i can see the keycode when i run xev), after following the procedure on [http://www.linux.it/~malattia/wiki/index.php/Sony-laptop](http://www.linux.it/~malattia/wiki/index.php/Sony-laptop). I am now trying to figure out how to map fn keys events to the laptop functions (like changing brightness, for example).

I've also compiled the most recent ALSA drivers, follow the procedure from [http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147) and adding the line
options snd-hda-intel model=vaio position_fix=0
to /etc/modprobe.d/sound , i got speakers, headphones and mic working perfectly.

I also managed to get webcam working by compiling Ricoh driver ([http://www.uuhaus.de/linux/r5u870-0.10.0.tgz](http://www.uuhaus.de/linux/r5u870-0.10.0.tgz)) with the following patch 
[http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch](http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch)

I didn't have time to test other things yet. Let me know if you have some problem.


> **dyous87 said:**
> Has anyone be successful in running 7.10 on this machine yet. I am currently attempting to upgrade it now. I am doing a fresh install. I will post how it goes. Wish me luck :)


David

---

### Post by guido_damico on 2007-11-22
> **poamj said:**
> I managed to get Gutsy running on my fz140e.
I've compiled the most recent stable kernel (2.6.23.1), following the procedure found on [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) . Now hibernation and suspend are working ok.

    I am not sure if you did this in order to run the latest or if you had specific issues you were trying to overcome, but just for documentation purposes: for 7.10 this is what I found:
[LIST=1]
[*] The only piece of hardware not recognized is the webcam,the rest works fine.
[*] Wireless working, except the "wlan" light.
[*] Hibernate works but requires the network to be restarted after waking up (might be my misconfiguration).
[/LIST]

> **poamj said:**
> I also managed to get webcam working by compiling Ricoh driver ([http://www.uuhaus.de/linux/r5u870-0.10.0.tgz](http://www.uuhaus.de/linux/r5u870-0.10.0.tgz)) with the following patch 
[http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch](http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch)

I didn't have time to test other things yet. Let me know if you have some problem.
    Could you spend a little more on giuding a newbee to do the same? Just instalin those drivers will lead the webcam to be recognized and usable?

    Thanks!
        Guido

---

### Post by mohit.khanna on 2007-11-22
> **poamj said:**
> I managed to get Gutsy running on my fz140e.
I've compiled the most recent stable kernel (2.6.23.1), following the procedure found on [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) . Now hibernation and suspend are working ok.

** When you compile a new kernel, the wireless card will stop working. You need to recompile the drivers ([http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/))

Remember to enable and load sonypi and sony-laptop modules. My fn keys are now recognized (i can see the keycode when i run xev), after following the procedure on [http://www.linux.it/~malattia/wiki/index.php/Sony-laptop](http://www.linux.it/~malattia/wiki/index.php/Sony-laptop). I am now trying to figure out how to map fn keys events to the laptop functions (like changing brightness, for example).

I've also compiled the most recent ALSA drivers, follow the procedure from [http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147) and adding the line
options snd-hda-intel model=vaio position_fix=0
to /etc/modprobe.d/sound , i got speakers, headphones and mic working perfectly.

I also managed to get webcam working by compiling Ricoh driver ([http://www.uuhaus.de/linux/r5u870-0.10.0.tgz](http://www.uuhaus.de/linux/r5u870-0.10.0.tgz)) with the following patch 
[http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch](http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch)

I didn't have time to test other things yet. Let me know if you have some problem.
I tried do it...but was unable to get my cam working....can u please elucidate..or help me find out whats the problem..
And is there any specific application with which the cam works..I tried it with MSN and SKYPE...it doesnt seem to be working...
MSN messenger gives me this error.
can't read "brightness": no such variable
    while executing
"::Capture::SetBrightness $grabber $brightness"
    (procedure "setPic" line 31)
    invoked from within
"setPic $::CAMGUI::webcam_preview"
    (procedure "::AVAssistant::StartPreviewLinux" line 52)
    invoked from within
"::AVAssistant::StartPreviewLinux .assistant1.bodyf.contentf.left.chans {Camera 1}"
    ("after" script)

---

### Post by poamj on 2007-12-07
I don't remember doing anything special to get my webcam working.
I just compiled the driver (after applying the patch modifications) and then, loaded the driver.
I think i've just runned the following commands:
make
make install
modprobe r5u870

By the way... I've tested it with xawtv and amsn and it is working.

---

### Post by drobles on 2007-12-11
It worked!

Thanks guys

---

### Post by steenbras on 2008-01-16
I found that it worked on my VGN-FE48G by just doing the following:
1. Downloaded the tar.gz file mentioned above to a work directory (~/webcam which I created)
2. extracted it using tar -xvf r5u870-0.10.0.tgz
3. cd into the created /r5u870-0.10.0 directory
4. sudo make install
5. sudo modprobe r5u870

This worked for me - no need to patch.

---

### Post by Jalsemgeest on 2008-01-27
> **guido_damico said:**
> I am not sure if you did this in order to run the latest or if you had specific issues you were trying to overcome, but just for documentation purposes: for 7.10 this is what I found:
[LIST=1]
[*] The only piece of hardware not recognized is the webcam,the rest works fine.
[*] Wireless working, except the "wlan" light.
[*] Hibernate works but requires the network to be restarted after waking up (might be my misconfiguration).
[/LIST]


    Could you spend a little more on giuding a newbee to do the same? Just instalin those drivers will lead the webcam to be recognized and usable?

    Thanks!
        Guido

Hey, I dont know what to do if i want to get my webcam working, i downloaded the correct stuff, although i dont know what to do with it.
thanks, Jalsemgeest

---

### Post by Jalsemgeest on 2008-01-27
Hey, could anyone help me? I would obviously like everything to work, but i know thats a lot of work.  I have a Sonvy Vaio VGN-FZ140E.  I put XP onto it and i installed some drivers i could find, i have the wireless working, the video card and sound card although my headphone port works but the sound comes out of the speakers at the same time.

If anyone has any idea of how to get the following working please please help: _Webcam_, _The Touchpad scroll down-up thing_ _SD, PRQ card slot_, _fn keys_, and _the sound problem with the headphones_.

Note: I am sort of a new person to doing this sorta stuff so please explain thouroughly.

Thanks,
Jalsemgeest

---

### Post by josemanuel on 2008-02-10
[QUOTE=poamj;3909113]I don't remember doing anything special to get my webcam working.
I just compiled the driver (after applying the patch modifications) and then, loaded the driver.
I think i've just runned the following commands:
make
make install
modprobe r5u870


 Hello, I just followed the above instructions and the webcam is working with skype. No need to re-patch. Cheers

---

### Post by Nighunter on 2008-03-22
Hey guy's thanks you for the wonderfull topic. I have a question i am running Kubuntu 7.10 ,and i have a problem running the web cam.
Please tell me how to apply the patch for Richo web cam.

---

### Post by poamj on 2008-04-04
> **Nighunter said:**
> Hey guy's thanks you for the wonderfull topic. I have a question i am running Kubuntu 7.10 ,and i have a problem running the web cam.
Please tell me how to apply the patch for Richo web cam.

You don't need to apply the patch anymore. Just download the version 0.11.0 of the driver and it will work.

[http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)

I download the source code, unpacked, executed:
make
make install
modprobe r5u870
and it works! (I've tested the webcam on Skype).

I didn't test the ubuntu package for this driver. I don't know if it works.

I'm running hardy. kernel 2.6.24-14-generic

Pedro Matos Jr.

---

### Post by poamj on 2008-04-04
I've managed to get my FN keys working by writing a new keymap quirk for hal.

I have submited this patch to the hal development list:
[http://lists.freedesktop.org/archives/hal/2008-March/011321.html](http://lists.freedesktop.org/archives/hal/2008-March/011321.html)

It has already been commited to hal-info's source tree and will be available on the next hal-info release. Thus, in future releases of ubuntu, the FN keys should "just work" for everybody with this laptop model.

---

### Post by Nighunter on 2008-04-25
Thank you poamj, it works like a charm.
Some times when i open skype and do the camera test the image is upside down , do you have the same problem.

And another question. When i upgrade from 7.10 to 8.04 my headphone doesn't work. Do you know how to fix it.

Thanks, Best Wishes
Alex

---

### Post by poamj on 2008-04-26
> **Nighunter said:**
> Thank you poamj, it works like a charm.
Some times when i open skype and do the camera test the image is upside down , do you have the same problem.

And another question. When i upgrade from 7.10 to 8.04 my headphone doesn't work. Do you know how to fix it.

Thanks, Best Wishes
Alex

Hi Alex,

I don't have upside down image problem with skype. Have you updated your kernel to a new version ? Remember that the driver is compiled against a specific kernel, so every time your kernel is updated, reboot with the new installed kernel, go to the directory where the source for the drivers are and run the commands:
make clean
make
make install
modprobe r5u870

For your headphone, open the file "/etc/modprobe.d/alsa-base" (sudo gedit /etc/modprobe.d/alsa-base) and check if there is a line with:
options snd-hda-intel model=vaio position_fix=0
If you can't find it, add it to end of the file, save and restart alsa or reboot.
Tell me if it works. 

bests,

Pedro

---

### Post by Nighunter on 2008-05-15
HI poamj.
I have just install fresh copy of Kubuntu 8.04 KDE3
and i still have the same problem with my camera. The image is show upsidedown.
The good news is my headphone works

Do you have any idea how to solve this problem

Best wishes
Alex

---

### Post by brgirgis on 2008-06-13
The new Ubuntu 8.04 works pretty much out of the box. Main screen, wireless, and dvd drive are working. I installed this version using the alternative cd. I don't know whether the regular version would work or not.

The webcam is installed on system setup, but you need to follow the above mentioned procedure to get it working correctly. Also the headphone jack was not working, but after adding the above line, it works fine. The built in mic was not working, I followed these steps to get it working (found them in another thread):

open volume control
edit preferences
select all of them and close
in Recording tab unclick no microphone and raise volume
in Switches click Internal Mic

Didn't test the card reader, S Video, mic jack, output monitor.

Cheers!!! Finally I got this laptop working at leat 90% on linux!!! WE MADE IT GUYS!!!

---

