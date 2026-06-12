---
title: "Anyone running Ubuntu on a Lenovo X300?"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by voidmain on 2008-03-16
I'm trying to figure out which Lenovo to buy and want to go with the X300 because it is so light and solid, but I'm worried that it will be an uphill battle to get everything working with Hardy. Has anyone gotten Gusty or Hardy successfully working on a Lenovo X300? Or got it partially working and could describe the issues they ran into.

---

### Post by dré on 2008-03-18
[thread]("http://thread.gmane.org/gmane.linux.acpi.ibm-acpi.devel/1341") on Thinkpad ACPI list running Hardy

---

### Post by pchap123456 on 2008-03-29
I'm testing Hardy Heron beta on a Lenovo X300 (60GB SD) since yesterday.

The X300 is a great product; very light and with an excellent monitor which allows you to perfectly see what's on the screen even under the [spring] sun light.

On the other side, it is noisy due to a fan that apparently never (or almost) takes a break. Also, the sound doesn't work on Hardy Heron.

Phil

---

### Post by diego_dambra on 2008-04-13
I've managed to get most things running on Gutsy (7.10).

The minor issues are:
 - gnome-power-manager doesn't always start, resulting in very slow response when clicking on Quit and no brightness control (but you can invoke it through terminal)
 - build-in camera doesn't work with Skype
 - no flashing LED with WiFi activity
 - build-in mic records nothing (mic through mini-jack is working)
 - suspend/hibernate doesn't work

To get sound working I'd to patch alsa driver.

Basically things are working so good that I've managed to fully switch to this new machine :-)

---

### Post by sunshinege on 2008-05-01
I installed Ubuntu 8.04 about a month ago, and it works good now except no sound.

---

### Post by cmsj on 2008-05-05
I started the thread on the acpi-devel mailing list, and I've been running Hardy on my X300 since they were first available.
I'm hoping to prepare some packages for the audio, but in the meantime you need to compile a recent ALSA snapshot yourself.

Please feel free to join the thinkpad-x300 team on Launchpad and subscribe to the mailing list there :)

---

### Post by iNerdSure on 2008-05-05
> **cmsj said:**
> I started the thread on the acpi-devel mailing list, and I've been running Hardy on my X300 since they were first available.
I'm hoping to prepare some packages for the audio, but in the meantime you need to compile a recent ALSA snapshot yourself.

Please feel free to join the thinkpad-x300 team on Launchpad and subscribe to the mailing list there :)

I've just installed Ubuntu 8.04 on Lenovo X300 ThinkPad. Everything seems to be working fine, except NO SOUND and finger print recognition for security.

Anyone managed to get the sound to work? Or any suggestions, tips, advice, etc?  Thanks.  :confused:

---

### Post by iNerdSure on 2008-05-06
> **diego_dambra said:**
> I've managed to get most things running on Gutsy (7.10).

The minor issues are:
 - gnome-power-manager doesn't always start, resulting in very slow response when clicking on Quit and no brightness control (but you can invoke it through terminal)
 - build-in camera doesn't work with Skype
 - no flashing LED with WiFi activity
 - build-in mic records nothing (mic through mini-jack is working)
 - suspend/hibernate doesn't work

To get sound working I'd to patch alsa driver.

Basically things are working so good that I've managed to fully switch to this new machine :-)
Can you please help with the steps in getting the sound to work in Lenovo X300?  You mention "Patch ALSA driver" .. I'm not familiar with what this inolves or what it takes.

Your expert help will be greatly appreciated.

---

### Post by wired98 on 2008-05-07
Hi INerdSure,

I do not own a X300 but I plan to buy one somehow within this year. Therefore I already googled around for hardware infos and ubuntu compatibility recently.

[Here]("http://redmonk.com/sogrady/2008/04/29/sog-1-busted-sound-0-getting-audio-working-on-the-x300-under-ubuntu/") is a blog that gives detailed steps how to get sound working under ubuntu.

Further you can find useful infos in the thinkwiki:

[http://www.thinkwiki.org/wiki/Category:X300]("http://www.thinkwiki.org/wiki/Category:X300")

and

[http://www.thinkwiki.org/wiki/Category_talk:X300]("http://www.thinkwiki.org/wiki/Category_talk:X300")

Good luck with the sound!

---

### Post by iNerdSure on 2008-05-07
> **wired98 said:**
> Hi INerdSure,

I do not own a X300 but I plan to buy one somehow within this year. Therefore I already googled around for hardware infos and ubuntu compatibility recently.

[Here]("http://redmonk.com/sogrady/2008/04/29/sog-1-busted-sound-0-getting-audio-working-on-the-x300-under-ubuntu/") is a blog that gives detailed steps how to get sound working under ubuntu.

Further you can find useful infos in the thinkwiki:

[http://www.thinkwiki.org/wiki/Category:X300]("http://www.thinkwiki.org/wiki/Category:X300")

and

[http://www.thinkwiki.org/wiki/Category_talk:X300]("http://www.thinkwiki.org/wiki/Category_talk:X300")

Good luck with the sound!

Thanks for the tips and links.  I will try and see if the soluions work.

---

### Post by sunshinege on 2008-05-07
> **wired98 said:**
> Hi INerdSure,

I do not own a X300 but I plan to buy one somehow within this year. Therefore I already googled around for hardware infos and ubuntu compatibility recently.

[Here]("http://redmonk.com/sogrady/2008/04/29/sog-1-busted-sound-0-getting-audio-working-on-the-x300-under-ubuntu/") is a blog that gives detailed steps how to get sound working under ubuntu.

Further you can find useful infos in the thinkwiki:

[http://www.thinkwiki.org/wiki/Category:X300]("http://www.thinkwiki.org/wiki/Category:X300")

and

[http://www.thinkwiki.org/wiki/Category_talk:X300]("http://www.thinkwiki.org/wiki/Category_talk:X300")

Good luck with the sound!

Thanks for your information. 

According to [http://www.thinkwiki.org/wiki/Category_talk:X300](http://www.thinkwiki.org/wiki/Category_talk:X300), this bug will not be solved until kernel 2.6.26 is released.

When will kernel 2.6.26 be released?

> 
Things that don't work:

* Audio:
* Latest ALSA release shows Master and PCM only in the mixer and produces no audio
* [2008-03-11] Nightly alsa-driver snapshot populates the mixer with more realistic entries, but is still silent on both speakers and headphones.
* [2008-03-14] An extremely helpful ALSA developer is making the necessary changes. An early version is able to play sound and most of the card/mixer features work.
* [2008-04-25] Patch is in git kernel now, we won't officially see it until 2.6.26 is released.


---

### Post by iNerdSure on 2008-05-08
> **sunshinege said:**
> Thanks for your information. 

According to [http://www.thinkwiki.org/wiki/Category_talk:X300](http://www.thinkwiki.org/wiki/Category_talk:X300), this bug will not be solved until kernel 2.6.26 is released.

When will kernel 2.6.26 be release?
I hope 2.6.26 will be released soon.  Althernatively, I could do the ALSA driver upgrade myself.  But that would leave my X300 missing out on future ALSA upgrades, unless I so something on the backports as well.

I suppose the neater way is to wait for the 2.6.26 release, and in the meantime swap between Linux and WinVista on bootup, if sound is really needed. :(

---

### Post by voidmain on 2008-05-13
> **cmsj said:**
> I started the thread on the acpi-devel mailing list, and I've been running Hardy on my X300 since they were first available.
I'm hoping to prepare some packages for the audio, but in the meantime you need to compile a recent ALSA snapshot yourself.

Please feel free to join the thinkpad-x300 team on Launchpad and subscribe to the mailing list there :)

I couldn't find the thinkpad-x300 team on launchpad. Can you post the link to the group and also the thread you mentioned?

---

### Post by voidmain on 2008-05-13
Here is my current list of issues thus far. If anyone has solutions, please post them here.

[LIST]
[*]Fan is almost always on highest setting (REALLY annoying and noisy!)
[*]Suspend fails almost always
[*]No sound
[*]Battery life is less than in Windows
[/LIST]

I haven't tried anything with the camera or the finger print reader. My main pain point right now is the fan noise, which I haven't solved yet. However, it is brutally annoying, especially when I'm not doing anything and the fan just kicks on. Really lame.

---

### Post by tillk on 2008-05-28
> **voidmain said:**
> Here is my current list of issues thus far. If anyone has solutions, please post them here.


[*]Fan is almost always on highest setting (REALLY annoying and noisy!)


My fan does turn on demand, most times I don't hear it.

> 
[*]Suspend fails almost always


No problem here, neither suspend to RAM, nor suspend to disk (hibernate). Both works out of the box with hardy on my X300 (type 6478-14G).

> 
[*]No sound


works with recent alsa nightly code. I am using alsa-driver-hg20080516 at the moment, sound output and input both work. Move contents of /lib/modules/[your-kernel-version]/ubuntu/sound/ out of the way, download recent alsa source code, configure, make and make install it and finally listen and record sound...

> 
[*]Battery life is less than in Windows


I can't compare. I get hardly 4 hours doing "light but constant work" (some coding, some email, some web browsing, some music playing) using wifi all the time and screen brightnes set to medium levels. Without wifi it's some minutes more (can't really tell, but must be about 4.5 to 5 hours). The 6 cell battery isn't really a big one: getting 4 hours out of a 44 Wh battery means the computer is consuming only about 11 W, which is quite good. The X300 isn't eating much energy, the battery (even the "big" 6 cell) is just too small...

> 
I haven't tried anything with the camera or the finger print reader.


Both work for me out of the box with Hardy.

> 
 My main pain point right now is the fan noise, which I haven't solved yet. However, it is brutally annoying, especially when I'm not doing anything and the fan just kicks on. Really lame.

Strange behaviour. As I said: My fan stays calm most of the time (yes, running hardy).
I still have some strange issues switching wifi and bluetooth usinf Fn-F5, sometimes wifi even crashes. But I've found ways to deal with that (turning on the wifi kill switch at least once after each hibernate circle seems to avoid the crashes).

---

### Post by sunshinege on 2008-05-30
I cannot find where to download nightly code from alsa-project, I browse all directories in [ftp://ftp.alsa-project.org](ftp://ftp.alsa-project.org), and only find there are some files under subdir /pub/cvsroot but all these cannot download.

Can you help me to download the nightly code? and I also don't know how to build it (must I uninstall the current version of alsa-driver?). I want to try to build.

> **tillk said:**
> works with recent alsa nightly code. I am using alsa-driver-hg20080516 at the moment, sound output and input both work. Move contents of /lib/modules/[your-kernel-version]/ubuntu/sound/ out of the way, download recent alsa source code, configure, make and make install it and finally listen and record sound...

---

### Post by tillk on 2008-06-02
> **sunshinege said:**
> 
Can you help me to download the nightly code?


Try this location: [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/)

> 
 and I also don't know how to build it (must I uninstall the current version of alsa-driver?). I want to try to build.

On Hardy you need to move contents of /lib/modules/[your kernel version]/ubuntu/sound out of the way. You may simply rename the contents of that directory. Then configure, make and make install the downloaded alsa drivers.

---

### Post by sunshinege on 2008-06-02
> **tillk said:**
> Try this location: [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/)

On Hardy you need to move contents of /lib/modules/[your kernel version]/ubuntu/sound out of the way. You may simply rename the contents of that directory. Then configure, make and make install the downloaded alsa drivers.

Thank you very much!

I had download the driver code, and unfold them to directory alsa-driver, and then move to /lib/modules/2.6.24-17-generic/ubuntu/sound/.

But I wonder which parameter with configure, I use:

./configure --with-cards=snd-hda-intel

and then make, and make install, 

output said: 
> WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

But the result of alsamixer shows all are max, nothing are shows muted.

tillk, Can you give me a more detailed guide?

---

### Post by tillk on 2008-06-03
> **sunshinege said:**
> Thank you very much!

I had download the driver code, and unfold them to directory alsa-driver, and then move to /lib/modules/2.6.24-17-generic/ubuntu/sound/.


You don't need to move the alsa sources to that directory. Just move the preinstalled Ubuntu alsa drivers in that directory out of the way.

> 
But I wonder which parameter with configure, I use:

./configure --with-cards=snd-hda-intel


Just plain ./configure should do the job.

> 
and then make, and make install, 


Have you done /etc/init.d/alsasound restart to unload the old drivers and load the new ones? If that doesn't help, a reboot should do the job.

> 
tillk, Can you give me a more detailed guide?

That's what I did:
[LIST]
[*]Unpack the downloaded alsa drivers somewhere (e.g. in your home directory): 
```
tar xjf alsa-driver-[date].tar.bz2
```
[*]change to the now created directory alsa-driver: 
```
cd alsa-driver/
```
[*]run configure and make: 
```
./configure
[...]
./make
[...]
```
[*]now become root (sudo -s) and move the old alsa drivers out of the way:
```
mv /lib/modules/[kernel version]/ubuntu/sound/alsa-driver/ ~/alsa-driver.bak/
``` (moves them to a folder alsa-driver.bak in root's home directory)
[*]now install the new alsa drivers:
```
make install
```
[*]restart alsa:
```
/etc/init.d/alsasound restart
```
[*]adjust volumes (e.g. with alsamixer)
[/LIST]
If you still don't hear anything try rebooting to be sure the new alsa drivers are used.

---

### Post by pylon42 on 2008-06-03
> 
Fan is almost always on highest setting (REALLY annoying and noisy!)

Yes! The fan is killing me - I have to keep a set of headphones on when I'm using my x300 or it drives me insane...

When on AC it's always at max - when on battery it pulses to max (even more annoying).

---

### Post by oeffentlich on 2008-06-03
I had the same fan issue on a t61.

 whats about using tp-fancontrol? fan was only running, when i was running virtual box or something differnt, which was stressing the cpu, in the end my tp was more quiet than under xp or vista.

cheers

---

### Post by pylon42 on 2008-06-04
Hrmmm... I can't find that package. Is it under a different name?

---

### Post by pylon42 on 2008-06-04
Also, has anyone else lost sound recently and not been able to get it back by reinstalling alsa?

---

### Post by tillk on 2008-06-04
> **pylon42 said:**
> Also, has anyone else lost sound recently and not been able to get it back by reinstalling alsa?

Let me guess: You lost sound after a kernel update. Then you have to run the whole procedure again: Move contents of /lib/modules/[YOUR_NEW_KERNEL_VERSION!!!]/ubuntu/sound away and run alsa installation from source code. After a reboot sound should be there again.
Reinstalling alsa drivers from source isn't enough because the kernel update installs again the not working alsa drivers into the new modules directory. Those must be gone, otherwise they will be used.

---

### Post by pylon42 on 2008-06-04
> **tillk said:**
> Let me guess: You lost sound after a kernel update. Then you have to run the whole procedure again: Move contents of /lib/modules/[YOUR_NEW_KERNEL_VERSION!!!]/ubuntu/sound away and run alsa installation from source code. After a reboot sound should be there again.
Reinstalling alsa drivers from source isn't enough because the kernel update installs again the not working alsa drivers into the new modules directory. Those must be gone, otherwise they will be used.


Thank you for the response - I did try copying sound to sound.bak before installation, but it didn't seem to help :(

When I do a ./configure, make, make install on alsa 1.0.16, it seems to be copying the files to:
/lib/modules/[YOUR_NEW_KERNEL_VERSION!!!]/kernel/sound 

as opposed to:
/lib/modules/[YOUR_NEW_KERNEL_VERSION!!!]/ubuntu/sound 

Could that have something to do with my problems?

---

### Post by tillk on 2008-06-04
> **pylon42 said:**
> Thank you for the response - I did try copying sound to sound.bak before installation, but it didn't seem to help :(

When I do a ./configure, make, make install on alsa 1.0.16, it seems to be copying the files to:
/lib/modules/[YOUR_NEW_KERNEL_VERSION!!!]/kernel/sound 


Yes, that's the default location for alsa drivers. Don't care. As long as modprobe finds them when needed there is no need to worry.
But that's why it is important to move the original Ubuntu alsa drivers in ubuntu/sound/ away, otherwise the will still be used.

Are any sound modules loaded? Try lsmod | grep snd and see if snd_hda_intel is listed. If so, try modinfo snd_hda_intel to find out what module is used (look at the filename entry in the first line, is that the correct path to the newly installed alsa drivers)·

---

### Post by pylon42 on 2008-06-04
> **tillk said:**
> Yes, that's the default location for alsa drivers. Don't care. As long as modprobe finds them when needed there is no need to worry.
But that's why it is important to move the original Ubuntu alsa drivers in ubuntu/sound/ away, otherwise the will still be used.

Are any sound modules loaded? Try lsmod | grep snd and see if snd_hda_intel is listed. If so, try modinfo snd_hda_intel to find out what module is used (look at the filename entry in the first line, is that the correct path to the newly installed alsa drivers)·

Ha! Right you are - it's using my sound.bak instead of my sound folder...

I'll try completely removing it and see what happens

---

### Post by pylon42 on 2008-06-04
Well... at least it's progress :)

modinfo snd_hda_intel now shows that I'm using the proper driver (the one that was just installed to kernel)

However, I still don't have sound :(

I ran alsamixer to make sure it wasn't muted...

---

### Post by pylon42 on 2008-06-04
I tried the same process with a different alsa driver. This time my audio control has a red x through it and it says:

No volume control GStreamer plugins and/or devices found.

modinfo snd_hda_intel confirms that it is still pointing at the correct location.

:(

---

### Post by maxki on 2008-06-04
Is built-in 3G modem working alright ? Anyone tried ?

---

### Post by pylon42 on 2008-06-05
Well... things are getting worse again. I tested 3 previous versions of the alsa driver, then bam - I can no longer compile any version. When I try to "make" it spits out:

make: *** [include/sndversions.h] Error 2

This is using the exact same drivers and the exact same method I used before... about a hundred times...

---

### Post by kleeman on 2008-06-06
I got a X300 three days back. 

Installed hardy from a usb drive which meant I had to edit /etc/fstab and remove the /dev/sdb1 line to get usb flashdrives to work.

I updated the kernel to version 2.6.24-18 yesterday using the proposed repository AND ALSA STARTED WORKING. It did not with the original kernel. The sound is amazing for a laptop as it has two large front speakers. audacious playing a classical music stream is just fantastic.

I also got ekiga working perfectly: The camera works out of the box as does the builtin microphone.

wireless is working flawlessly with network-manager and a wpa encrypted access point.

The fan is annoying. I watched the sensors applet and several things stand out. The fan seems to have only three settings 0, 1800rpm and 5500rpm. The cpu seems to have only 2 settings (I need to check this) 800Mhz and 1.2Ghz.
This seems very coarse grained compared to Windows (I have Vista on a dual boot).

The batteries are great (I have two). With normal use there appears to be about 4.5 hours of life.

The external video I tested with a projector and it did not work very well. Need to dig into this more. It worked flawlessly in Vista so this may be an intel driver issue.

Suspend works flawlessly...

Overall I give Hardy high marks indeed in getting most of the hardware working.

Next steps: Investigate the gps receiver, verizon wan and bluetooth....

EDIT: Sound stopped working when I upgraded the kernel to 2.6.24-19. It appears  only to work with 2.6.24-18.

---

### Post by gnychis on 2008-06-07
> **kleeman said:**
> I got a X300 three days back. 

Installed hardy from a usb drive which meant I had to edit /etc/fstab and remove the /dev/sdb1 line to get usb flashdrives to work.

I updated the kernel to version 2.6.24-18 yesterday using the proposed repository AND ALSA STARTED WORKING. It did not with the original kernel. The sound is amazing for a laptop as it has two large front speakers. audacious playing a classical music stream is just fantastic.

I also got ekiga working perfectly: The camera works out of the box as does the builtin microphone.

wireless is working flawlessly with network-manager and a wpa encrypted access point.

The fan is annoying. I watched the sensors applet and several things stand out. The fan seems to have only three settings 0, 1800rpm and 5500rpm. The cpu seems to have only 2 settings (I need to check this) 800Mhz and 1.2Ghz.
This seems very coarse grained compared to Windows (I have Vista on a dual boot).

The batteries are great (I have two). With normal use there appears to be about 4.5 hours of life.

The external video I tested with a projector and it did not work very well. Need to dig into this more. It worked flawlessly in Vista so this may be an intel driver issue.

Suspend works flawlessly...

Overall I give Hardy high marks indeed in getting most of the hardware working.

Next steps: Investigate the gps receiver, verizon wan and bluetooth....

EDIT: Sound stopped working when I upgraded the kernel to 2.6.24-19. It appears  only to work with 2.6.24-18.

what repository are you talking about for the kernel to get the sound working?

---

### Post by gnychis on 2008-06-07
btw, I've also been trying to get the GPS to work... I've found out that the GPS uses the Sierra EVDO modem.  
"Sierra Wireless 1X/EVDO module and a GPS that uses the EVDO module's aGPS"
... take from [http://www.mobiletechreview.com/notebooks/Lenovo-ThinkPad-X300.htm](http://www.mobiletechreview.com/notebooks/Lenovo-ThinkPad-X300.htm)


Here's where it's initialized:
```

[   22.801284] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   22.838168] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (1 port)
[   22.838211] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (3 port)
[   22.838263] sierra 4-1:1.0: Sierra USB modem (3 port) converter detected
[   22.844625] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB0
[   22.844705] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB1
[   22.844776] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB2
[   22.844794] usbcore: registered new interface driver sierra
[   22.844798] /build/buildd/linux-2.6.24/drivers/usb/serial/sierra.c: USB Driver for Sierra Wireless USB modems: v.1.2.5b

```

---

### Post by kleeman on 2008-06-08
> **gnychis said:**
> what repository are you talking about for the kernel to get the sound working?

Go to the update tab in the software sources app and enable the hardy-proposed radio button. Only the 2.6.24-18 works. Weird!

---

### Post by kleeman on 2008-06-10
> **gnychis said:**
> btw, I've also been trying to get the GPS to work... I've found out that the GPS uses the Sierra EVDO modem.  
"Sierra Wireless 1X/EVDO module and a GPS that uses the EVDO module's aGPS"
... take from [http://www.mobiletechreview.com/notebooks/Lenovo-ThinkPad-X300.htm](http://www.mobiletechreview.com/notebooks/Lenovo-ThinkPad-X300.htm)


Here's where it's initialized:
```

[   22.801284] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   22.838168] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (1 port)
[   22.838211] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (3 port)
[   22.838263] sierra 4-1:1.0: Sierra USB modem (3 port) converter detected
[   22.844625] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB0
[   22.844705] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB1
[   22.844776] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB2
[   22.844794] usbcore: registered new interface driver sierra
[   22.844798] /build/buildd/linux-2.6.24/drivers/usb/serial/sierra.c: USB Driver for Sierra Wireless USB modems: v.1.2.5b

```

Any luck with that? I tried hooking /dev/ttyUSB(0,1,2) to gpsd but it didn't work. The sierra.c driver has no clues either.... I was thinking of asking the driver's author....

---

### Post by gnychis on 2008-06-10
still no luck yet either :\ I was conversing with someone in #gpsd on freenode, and they weren't so sure either

---

### Post by diego_dambra on 2008-06-11
> **maxki said:**
> Is built-in 3G modem working alright ? Anyone tried ?

Yep, hardware is detected and I'm able to connect to ISP through Networkmanager.

While I'm no expert, you should check that SIM card is compatible and modem isn't locked for a specific telco provider.

---

### Post by kleeman on 2008-06-12
> **diego_dambra said:**
> Yep, hardware is detected and I'm able to connect to ISP through Networkmanager.

While I'm no expert, you should check that SIM card is compatible and modem isn't locked for a specific telco provider.

Mini-howto on this might be useful....:):)

---

### Post by kleeman on 2008-06-12
I made some progress on gps. I heard back from the sierra driver author and it looks like gps is possible under linux. According to the sierra docs

[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601)

you can communicate with the wwan card using the minicom command (the package is in the Ubuntu repos). Then to set the correct port issue

minicom -s

and select the serial port option (third option).
Set it to /dev/ttyUSB0

Save and exit

Then issue

minicom

The sierra docs have various commands you can interrogate the card with.
To start up the gps tracking the sierra driver author told me you issue the following in minicon

AT!GPSTRACK=1,255,1000,1000,1

I got a tracking response and an OK

I then found that the gps data was coming into /dev/ttyUSB2 You can check this with

cat /dev/ttyUSB2

Then to feed this data into gps apps (like gpsdrive) you start up gpsd (also in the repos) with

sudo gpsd /dev/ttyUSB2

It comes into port 2947 and you can check that this is working with

telnet localhost 2947

type 'r' 

and you should see the gps commands.

xgps 

gives a nicer check (in the gps-utils package)

I haven't got gpsdrive working yet but the above is a start....

Edit: gpsdrive works my signal was too weak above (see below)...

---

### Post by gnychis on 2008-06-12
That is great progress kleeman, thank you!

Can you verify that the initialization code you gave me is correct?  When I try it I get an error:
```

Welcome to minicom 2.3-rc1

OPTIONS: I18n 
Compiled on Dec 10 2007, 10:36:19.
Port /dev/ttyUSB0

                 Press CTRL-A Z for help on special keys
                                                     
AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0                     
OK                                                   
AT!GPSTRACK=1,255,1000,1000,1                        
ERRCODE = 17

OK

```

I have set it to /dev/ttyUSB0

Is your correspondence with the sierra folks archived somewhere online that I can read?

Thanks!
George

---

### Post by kleeman on 2008-06-12
Woohoo it works with gpsdrive!!! 

I just had to take the x300 outside and bingo the gps data started flowing and gpsdrive located me highly accurately (I clicked the download map and I was set).

gnychris

your commmand looks OK. If you PM me your email adress I will forward (the very short) email. Some suggestions:

1) try lowercase that worked better for me for some weird reason
2) try the following so we can compare settings:
at!pcinfo
3) The radio may be switched off try
at!pcstate=1
4) Check signal strength with
at!rssi?

---

### Post by gnychis on 2008-06-12
awesome, great work!

I am still getting the error after trying to power it on:
```

at!pcinfo                                            
State: 1 (ONLINE)
LPM force flags - W_DISABLE:0 User:0 Temp:0 Volt:0
W_DISABLE: 0
Poweroff enabled: 1
LPM Persistent: 0 

OK
at!pcstate=1
OK
at!rssi?
-50
                                                                                
OK  

at!gpstrack=1,255,1000,1000,1                                                   
ERRCODE = 17                                                                    
                                                                                
OK                                                                         

```

I seem to be getting an RSSI reading tho, do we have the same hardware?

I'm concerned with the "Poweroff enabled: 1"

---

### Post by kleeman on 2008-06-12
Your settings are all the same as mine (including the one that was worrying you). Did that command have commas separating the numbers?

Here is my entry from lsusb

Bus 004 Device 003: ID 1199:0220 Sierra Wireless, Inc.

Is yours the same?

I emailed the message from the driver author...

Edit: Does GPS work under Windows? Mine did...

---

### Post by gnychis on 2008-06-12
interesting.  they are all commas

my lsusb entry is the same except for the bus and device:
```

Bus 004 Device 005: ID 1199:0220 Sierra Wireless, Inc.

```

---

### Post by kleeman on 2008-06-12
OK same hardware by the look of it. Did windows work?

your signal looks stronger than mine 
at!rssi?

gives -90 for me.

From the sierra docs

A range from   -60 dbm to -90 dBm can be considered adequate

---

### Post by gnychis on 2008-06-12
i didn't even let windows boot completely for the first time before i wiped it completely clean :)

I sent their support an e-mail in regards to the issue.  hopefully they can provide some useful feedback.  Until then, no rush on fixing the issue, it's more of a toy!  I greatly appreciate the help.

---

### Post by kleeman on 2008-06-12
One other thought is that I configured the wwan card first according to the sierra docs. Perhaps something was set in the card then,,,

---

### Post by gnychis on 2008-06-12
> **kleeman said:**
> One other thought is that I configured the wwan card first according to the sierra docs. Perhaps something was set in the card then,,,

in linux?  if so, can you point me to the document and section that you followed for configuration?  did you install a new driver or keep the ubuntu one?

---

### Post by kleeman on 2008-06-12
Sure. In

[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601)

I followed the Connecting to the network section

I did not mess with the kernel driver as dmesg seemed to show that working fine.

---

### Post by kleeman on 2008-06-12
By accident I issued
ati!pcinfo

and got the following extended hardware info

Manufacturer: Sierra Wireless, Inc.
Model: MC5725 Rev 2.0 (2)                                                       
Revision: p2006001,50853 [Apr 26 2007 09:57:49]                                 
APPL: SWI6800_FP.00.60.01 2007/04/26 11:14:44                                   
BOOT: SWI6800_FP.00.60.01 2007/04/26 11:14:44                                   
QCOM: SWI6800_FP.00.60.01 2007/04/26 11:14:44                                   
SWID: SWI6800_FP.00.60.01 2007/04/26 11:14:44 [LENOVO_00]                       
USBD: SWI6800_FP.00.60.01 2007/04/26 11:14:44 [LENOVO_00]                       
USB VID: 0x1199 PID: 0x0220                                                     
ESN: 0x605B5A5A                                                                 
+GCAP: +CIS707-A, CIS-856, CIS-856-A, +MS, +ES, +DS, +FCLASS                    
                                                                                
State: 1 (ONLINE)                                                               
LPM force flags - W_DISABLE:0 User:0 Temp:0 Volt:0                              
W_DISABLE: 0                                                                    
Poweroff enabled: 1                                                             
LPM Persistent: 0

---

### Post by gnychis on 2008-06-13
still no luck after trying to configure :(

---

### Post by kleeman on 2008-06-13
I was trying to automate minicom and someone (evilghost from dslreports thanks man) suggested something much simpler which works. As root execute

echo 'at!gpstrack=1,255,1000,1000,1' > /dev/ttyUSB0

---

### Post by kleeman on 2008-06-13
In case anyone needs a howto here is how I got the x300 gps working automatically:

1) sudo apt-get install gpsd gpsdrive gpsd-clients gpsdrive-scripts
2) Edit the file /etc/default/gpsd as root (sudo gedit) and replace the line
START_DAEMON="false"
with
START_DAEMON="true"

replace
DEVICES=""

with

DEVICES="/dev/ttyUSB2"

3) Edit the file /etc/rc.local as root and insert the following line as the
second last line

echo 'at!gpstrack=1,255,1000,1000,1' > /dev/ttyUSB0

After reboot launch gpsdrive from Applications------> Internet
and you should see a green gps indicator bottom right.

I have found cgps launched from a terminal is a nice diagnostic program to check that things are OK (it has some error measures as well).

---

### Post by gnychis on 2008-06-18
I'm getting closer!

Sierra e-mailed me back and said issue:
```

AT!GPSLOCK=0

```

After doing so I now get this output:
```

at!gpstrack=1,255,1000,1000,1                                                   
Tracking initiated                                                              
                                                                                
OK

```

Is that the output you get when you issue the command?

I still don't see any GPS data on /dev/ttyUSB2 though... maybe because I'm indoors, I will try a bit later outdoors.

When I run gpsdrive it says that it does not have enough satellites in view.

BTW, you forgot to add "install" to your apt-get line in your gpsdrive instructions :)  Thanks though, they're great!

---

### Post by kleeman on 2008-06-18
Yep that's what I got. I also found I had to head outdoors.....

---

### Post by Mach1US on 2008-06-23
I just set-up on with HH but have some freezing problems.

---

### Post by gnychis on 2008-06-30
should i be running 64-bit ubuntu?

---

### Post by garrydolley on 2008-07-16
> **voidmain said:**
> 
I haven't tried anything with the camera or the finger print reader. My main pain point right now is the fan noise, which I haven't solved yet. However, it is brutally annoying, especially when I'm not doing anything and the fan just kicks on. Really lame.

I've fixed the fan problem on my X300.  I blogged about it here: [http://scie.nti.st/2008/7/16/noisy-fan-on-the-x300](http://scie.nti.st/2008/7/16/noisy-fan-on-the-x300)

-- Garry

---

