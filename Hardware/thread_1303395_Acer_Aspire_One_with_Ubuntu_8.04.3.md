---
title: "Acer Aspire One with Ubuntu 8.04.3"
date: 2009-10-28
forum: Hardware
---

### Post by leorolla on 2009-10-28
* Facts

I have a netbook Acer Aspire One, that came with Windows XP.
I am trying to migrate to Ubuntu 8.04.

I downloaded Ubuntu 8.04.3 from [http://releases.ubuntu.com//hardy/ubuntu-8.04.3-desktop-i386.iso](http://releases.ubuntu.com//hardy/ubuntu-8.04.3-desktop-i386.iso) , then mounted the ISO with Daemon tools, and the auto-run of the virtual CD opened.

I chose "install inside windows".

Now I am following the guide
[https://help.ubuntu.com/community/AspireOne/Ubuntu8.04](https://help.ubuntu.com/community/AspireOne/Ubuntu8.04)

Some things worked well, some are out of date, and some are not working well.


* Motivation

Why Inside Windows?
Why 8.04?
Unless you thougt of making the above questions, you can skip this part.

Installing inside Windows is because while I try to go tough and use only good software, I also need to the computer for the uses I bought it for: internet browse with java plug-in; listen to music; subversion 1.4 or later; latex, latex packages, pdflatex, dvips, dvipdf, ps2pdf; viewing pdf files; open usb flash memory; use skype with built-in or external sound, with built-in or external microphone, with or without built-in or external webcam, in all possible combinations. I think these are all.

I need the computer, I know Windows does suck, but it gives all the above functionalities. Once I can get them all working neat and nice on Ubuntu, I cannot fire Windows.

I chose Ubuntu 8.04 because I have issues with KDE 4, detailed below. I use Gnome, but I borrow packages from KDE, such as kile, kghostview, kdiff3 and kdvi. I don't know how to enforce KDE 3 inside later Ubuntu distros, and anyway if it's too much of a detour, I would rather keep it simpe and stay with Ubuntu 8.04.

KDE 4. KDVI is no longer there, and nothing does exaclty the same job. With KILE 2.0 and KDVI I can do really great. One key takes me from a TEX file to the DVI, whose viewer is embedded in KILE, positioned exactly at the corresponding paragraph, and One mouse click on the DVI brings me back to the TEX source at the corresponding source line. With the latest KDE version I still couldn't get that functionality running so well: Okular does tell Kile to position on the correct line, but the okular windows is still in front, and it is not done with only one mouse click. I like the KILE 2.0 interface far better. KDE 4 is too heavy, I don't need all that.


* Preliminary question

To make the thread is useful to other Aspire One users and to update the Ubuntu documentation pages, should we treat all issues here one at a time, or do we treat one problem at a time?


* Support questions


Step 1

I installed 8.04.3 instead of 8.04.1
I installed inside Windows


Step 2


WIRELESS

Wireless was already working out of the box.

I followed the "madwifi" procedure, I now can now switch it on and off from the computer's key for that.
Great!!!

**[COLOR=Red]Remark:[/COLOR]**
"cd madwifi-hal-0.10.5.6-r3879-20081204" doen't work: the directory created had a different name and I replaced it by that name.


WIRELESS LED

It doesn't work out of the box.

I haven't done anything yet.


WEBCAM

I don't k now how to test if it works out of the box.

I followed the instructions.

[COLOR=Black]During the last one it opened a black window, which I guess should be showing myself from the webcam, but the system completely halted. I haven't tested after rebooting, though.
[/COLOR] 
Edit: after rebooting it works fine.


AUDIO

I couldn't hear any sound before, but I had the sound icon on the panel.

After doing

```

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
sudo alsa force-unload
sudo depmod -ae
sudo modprobe snd-hda-intel

```[COLOR=Red]**the sound icon disappeared from the panel, it opened a windows asking me if I wanted it to reload.**[/COLOR]
I just closed the window.

I have tried

```

options snd-hda-intel model=acer-aspire

```and

```

options snd-hda-intel model=auto

```[COLOR=Red][B]but still I don't hear sounds and I don't see the sound icon.
[/B][/COLOR] 

CARD READER
USB MOUNT

I have not tested yet.


NOISE (FAN CONTROL)
VIDEO AND 3D PERFORMANCE
Screen Tweaks
TOUCHPAD TWEAKS
TWEAK FOR BOOTUP SPEED
TWEAKS FOR POWERSAVING

I'm trying to first get the most important running.
Then I try these.


HIBERNATE

I installed inside Windows, so there is no hibernate.


Alternative Method for upgrading ALSA and settings

[COLOR=Red]Should I do it?[/COLOR]


NETBOOK REMIX
[COLOR=Red]
Should I install it?[/COLOR]



Thank you in advance!!!

---

### Post by bgeraghty on 2009-10-28
Which Model AcerAspireOne do you have?  I'm using an Asus eeePC 1000H netbook, which I was told had a very limited choice of operating systems when I purchased it.  I was suprised to see that I was able to get full functionality out of 6 different flavors of Linux. You might get away with a higher version, and you'll probably upgrade to it for the most part anyways.

[https://help.ubuntu.com/community/AspireOne/Home](https://help.ubuntu.com/community/AspireOne/Home)

I'm not really for the 'inside windows' option of install, because of the decrease in harddrive performance, along with the risk of an unclean shutdown.  I personally would have resized my windows partition, and installed ubuntu to its own separate partition, along with GRUB bootloader in the MBR. It would give you the same functionality you have now, (windows + linux, choice at boot time) minus the encapsulated filesystem. The filesystem you have would make more sense to me if this was a persistent, removable media installation.

Are you absolutely set on KDE? don't forget the options of other window managers, such as GNOME, (my favorite), along with the fact that you can disable the GDM graphical login, and automatic start of x, so you can configure your x to your liking/compatibility. 

Wireless works... ok... the LED seems like a minor detail. You can probably monitor activity some other way if push comes to shove.

Webcam, look into your Model Number again, and from there find the specific name of the webcam in the netbook. (It could possibly be classified as a usb cam, even though it is internal)

The rest of these system and accessory devices require the same research if they are giving you more than just a little grief to get working.  

Didn't care for Netbook Remix all that much, I was turned off by the default KDE and bloated navigation window that came up at the start.

Hope I could be of some help to you.

---

### Post by leorolla on 2009-10-28
Thanks!!!

My model: AOD150-1577 Aspire One 10.1" Netbook PC
( _[link]("http://us.acer.com/acer/seu30e.do?kcond61e.c2att101=55102&LanguageISOCtxParam=en&link=ln400e&CountryISOCtxParam=US&acond125e=55102&sp=page18e&ctx1g.c2att92=843&ctx2.c2att1=25&ctx1.att21k=1&CRC=1156696204")_ to this model inside acer.com )

Inside Windows: is easier to remove it in 10 seconds and re-install it in a few minutes in case I mess up. When I learn how to get it running well, step-by-step, I will do a true installation and repeat the steps.

I have not tried to make the LED work.

KDE: I use Gnome. When I mention KDE, it's because I borrow packages from KDE, such as KILE, KGHOSTVIEW, KDIFF3 and KDVI. I don't understand "so you can configure your x to your liking/compatibility".

I am following exactly your link. From there I clicked on Ubuntu 8.04 and now I am reporting what comes out of it.

Main questions at the moment:

- The recommended procedure to enable Audio did not work
- I wonder if Alternative Method for upgrading ALSA and settings is useful

Thanks.

---

### Post by teh603 on 2009-10-28
A lot of the hardware used in these netbooks was either very new or not released yet when Hardy was par for the course. I'd suggest trying Jaunty or Karmic. I know Jaunty works fine with my AAO. I haven't tried Karmic yet (one more day) but I doubt anything should break.

On Jaunty, the only thing I've had major trouble with is the card reader detection issue. The mic seems to work, the webcam works, sound works, and all that. When I was using eeebuntu Intrepid on it, the webcam and sound didn't work after startup (which was odd because it still played the startup music).

---

### Post by leorolla on 2009-10-28
Thank you, too!

I will keep trying... If it really ends up not being possible, I uninstall Wubi 8 and try Wubi 9 ;-)

---

### Post by leorolla on 2009-10-29
Webcam is working after reboot.

Sound is still mising.

---

### Post by teh603 on 2009-10-29
I just installed Karmic after a rather disastrous visit to Xubuntu, and the wifi led is working. Sound isn't anymore, though. Course, that only means I don't have to mute before playing certain games at work...

---

