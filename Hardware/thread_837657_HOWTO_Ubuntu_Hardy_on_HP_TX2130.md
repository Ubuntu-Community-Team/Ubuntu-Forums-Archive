---
title: "HOWTO: Ubuntu Hardy on HP TX2130"
date: 2008-06-22
forum: Hardware
---

### Post by siennalizard on 2008-06-22
Hello all.

This is a very scratchy and brief attempt to help people along with this laptop series: I just bought myself the tx2130. First, what doesn't work. If you've got answers to any of this, please do comment.

[SIZE=3]Not working at present[/SIZE]
[LIST]
[*]Screen rotation with xrandr
[/LIST]

[SIZE=3]Sort of working[/SIZE]
[LIST]
[*]Fingerprint scanner (AuthenTec AES1610) - can be demo'ed as root, but PAM module not very useful in current, basic state
[/LIST]

[SIZE=3]We* made these work (see below)[/SIZE]
[LIST]
[*]Wireless card (Broadcom BCM4328 802.11a/b/g/n)
[*]Sound (nVidia MCP51 High Definition Audio HDA)
[*]3D graphics acceleration (nVidia C51 Geforce 6150 Go)
[*]Suspend
[*]Lightscribe labeller DVD drive
[/LIST]

[SIZE="3"]Untested[/SIZE]
[LIST]
[*]Expansion Port 3
[*]S-video (TV out)
[/LIST]

[SIZE="3"]Everything else[/SIZE]
[LIST]
[*]If I haven't mentioned it, it worked out of the box. A few notables:
[*]Remote control (Philips R6) - seems to work with the hardware, with no need for drivers
[*]Webcam - for some programs like Skype, seems to work out of the box. Not everything though (camorama fails, for example).
[/LIST]

This is how we* sorted some of the problems:
[SIZE=3]Wireless card (Broadcom BCM4328 802.11a/b/g/n)[/SIZE]
Use ndiswrapper. Follow these steps (from [http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html](http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html))
```
wget http://ftp.us.dell.com/network/R151517.EXE
mkdir driver
unzip -a R151517.EXE -d driver/
cd driver/DRIVER/
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```If that works, try adding 'ndiswrapper' to the /etc/modules file. Then it should load up at boot time. NOTE Not tested with WPA, yet. YMMV.

[SIZE=3]Sound (nVidia MCP51 High Definition Audio HDA)[/SIZE]

Shouldn't have taken as long as it did. Create a file called /etc/modprobe.d/sound and put this in it:
```
options snd-hda-intel model=hp
```Then reboot. You should hear the login tune.

[SIZE=3]3D graphics acceleration (nVidia C51 Geforce 6150 Go)[/SIZE]
Sadly, I cannot remember exactly what I did - lots of trial and error. One thing is for certain: you should reboot after installing all the initial updates (some 200?). It is important that you are using the correct kernel before you start the setup.

[SIZE="3"]Software Suspend[/SIZE]
You need to change two files to get this to work. Firstly, we update grub so that the computer starts with some different kernel options.
Edit /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst[CODE]
Find the line that begins "defoptions=" (around line 89) and edit it so that it looks like this:

[CODE]# defoptions=quiet splash noapic nolapic irqfixup
```

When you've finished, saved the file and exited, you need to run the update script for grub, so that it will take note of your changes next boot.
```
sudo update-grub
```

You may have found that the screen is black when the computer resumes from standby sometimes. Try this:

Edit /etc/default/acpi-support:

```
sudo gedit /etc/default/acpi-support
```

Find "POST_VIDEO=" and change it to:
```
POST_VIDEO=false
```

Now reboot and test suspend and hibernate.

[SIZE=3]Wacom tablet and touchscreen[/SIZE]
The best approach I've found is in the tutorial below. Thanks, Gali98!

> 
I have written a short tutorial on how to get the stylus and touchscreen working with a new version of linuxwacom made for Usb tablets.
This way you don't have to apply patches....
go here to see
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)
Kory


If you want to use two monitors, but only have the tablet work on the lower screen (seems sane to me), remember to add "Options ScreenNo 0" into xorg.conf in the stylus, touch and eraser sections.

I can't seem to get xrandr to work to rotate the screen, though, so you're stuck in landscape for now.

[SIZE=3]Lightscribe labeller drive[/SIZE]
These steps are good for the 32-bit version. For those of you (like me) who installed 64-bit Ubuntu, you'll have more messing about to do. Read up about the **getlibs** script.

First, install alien to convert RPM packages to Debian/Ubuntu debs:

```
sudo apt-get install alien 
```

Then fetch the lightscribe packages: first the library, then the simple labeller, then the rather better labeller developed by Lacie:
```
wget [http://download.lightscribe.com/ls/lightscribe-1.14.17.1-linux-2.6-intel.deb](http://download.lightscribe.com/ls/lightscribe-1.14.17.1-linux-2.6-intel.deb)
wget [http://download.lightscribe.com/ls/lightscribeApplications-1.10.19.1-linux-2.6-intel.deb](http://download.lightscribe.com/ls/lightscribeApplications-1.10.19.1-linux-2.6-intel.deb)
get [http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm](http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm)

```

Now for the installations:
```

sudo dpkg -i lightscribeApplications-1.10.19.1-linux-2.6-intel.deb lightscribe-1.14.17.1-linux-2.6-intel.deb
sudo alien 4L-1.0-r6.i586.rpm
```

Both packages need read access to a config file in the /etc directory, but neither install creates it. Here's what to do:

```

sudo touch /etc/lightscribe.rc
sudo chmod a+r /etc/lightscribe.rc

```

To run the Lacie program, which allows you to select and scale an image to be printed on to the disk:

```
4L-gui
```

Th simpler program which allows you only to burn text and a decorative border can be found here:
```
/opt/lightscribeApplications/SimpleLabeler/SimpleLabeler
```

Gali98 strongly recommends 4L-gui over the simpler option. Try both!


[SIZE=3]Other considerations[/SIZE]
[LIST]
[*]Load Cycle Count of hard disk seems high. I've fixed mine according to this thread: [http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327) by nicedude. I suggest you have a read, too.
[*]...
[/LIST]

If anyone has more detailed information to offer, please post and I will incorporate it.

Now, get hacking!
J.

[SIZE="3"]* Contributors so far are listed below. Many thanks, folks![/SIZE]
[LIST]
[*]gali98
[*]tempo500
[/LIST]

---

### Post by gali98 on 2008-06-23
Hey man.. Thanks for your work to help others. I have the tx2000z, but it looks like we have about the same hardware.
This thread has a lot of info about the wacom:
[http://ubuntuforums.org/showthread.php?t=708726](http://ubuntuforums.org/showthread.php?t=708726)

Basically you have to read through it all(the first post has not been updated), but people have gotten both the touch screen and the digitalizer to work in ubuntu. I have not tried it yet so I can't tell you too much about it, other than you will have to compile stuff. May Intrepid will support it out of the box.

On the sound you might try 

options snd-hda-intel model=hp

instead. My headphones work fine. In the mixer (I use Gnome Alsa Mixer) just make sure the headphones are unmuted and turned up as well as the master volume.

On the webcam All I did was go into synaptic and search uvc then installed every package that showed up. Then install cheese (it's a much less cooler photobooth but it works) or Xawtv (that is probably not the name but it is something like that) and it should pick up the video feed.


I haven't been able to get the two mics by the webcam to  work with recording, but if I have my headphones in and talk into the mics, it comes in through the headphones, so there is probably a way to get it to work.

On the video, after you first install, then install all the updates just go to restricted drivers and use the one for nvidia.
You can also just install the package nvidia-glx-new (or it may be nvidia-new-glx) and that will also work. Then you just reboot and it should work.

I think most of the buttons an the remote come across as keyboard events which is good. Most of the buttons on the laptop (i.e. dvd and the buttons around it) work, but a few of them are hardcoded and will need a driver written for them... What a pain.

On thing you did forget to mention is suspend. Basically it doesn't work. Also if you put the laptop to sleep it will lock up and you have to turn it off and listen to that scary sound.

I hope this helped. Try it out and add to your post. I would love to help some more. Just post and I will look. Thanks,
Kory

---

### Post by siennalizard on 2008-06-23
Hi Kory,

thanks for your help on this. It's great of you to contribute.

I tried the Wacom steps but no luck: tested every way, but it seems that the event handle under /dev does not appear for me, so there's no way that it's going to work in Xorg.

Had a look through Synaptic, but could only see one "uvc" package. Could you post up your sources.list so I can work out from which repo you got them?

Suspend seems erratic. I'll look for some fixes tomorrow, hopefully.

Cheers for your help!
J.

---

### Post by siennalizard on 2008-06-23
Hi Kory,

thanks for your help on this. It's great of you to contribute.

I tried the Wacom steps but no luck: tested every way, but it seems that the event handle under /dev does not appear for me, so there's no way that it's going to work in Xorg.

Had a look through Synaptic, but could only see one "uvc" package: luvcview, which produced a similar error to other viewers I've tried:

```

james@opal:~$ luvcview 
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 22.
 Init v4L2 failed !! exit fatal 

```

Could you post up your sources.list so I can work out from which repo you got your working uvc packages?

Suspend seems erratic. I'll look for some fixes tomorrow, hopefully.

Cheers for your help!
J.

---

### Post by gali98 on 2008-06-24
Hey I'm glad your doing this. The tutorial in the link I posted is kinda spread out and hard to follow. It will be nice to have a solid post to work with. At this moment I'm at work and don't have access to my computer. I think I may have had to download an extra package for the webcam now that I think about it. I will post hopefully later today with more info. Thanks again for your hard work.
Kory

---

### Post by gali98 on 2008-06-24
Okay so here are all the packages I have related to webcams:

cheese
luvcview
webcam
webcamd

(the last two I don't think you need)

And that got it working. I don't know what else to tell you.... Make sure nvidia-glx-new is installed. I tried the same program you posted in the code, and I got the same error. 
When I used Multimedia Systems selector (it is hidden in System->Preferences you have to right click on System and do Edit Menus.)
It worked.
Cheese Worked.
XawTV worked.
Hope it works for You now.

We both forgot Lightscribe :confused:

Short Tutorial:

```
sudo apt-get install alien 
```(an rpm->deb thingie)

```
wget [http://download.lightscribe.com/ls/lightscribeApplications-1.10.19.1-linux-2.6-intel.deb](http://download.lightscribe.com/ls/lightscribeApplications-1.10.19.1-linux-2.6-intel.deb)

wget [http://download.lightscribe.com/ls/lightscribe-1.14.17.1-linux-2.6-intel.deb](http://download.lightscribe.com/ls/lightscribe-1.14.17.1-linux-2.6-intel.deb)

wget [http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm](http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm)

sudo dpkg -i lightscribeApplications-1.10.19.1-linux-2.6-intel.deb.deb lightscribe-1.14.17.1-linux-2.6-intel.deb

sudo alien 4L-1.0-r6.i586.rpm
```

You can now run it with 

```
4L-gui
``` (this is the lacie program)

a simpler program without many features resides at 

```
/opt/lightscribeApplications/SimpleLabeler/SimpleLabeler
```

(use 4L-gui trust me)

Unforutunately there was some permissions problem that I cannot remember. It was an easy fix so I hope you will do this and also add that fix.

I am going to create a new partion and start all over again detailing my steps in hope that I can help others. I will work on Wacom on that. It may be a few days though, but I will continue to post.
If you would, could you run

```
sudo lshw >> hardware.txt
```

and upload hardware.txt so that we can compare any differences that might slip us up. Mine is attached to this post.
There we go!!
Kory

By the way, 
Thanks for the addition of the hard drive polling. I had forgotten about that. Cheers:)

---

### Post by siennalizard on 2008-06-25
Thanks for all this. Hold off on the Wacom work: I have been in touch with the developers, and they're going to be updating their driver to support this tablet any day.

I had forgotten lightscribe. Will test that soon and update the howto.

This is good collaboration we've got going on here!

Cheers,
J.

---

### Post by siennalizard on 2008-06-25
Here is the output of lshw as you wanted. I also attach a diff.

The differences are what you'd expect. At a glance:

[LIST]
[*]Hostname and serial number (obviously)
[*]CPU
[*]Cache and RAM sizes
[*]Network card (I have the pre-N Broadcom, you have the g)
[*]HDD partition sizes
[/LIST]

So I think we can continue in the knowledge that we're dealing with the same sort of machine.

I might update the title of the HOWTO to suit that fact, and then have a list at the top showing what hardware we believe the advice we give will match. Then people searching for their specific model will be able to find us...

J.

---

### Post by siennalizard on 2008-06-25
We have a small problem with LightScribe: I'm running Hardy 64-bit. I will also link to these instructions in the HOWTO (when I've tried them): [http://ubuntuforums.org/showthread.php?t=769926](http://ubuntuforums.org/showthread.php?t=769926)

J.

---

### Post by tempo500 on 2008-06-25
my webcam worked out of the box with skype, the mics work to after fiddling with the volume controls... below is my tomboy note if anyone is interrested.... and it looks like my gpu is at 80celius in idle!!!!! it happend after i changed some things on the system... but now i have a fresh installation of ubuntu. tried it once with the default packaged nvidia binaries, and now i am running the 173.14.09 beta....

---

### Post by siennalizard on 2008-06-25
tempo 500: thanks for your Tomboy note. Your suspend fix works, so i'll add it to the HOWTO.

The stereo mics do seem to feed into the speakers, but I couldn't get any recorded sound on them. Same for gali98, above.

Cheers,
J.

---

### Post by mirosol on 2008-06-26
This machine has already many resources to get everything working. For example [http://ubuntuforums.org/showthread.php?t=708726](http://ubuntuforums.org/showthread.php?t=708726) and [http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm).

---

### Post by gali98 on 2008-06-26
> **mirosol said:**
> This machine has already many resources to get everything working. For example [http://ubuntuforums.org/showthread.php?t=708726](http://ubuntuforums.org/showthread.php?t=708726) and [http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm).

Thanks for the second link so much.
I was never able to find that much info just searching on the web.
The first link is not organized right. You have to search page after page, and make sure what you are reading is updated.

I wanted to help make a tutorial on that is easy to follow and is updated with what's new and what works.
I think siennalizard is doing a great job.
Also Thanks tempo500 for the note.
Can you record out of the mics by the webcam? Read my earlier post to see the problem.
By the Way the link for the hard drive polling thing needs to be updated to:
[http://ubuntuforums.org/showthread.php?p=5030999](http://ubuntuforums.org/showthread.php?p=5030999)

that is the most recent thread on the issue and has more information.
Basically no fix is perfect in this situation and you have to compromise something. The good news is that the issue is on ubuntu Brainstorm

[http://brainstorm.ubuntu.com/idea/288/](http://brainstorm.ubuntu.com/idea/288/)

and it is marked as in development! Hopefully that issue won't plauge us on Intreped.
Thanks guys!
Kory

---

### Post by mirosol on 2008-06-26
Thank you Gali98. I had really hard time to get everything right. But thankfully many people were there to help out. I originally started [thread at ubuntu finland forum.](http://forum.ubuntu-fi.org/index.php?topic=18172.0) And like i said on my page, it's just *extended* translation of that post.

Reason, that i didn't translate that post to ubuntuforums.org was that there already were several different threads about wacom and tx2000-series in general.

It's pretty sad that at the time of writing, there's way too much work to get everything running properly on this machine. I'm just hoping that in future you can get ubuntu working out of the box, like ms os's.

It's not too much work for me, or for some other people. But it's hard to convince someone who's first machine is this tablet/laptop that linux/ubuntu is a good thing.

Personally i think that we all should write some email to HP. That corporation has history of taking GNU/Linux seriously, but still they use broadcom wifi-cards.. for example.

It was exiting to find out that linuxwacom project took it as "real thing" to make that patch to beta driver for us to use with wacom active digitizer touchscreen. Sad truth anyway is, that that patched driver is still far away from commercial drivers.

Other thing is that FPrint. I'm waiting for it's first final version.

After reinstalling and following my own collection of howtos, i have just two minor problems with:
1. Processor scaling is stuck at 2GHz - I wouldn't mind if it was winter :)
2. If i use stylus/pen in tablet mode for a while, synaptics-touchpad looses it's scroll-panel.

Latter had problems in vista as well. So it's not surprising "fault".

Sound recording and webcam recording work fine here by the way... Out of the box, ecxept that mute-button thing.

Suspend and hibernation needed just those 3 flags to be passed to kernel.

I think that wacom howto (originally by TomtheWombat) should be added to this thread's first post. Simply 'cause it's working fine. And it would take too long to wait for Xorg and kernel versions to have abilities to use these properly.

Once this thread's first post is done, i volunteer to be in team to add it to ubuntu wiki.

Thanks to all of you.

---

### Post by TomtheWombat on 2008-06-26
mirosol, it is hard for any company to take linux seriously.  The only mainstream company that provides state-of-the-art drivers is NVidia.  Intel is known for cooperating with Linux developers for basic hardware as well.  Past that, how is a company like NVidia supposed to choose hardware that is supported?  Kudos to Dell and the like for taking a stab in the dark, but what if open-source development for a particular device comes to a standstill and bugs arise?

That said, HP is really making zero effort as far as video drivers go..  Did they really have to screw with the video hardware??

And linuxwacom... We all got lucky there and a kind soul wrote a driver.  The Asus tablet was running with similar hardware for over a year without anybody writing a driver.

---

### Post by gali98 on 2008-06-28
Okay today I tried to enable Suspend and Hibernate. I ran into some problems.
Basically neither worked at all.
This is using the first post as a reference.
Now I need to note that I am on the rt kernel (realtime... for ubuntu studio stuff)
and that may be part of the problem. I am also not on 64 bit.
I am still thinking of installing in another partition. (64bit on that one)

Basically what happened is I would try each option, and the it would blank the screen but I could not get it to come back, and hibernate never shutdown.
I rebooted to try it on the generic kernel, and found out that it was broken as far as graphics go. The nvidia thing is not installed right or something. My guess is that the module didn't get installed right. It was very strange and for the life of me I could not fix it. When I went into safe graphics mode I reinstalled 
nvidia-glx-new and told it to use the nvidia driver, but it did not show in restricted drivers. I would actully rather just bury that problem since I use the rt kernel full time.
So anyway just alerting you of the problem. I will probably switch to 64bit to get us on the same page.
I will post again later. Keep up the good work,
Kory

by the way, siennalizard, I saw the wacom mailing list... Thanks for making the plea for us! :)

also @tomthewombat thanks for making a great tutorial. I have written two wacom tutorials
[http://ubuntuforums.org/showthread.php?t=619967](http://ubuntuforums.org/showthread.php?t=619967)
[http://ubuntuforums.org/showthread.php?t=553573](http://ubuntuforums.org/showthread.php?t=553573)

And I know how much work it is to write them. Obviously I let it slip away, but just incase you ever need to find something out, you might find a random bit of information you could use. I would be glad to be of service to you. Have a good day fellow ubunuers...

---

### Post by iofthestorm on 2008-07-12
Hi, I just installed Kubuntu 8.04.1 64 bit on my TX2110, which has the same wifi chipset, and I tried doing the ndiswrapper steps shown above but my wifi doesn't work. Could this be because of 64 bit? I'm on my desktop right now but I might try again with ndiswrapper later in the day.

---

### Post by Murphy2712 on 2008-07-13
> **iofthestorm said:**
> Hi, I just installed Kubuntu 8.04.1 64 bit on my TX2110, which has the same wifi chipset, and I tried doing the ndiswrapper steps shown above but my wifi doesn't work. Could this be because of 64 bit? I'm on my desktop right now but I might try again with ndiswrapper later in the day.

I think so : with my Debian I never succeed in having wifi with a 64bit kernel. Maybe we need a 64bit version of the driver.

---

### Post by tempo500 on 2008-07-27
did anybody get the omke.pl to work? it should enable the lid buttons even when its shut/tablet mode. [http://sourceforge.net/projects/omke/](http://sourceforge.net/projects/omke/)

it starts fine with "omke.pl -k 1" this command, but it doesnt work. any help?

ps.: my comands work fine when the lid is open...

---

### Post by gali98 on 2008-07-27
I have written a short tutorial on how to get the stylus and touchscreen working with a new version of linuxwacom made for Usb tablets.
This way you don't have to apply patches....
go here to see
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)
Kory

---

### Post by gali98 on 2008-08-04
The above tutorial has been updated and now pressure works....
Kory

---

