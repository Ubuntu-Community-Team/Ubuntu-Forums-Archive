---
title: "sound and touchscreen and wifi problems on a HP Touchsmart 600-1050sc"
date: 2010-01-17
forum: Hardware
---

### Post by SusurAce on 2010-01-17
I have been using hp 500 series machines running linux for more than 6 months now without trouble. 

Unfortunately my boss has just thrown me under the bus by deciding to buy a new touchsmart 600-1050

The problem is, that just about everything that could possibly change has changed.
Here is a link to the specs:
 [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01961233&tmp_task=pr...]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01961233&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=4040952&lang=en")

I made a clean install of the 64 bit version of ubuntu 9.1 karmic koala and the situation is


Graphics:  
Works straight out of the box with the standard Nvidia drivers


Sound:  
The ALSA driver recognizes the sound card and I am getting good quality sound out of the headphones but no sound from the speakers at all.  
I ran a script from the ALSA project website to identify my system (here are the results): 
[http://www.alsa-project.org/db/?f=54eb300bcc167100f5603c1dd43e565356441ee2](http://www.alsa-project.org/db/?f=54eb300bcc167100f5603c1dd43e565356441ee2)
It identifies the codec as: ALC888 (the specs for the 600 call it ALC888s so I guess this is right) but I tried every available option I could think of in my alsa-base config file, but still I only get sound out of the headphones.


Wireless:
 Ubuntu identifies it as "RaLink RT3092 Wireless 802.11n 2T/2R PCIe",  but it does not work out of the box and I have not been able to find a Linux driver for it yet


Touchscreen:
The touch screen is listed as a NextWindow 1950.  I tried installing evtouch, as all nextwindow screens are supposed to be evtouch compatible, but I am getting absolutely no response at all. 


I have sent nextwindow an email to there support, so hopefully *I will hear something from them.*


If anyone else out there is working on something similar, or can offer me any help at all, I would be very greatful

---

### Post by blade_fantasy on 2010-01-21
Hello! this is my /etc/modules  content:

ndiswrapper
lp
rtc
hp-wmi
rt3090sta

Tle last line is about wi-fi and it's working (i've tested just open connection)

bye

---

### Post by chontler on 2010-03-31
Hi SusurAce,

Did you have any joy regarding the touchscreen?  I just got the 300 model and have had no success getting the touchscreen to work.

in particular I found this vid: [http://www.youtube.com/watch?v=V6TK5R4XX9Y](http://www.youtube.com/watch?v=V6TK5R4XX9Y)
that has a link to some instructions that may help you, but didn't work for mine.

best regards
Rob

---

### Post by chontler on 2010-04-01
If you're still around and for anyone like me whose been searching for touchsmart fixes, I got the wireless working for the RT3092 (ubuntu 9.10) this way.

Add the following sources:

deb [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu) karmic main 
then in package manager you can now install rt3090-dkms 

reboot and it's good to go

I got the info from here:
[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)


:popcorn:

---

### Post by blade_fantasy on 2010-05-10
Please!
What about 
Sound (only on headphones)
TV aver A323
Touch screen

????

---

### Post by jdbower on 2010-05-13
I wish I had more definitive information to report, but [perhaps this will help]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313")?  Either way I'll be watching this thread closely for my TouchSmart 600 - hopefully touchscreen systems will be the next big thing for Canonical to tackle.

On a plain Lucid install everything seems to work for me except sound from the speakers (headphones are fine) and the Touchscreen.  I'm uncertain if wireless is working, I have a hidden SSID and a hardwire so I don't need it but I'll experiment for the good of the people shortly.

---

### Post by jdbower on 2010-05-13
[One more thing to try]("http://www.nextwindow.com/nextwindow_support/app_working_under_linux_2.html"), from NextWindow directly.  Wish I was at my PC now to test it out myself :(

---

### Post by blade_fantasy on 2010-05-14
Dear jdbower, you wrote everything (except touchscreen & speakers) 
works well with fresh installation....

Also the Tv? (aver a323)

I have the 600-1050it model (italian)

Thanks

---

### Post by jdbower on 2010-05-14
Sorry, I don't have the TV tuner module (nor do I have cable/satellite TV - everything is streamed over the web for me these days) so I can't test that part.  I do, however, have an HDMI input but I haven't had the chance to try that under Windows let alone Linux.

---

### Post by jdbower on 2010-06-03
As an update, here's what I've learned:

**Works fine:**
Video - works acceptably out of the box, better with the NVidia proprietary driver.

Keyboard - works out of the box.

Mouse - reported to work out of the box (I use a Logitech MX which also works fine)

HDMI input - seems to be hardware based and continues to function.

Webcam - works out of the box.

**Works with quirks:**
Sound - works with external speakers out of the box.  Updating the ALSA driver from the Ubuntu 1.0.22 to 1.0.23 had no effect.  I use headphones most of the time anyway so I haven't played much.

Network - wired works out of the box, wireless has a workaround (although I haven't tried this myself)
> Add repositories:
deb [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu) karmic main
Then install rt3090-dkms

Keyboard light - seems to work but I haven't searched to see if I can change the color or control through software like I can via Windows.

**Plain old broken:**
Touchscreen - the biggest sticking point.  I played with the xorg.conf settings as described above in the NextWindow link but the config failed to parse on reboot.  I haven't tried to troubleshoot to see what the issue is there.  The nw-fermi driver is i386 only.  I added another partition (what did we do before gparted?) and installed Lucid-32 on it.  With the nw-fermi driver I was able to get the screen to respond to touch, but about once a second there was a random mouseclick someplace on the screen rendering the installation useless.  On reboot it seems to lock up one of the USB buses very quickly - networking, the OEM keyboard, and a few other things lock up but the external USB port hidden in the back works fine. 

This USB device is the Touchscreen in question:
> Bus 003 Device 004: ID 1926:0006 

I believe it showed up as /dev/input/event5 but I'm not positive about that (nor am I sure that this is a fixed value).

---

### Post by kdeguy on 2010-06-04
@jdbower:
Thanks for your info. This is really helpful so far.
I am wondering though whether you have tried the latest Ubuntu 10.04? If so, was there any improvement?

---

### Post by jdbower on 2010-06-05
All of this was on 10.04 - since it's an LTS version I don't see any reason to play with 9.10 (other than proper placement of the window control buttons, but that's another thread and I'm mostly used to it now...).

What I have't tried is the [Maverick Alpha-1]("http://cdimage.ubuntu.com/releases/maverick/alpha-1/"), but I may do so if I can find the time.

---

### Post by jdbower on 2010-06-05
Just FYI, I tried out Maverick Alpha 1 (32-bit) and so far no real change to behavior of the touchscreen.  I'm not a great choice for Alphas so I'm back to Lucid for my daily work.  Frankly the touchscreen is nice but trading it for Ubuntu (at least in the short term) may be worthwhile.

---

### Post by lidex on 2010-06-06
Have you tried this option in alsa-base.conf:
```
options snd-hda-intel model=touchsmart
```
I would surmise your best bet is using lucid with alsa 1.0.23

---

### Post by jdbower on 2010-06-06
Thanks for the tip.  I gave it a shot and saw no difference, but I'm not sure how good of a test system I've got anymore.  I may have been hit with [Bug 584822]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/584822") and to try to normalize my system I've downgraded back to ALSA 1.0.22 (on Lucid64).  When I boot to the previous kernel I do get sound, but your extra option doesn't seem to have an effect.  Using alsamixer I've noticed that the "headphone" output seems to be mapped to the "front panel" mixer setting.

The sound issue is a lower priority for me anyway, I use headphones most of the time so it's more of an undocumented feature.  Still, I'd be happy to capture any data that would be useful.

---

### Post by jdbower on 2010-06-06
Another update on the sound.  A fresh Lucid64 install yields anticipated results.  Adding "options snd-hda-intel model=touchsmart" to /etc/modprobe.d/alsa-base.conf didn't change anything.  [Upgrading to ALSA 1.0.23]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/") didn't fix it (I also needed to link a few libraries to get it to compile, as shown in [this previous version]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/")).  Removing the options line didn't change anything.  Under 1.0.23 I have noticed the following regarding the alsamixer:

1.  The headphone jack now responds to the Headphon mixer entry.
2.  Using the up arrow on the Front mixer entry changes it from 0 (the default) to 100 but reduces the Master volume to zero (which can then be raised and lowered normally).
3.  Using the down arrow on the Front mixer entry when it's at 100 will actually reduce the Master volume until the Master is at 0 at which point the Front volume will be reduced.
4.  Using Select Sound Card lists the card as "HDA NVidia"

I was actually able to upgrade the kernel in this install to the latest without killing the sound like I did with my main install.  This may be a weird interaction with some of the other stuff I've got (for example, no VirtualBox, XBMC, Humble Game Pack, etc. on the fresh install like on my main system). 

I've also noticed a bug in apt-get that vim is not recognized as a dependency for everything as it properly should be :P

---

### Post by zazi on 2010-06-06
Does anyone got the microphone to work? The sound works so far with 'model=touchsmart' option, but there is no external microphone channel.

Cheers

---

### Post by jdbower on 2010-06-06
> **zazi said:**
> The sound works so far with 'model=touchsmart' option, but there is no external microphone channel.

Interesting, which TouchSmart do you have?  Are you getting sound out of the speakers or just the headphone jack? Are you using the stock ALSA driver, the 1.0.23 or something else?

My microphone works fine under ALSA 1.0.23 (both the internal and input jack) but you'll need to change the mixer settings.  If you use alsamixer and then hit F4 you'll see the Capture screen.  The default capture volume is 0 (which you'll need to change), but the source should default to Mic (which seems to autoswitch from the input jack and the internal mic).

---

### Post by zazi on 2010-06-06
Hi,

I have the HP TouchSmart IQ512de. At the beginning I got over several month only sound over the headphone. During this time I tried it several times to solve this problem without any success. At the end I found this little option in the alsa devices text file, which works so far for me, but I have no microphone support yet. I run it with alsa 1.0.22 on a Ubuntu Lucid 64x installation. Maybe I should try the new version.
Nice to hear that it works at least. Thanks a lot for your suggestions.

Cheers,

---

### Post by jdbower on 2010-06-06
I wouldn't get too excited, my 600 series apparently has very different hardware from yours.  Still, the reason I upgraded to 1.0.23 is because the release notes mentioned additional TouchSmart support (without mentioning models) so maybe you'll get lucky.  Best of luck and happy Ubuntu-ing!

---

### Post by lidex on 2010-06-06
> **jdbower said:**
> I wouldn't get too excited, my 600 series apparently has very different hardware from yours.  Still, the reason I upgraded to 1.0.23 is because the release notes mentioned additional TouchSmart support (without mentioning models) so maybe you'll get lucky.  Best of luck and happy Ubuntu-ing!
You may get an answer contacting the alsa devs. Model options for the new support are not documented anywhere I've seen, but they would know if those exist.

---

### Post by zazi on 2010-06-06
I've updated now to alsa 1.0.23 without any change. Still no external microphone channel available.

Cheers

---

### Post by jdbower on 2010-06-06
Lidex has another good idea, I found [this regarding the IQ522]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4614") - probably the same hardware as the IQ512.  Searching the site with ALC888S turns up four issues, I'll have to scour through them to see if any are relevant (none are based on the TouchSmart implementation).

---

### Post by zazi on 2010-06-07
Hi, so far as I can see, is this the patch where they added the workaround for the touchsmart as a new value for the model option. I use this setting already. My sound card model is AD1984B.
However, thanks again for that hint, I'll decribe my problem there.

Cheers,

<edit>
I added the output of the alsa-info script, it seems that it haven't updated the alsa driver to 1.0.23. I remember that I had some compiling issues yesterday during the update process.
However, I think the solution might be an update of that touchsmart patch.
</edit>

---

### Post by ajstrobus on 2010-06-25
I hate to be rude but this thread is about "sound and touchscreen and wifi problems on a hp touchsmart 600-1050sc" if your hardware is the same thats one thing but if its completely different chipset please stop posting fixes for other computers, we're interested in a fix for alc888 touchsmart internal speaker problem which we await patiently as noone has posted a fix yet... 

My 2 cents worth is a codec dump of the codec shows nodeids of 20-12-2 for the headphones, & 21-13-3 for internal speakers, when ported to osx snow leopard sound also works great on headphones, lineout & mic. Maybe the nodeid's are wrong in the alsa driver for the internal speakers? might be wrong just thought id post it in case someone has some ideas... 

** -u can get your codec dump with cat /proc/asound/card0/codec#0 > ~/Desktop/codecdump.txt

---

### Post by lidex on 2010-06-27
Some other alsa-base.conf options to try:
```
options snd-hda-intel model=3stack-dig
options snd-hda-intel model=6stack-dig
options snd-hda-intel model=3stack-6ch
options snd-hda-intel model=3stack-6ch-dig
options snd-hda-intel model=3stack-hp
options snd-hda-intel model=auto
options snd-hda-intel index=0 model=toshiba position_fix=1
options snd-hda-intel model=toshiba position_fix=1
options snd-hda-intel model=zepto position_fix=1
```

Remember only one line at a time.

---

### Post by jdbower on 2010-08-12
Huzzah!

There's a new [nwfermi driver]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313/comments/65") that seems to support my HP TouchSmart 600.  The down side is that it's 32-bit only so I need to reinstall (I'm running off a small test partition as we speak).  Basic functionality seems to be there, but there's a long way for Ubuntu to go to get the "wow-factor" that a multitouch interface can provide.  Still, basic driver functionality is a good start.  

Now I'm off to see if there are any sound driver updates :)

---

### Post by jdbower on 2010-08-14
OK, here's a quick HowTo on getting Ubuntu Lucid installed on an HP TouchSmart 600-1xxx:

1.  Make sure you install the 32-bit version unless you've got experience with getting 32-bit stuff working on 64-bit systems.  The touchscreen driver is 32-bit only.

2.  Once you've got Ubuntu installed, marvel at how everything just works.  Except for the touchscreen, the wireless, and the sound card (which only plays through the headphones).

3.  First thing I do is a "sudo apt-get update; sudo apt-get upgrade" and then enable the enhanced Nvidia driver.  The driver is probably not needed but provides for a much better video experience.  I reboot after this to enable the driver, but the impatient may be able to continue without the reboot.

4.  One of the first things many people need to do is get the wireless working.  Personally I hate wireless on a desktop, I'd rather pull a cable, but the install is easy enough.  Unfortunately there is no PPA for Lucid, but there's a [HOWTO for building the driver]("http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/") including a [link to the driver]("http://stat.case.edu/~jrt32/how_to_build_rt3090_for_ubuntu_lucid/rt3090-dkms_2.3.1.4-0ubuntu0~ppa1_all.deb") for the lazy.

5.  Now the real magic - the touchscreen.  Deep in the bowels of [bug 379313]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313") comments is a link to a proprietary driver called [nwfermi]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313/+attachment/1455604/+files/nwfermi-0.2_i386.deb").  Install version 0.2 and you should be good to go.

6.  The sound card, sadly is not so easy as of now.  Headphones work fine, but I can't get the internal speakers to work at all.  Please track (and participate in) [bug 597056]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/597056") for updates.

Despite downgrading to the 32-bit release and not having sound I'm now comfortable enough to wipe my seldom-used Win7 partition. There is also a Launchpad blueprint for [better touchscreen support]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-touchscreen-handling").  I'm not sure how to help, but I figure subscribing is the first step.

---

### Post by jdbower on 2010-08-27
No new information (although there's some traction on the sound issue in the bug report listed above), but I've captured the installation instructions in a single document.  Let me know if you've got any questions or comments:
[http://www.ebower.com/docs/ubuntu-touchsmart/](http://www.ebower.com/docs/ubuntu-touchsmart/)

---

### Post by jdbower on 2010-09-06
A slight update to [my document]("http://www.ebower.com/docs/ubuntu-touchsmart/") to include Maverick support.  If you're getting errors installing the .deb involving usb_buffer_alloc or usb_buffer_free you'll have to build the module manually as I describe.

Sadly, from what I can tell no multitouch love for the TouchSmart 600 as of now. :(

---

### Post by Yumi on 2010-10-05
Any progress? I follow your interesting reports and am contemplating buying such a machine.

Michael

---

### Post by jdbower on 2010-10-05
Sorry, nothing too new to report.  There's been some efforts and attention on the sound front (see the bug reports listed above or in my doc), but nothing tangible as yet.  While I'm happy with the TouchSmart 600 and Ubuntu in its current state, as of now I'd probably recommend looking at the [uTouch supported hardware]("https://wiki.ubuntu.com/Multitouch#Hardware Support") if you want an out-of-the-box solution.  You have prompted me to create [bug 655169]("https://bugs.launchpad.net/ubuntu/+source/utouch/+bug/655169") to request uTouch support, hopefully anyone interested can help me gather the appropriate information or at least check the "this affects me" button.  I'll try to update my document with the details shortly.

---

### Post by lidex on 2010-10-05
> **jdbower said:**
> Sorry, nothing too new to report.  There's been some efforts and attention on the sound front (see the bug reports listed above or in my doc), but nothing tangible as yet.  While I'm happy with the TouchSmart 600 and Ubuntu in its current state, as of now I'd probably recommend looking at the [uTouch supported hardware]("https://wiki.ubuntu.com/Multitouch#Hardware Support") if you want an out-of-the-box solution.  You have prompted me to create [bug 655169]("https://bugs.launchpad.net/ubuntu/+source/utouch/+bug/655169") to request uTouch support, hopefully anyone interested can help me gather the appropriate information or at least check the "this affects me" button.  I'll try to update my document with the details shortly.
Have you tried maverick yet?

---

### Post by jdbower on 2010-10-06
> **lidex said:**
> Have you tried maverick yet?

Yes, sadly it's largely the same as Lucid as far as the TouchSmart 600 is concerned.  I haven't played too much with the RC, but at least as of the beta the current issues are all present.  Luckily the workarounds also work well (with slight modifications), so there's no step backwards.  As I mentioned above, the 10.10 multitouch packages don't support the nwfermi driver for the touchscreen yet but I've created a bug report.

---

### Post by jdbower on 2010-10-06
Just FYI, the nwfermi driver has been updated to 0.4 and now includes and amd64 version.  Check out djp's [comment 77]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313/comments/77") and [comment 78]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313/comments/78") for the download links.  It claims to support more devices as well as installations on Maverick kernels - I think the Maverick kernel and 64-bit support are most relevant to TouchSmart 600 users but I haven't had the chance to test either yet (and at this point I may as well wait for 10^3 to install the full release of Maverick).

Of course, [my document]("http://www.ebower.com/docs/ubuntu-touchsmart") has also been updated.

---

### Post by Yumi on 2010-10-06
We will see next week then. Interesting that there was a lot of posting back in August about Multi-touch in Maverick, but it has been very quite ever since.

On recent anouncement says
> The major improvements of Ubuntu 10.10 are in User Interface area, as Canonical&#8217;s work on the new Unity user interface. And Ubuntu come as the first Linux distribution that support multi touch gesture screen. And **this will ship with Ubuntu 10.10 netbook edition**.
does this mean Multi-touch only with netbook edition?

And this might be interesting reading and information
[http://www.omgubuntu.co.uk/2010/09/benjamin-gets-his-hands-on-the-apple-magic-trackpad/]("http://www.omgubuntu.co.uk/2010/09/benjamin-gets-his-hands-on-the-apple-magic-trackpad/")

Michael

---

### Post by jdbower on 2010-10-08
> **Yumi said:**
> does this mean Multi-touch only with netbook edition?

I'm not really sure what it means, to be honest.  I had to manually install the utouch package on the Desktop Edition, perhaps it gets installed automatically on the NetBook edition?  Or they were calling out that tablets would work better with the NBR?  Either way, there are some recommended "does your driver support multi-touch" programs and the TouchSmart screen didn't register.  On Sunday maybe I'll try both just in case.  

BTW, the Apple touchpad is in the supported hardware list if you'd like to play with it and Maverick gesture support.  Personally I don't find it overly magical, I use the mouse way too much to be able to switch to it and for "on the couch" stuff the [Logitech MX Air]("http://www.logitech.com/en-us/mice-pointers/mice/devices/3443") is a better solution for me.

---

### Post by Ayuthia on 2010-10-08
> **Yumi said:**
> We will see next week then. Interesting that there was a lot of posting back in August about Multi-touch in Maverick, but it has been very quite ever since.

On recent anouncement says

does this mean Multi-touch only with netbook edition?



They currently have the gestures library built and it seems to be working fine for certain devices.  You see some of the information [here]("https://wiki.ubuntu.com/Multitouch").

For the netbook edition, the Unity desktop does have some multitouch gestures built-in.  The normal Gnome and KDE desktop versions do not have anything as of yet.

As far as I know, your version of the Touchsmart is not currently working with it yet.  From what I understand, they need to be MT-capable.  What that means is that their kernel module code needs to be producing ABS-MT (the multitouch events) events.  Right now, there are only a handful of devices that do this.

---

### Post by jdbower on 2010-10-10
The final tally with Maverick 10.10 Desktop-64:

We're pretty much in the same state as with Lucid.  No change to the sound issue (no surprise - while the ALSA driver was updated from 1.0.22 to 1.0.23, manually updating the this version in Lucid didn't change anything).  The touchscreen is not active by default, but installing the nwfermi driver worked fine.  The wireless card is not auto-detected, I can only assume that building the driver as I've documented will still work (I haven't tested it out because wireless is for laptops!).  And, sadly, the driver is not multi-touch aware (or at least uTouch doesn't seem to register gestures).  I'll try to play a bit more tomorrow if I get the chance.

---

### Post by Andrew Golightly on 2010-11-13
I have the HP TouchSmart 600-1070a.

When I boot from the liveCD (I'm using Maverick 32bit), it begins to boot (I see the initial logo at the bottom of the screen), and then the screen goes black. Basically the video does not seem to be working at all. I hear the CD still whirring away and loading whatever else.. I just see a blank screen...

Most posts seem to say that at least the video works straight "out of the box".
Tips/advice??

---

### Post by Andrew Golightly on 2010-11-13
Turns out if I tick "nomodeset" on booting the liveCD, all seems to work.

The question now... is if I install it, do I need to do something to the grub config to make it do the nomodeset?? Or will installing the nvidia drivers sort everything out for moi??

---

### Post by faibistes on 2011-03-10
Everything is smooth here (Ubuntu Maverick- Touchsmart 600 1210de)... except external speakers. Any hints? I'm trying every snd-hda-intel model combination, to no avail.

---

### Post by lidex on 2011-03-17
> **faibistes said:**
> Everything is smooth here (Ubuntu Maverick- Touchsmart 600 1210de)... except external speakers. Any hints? I'm trying every snd-hda-intel model combination, to no avail.

Which output are you using? Have you tried adjusting levels in alsamixer?

---

### Post by spansite on 2011-03-23
Hello!

I have some problem with this model (HP TouchSmart 600 PC).

When I'm install ubuntu, I remove all Windows Files from computer. What I must to do to install Windows 7 back?

---

### Post by faibistes on 2011-03-24
> **lidex said:**
> Which output are you using? Have you tried adjusting levels in alsamixer?

Yes I have. This is the current state of the bug:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5308](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5308)

---

### Post by blade_fantasy on 2012-01-27
Alsa 1.0.25 driver are out.... Anyone tried to install them?

---

