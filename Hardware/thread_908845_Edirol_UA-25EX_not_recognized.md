---
title: "Edirol UA-25EX not recognized"
date: 2008-09-02
forum: Hardware
---

### Post by kb19 on 2008-09-02
Hey folks, I have just purchased this audio interface and cannot, for the life of me, get it to work. It shows up under lsusb but not when I do the whole cat /proc/sound/alsa (in which case only my onboard sound shows up). Does anyone have any suggestions? I read that this audio interface worked with ubuntu and it's really a pain to get it set up.  I'm running Ubuntu 8.04.

oh and it does not show up when I do System - Pref - Sound

thanks in advance

---

### Post by zaCh3puo on 2008-09-08
Hi,

> **kb19 said:**
> I [...] cannot, for the life of me, get it to work. It shows up under lsusb but not when I do the whole cat /proc/sound/alsa (in which case only my onboard sound shows up).


Does it work already?

I'm curious whether I should by this device, too.

---

### Post by uBeer on 2008-09-09
Same problem here. I thought I read somewhere that the ua-25 worked, but no success... Too bad, I'll just have to cope with a little less sound quality when I'm using Ubuntu...

---

### Post by CliffE on 2008-09-13
Hi all,

I too have just bought a UA-25EX, with only limited success so far (I'm running Debian with a 2.6.21 kernel but I thought my experiences might be useful to you).

In standard mode (set by flicking the switch on the back of the box) the UA-25EX is recognised and I can playback and record using ALSA and JACK, but only in 16 bit, 44.1KHz and no MIDI, due to the UA-25EX's limitations in standard mode.

In advanced mode the unit is recognised as a USB device, but not by ALSA. My current thinking is that the ALSA driver, snd-usb-audio, doesn't recognise the new product ID for the UA-25EX, which is different from the UA-25.

I'll post back any further successes here, as time permits.

Cliff.

---

### Post by blablack on 2008-09-17
Hi all,

Same problem here, only able to get Ubuntu to recognize the UA-25EX if the "Advanced Driver" switch is off.

Although, I found out this page about the UA-4FX and a really similar problem with the "Advanced Driver":
[http://alsa.opensrc.org/index.php/Edirol_UA-4FX#Getting_Advanced_mode_to_work]("http://alsa.opensrc.org/index.php/Edirol_UA-4FX#Getting_Advanced_mode_to_work")

May be it is "as simple as" creating a similar patch for the UA-25EX.

I'll have a look as soon as I have some free time.

Cheerio,
Aurélien

---

### Post by blablack on 2008-09-18
Hey guys,

I modified the patch from the link in my previous message.
I made the soundcard work, but may be it needs some improvements...

```
Add Alsa support for Roland Edirol UA-25EX in Advanced mode
(for MIDI support and sample rates of 48 kHz and 96 kHz)
usbquirks.h
===================================================================
diff -u sound/usb/usbquirks.h.00 sound/usb/usbquirks.h
--- sound/usb/usbquirks.h.00	2007-11-28 02:15:11.000000000 -0700
+++ sound/usb/usbquirks.h	2007-11-28 02:17:51.000000000 -0700
@@ -1311,6 +1311,37 @@
 	}
 },
 	/* TODO: add Edirol MD-P1 support */
+{	/*
+	 * This quirk is for the "Advanced" modes of the Edirol UA-25EX.
+	 * If the switch is not in an advanced setting, the UA-25EX has
+	 * ID 0x0582/0x00a4 and is standard compliant (no quirks), but
+	 * offers only 16-bit PCM at 44.1 kHz and no MIDI.
+	 */
+	USB_DEVICE_VENDOR_SPEC(0x0582, 0x00e6),
+	.driver_info = (unsigned long) & (const struct snd_usb_audio_quirk) {
+		.vendor_name = "EDIROL",
+		.product_name = "UA-25EX",
+		.ifnum = QUIRK_ANY_INTERFACE,
+		.type = QUIRK_COMPOSITE,
+		.data = (const struct snd_usb_audio_quirk[]) {
+			{
+				.ifnum = 0,
+				.type = QUIRK_AUDIO_EDIROL_UA700_UA25
+			},
+			{
+				.ifnum = 1,
+				.type = QUIRK_AUDIO_EDIROL_UA700_UA25
+			},
+			{
+				.ifnum = 2,
+				.type = QUIRK_AUDIO_EDIROL_UA700_UA25
+			},
+			{
+				.ifnum = -1
+			}
+		}
+	}
+},
 {
 	/* Roland SH-201 */
 	USB_DEVICE(0x0582, 0x00ad),

```

Let me know anyway...

Aurélien

---

### Post by blablack on 2008-09-19
Hello guys,

Created a wiki page about the Edirol UA-25EX on the Alsa Wiki:
[http://alsa.opensrc.org/index.php/Edirol_UA-25EX]("http://alsa.opensrc.org/index.php/Edirol_UA-25EX")

Hope it helps!

Aurelien

---

### Post by CliffE on 2008-09-19
Thanks for your efforts, Aurelien, I'll give it a go once I've figured out how!

Cliff.

---

### Post by gilson.beck on 2008-10-01
Hello all.

I bought the Edirol UA25EX sound card and I'm trying to make it work in advanced mode. I would like to work with jack.

So, I'm very dumb in linux configuration (I'm a simple audio user, not a good configurer).
When I give the command "$diff -u sound/usb/usbquirks.h.00 sound/usb/usbquirks.h", terminal said that this files don't exist. $cat /proc/bus/usb/devices said file or directory don't exist.

Can someone make some "step by step" guide?
If so, I can try to test anything.

Thanks a lot.

Gilson.
Ubuntu 8.04 - kernel 2.6.24-19-rt - GNOME 2.22.3
Acer Aspire 5610 - 2gb ram.

---

### Post by blablack on 2008-10-02
Hello Gilson,

Unfortunately, to be able to make the UA-25EX work, you will have to recompile your kernel. It is a fastidious task, but you can find very good articles that explains how to do it:
[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

To apply the patch I created, once you have the kernel source, go to the directory:
```
cd /usr/src/linux/sound/usb
```

and apply the patch there.

Ensure when you compile your kernel to activate the module snd-usb-audio

Hope this help you a bit.

---

### Post by jhmos on 2008-10-06
Thanks for the patch, although I have not got it working on my first attempt, will try again when I get a chance.
Its a bit of a pain to patch the kernel and get everything else working (like the NVIDIA driver) each time there is a kernel update. I see that the patch has not made it into the 2.6.27 kernel version in the Ubuntu 8.10 beta. Any idea how long it would be to at least get the patch accepted into a standard kernel? Would it go through the ALSA maintainers?

---

### Post by [censored] on 2008-10-21
Hey I can't even get it to operate in basic mode. 

According to the wiki page at [http://alsa.opensrc.org/index.php/Edirol_UA-25EX](http://alsa.opensrc.org/index.php/Edirol_UA-25EX) it's supposed to just show up in /proc/asound/cards, but there's nothing there.

When I do lsusb, however, I get 

>  Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0582:00e6 Roland Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 045e:0008 Microsoft Corp. SideWinder Precision Pro
Bus 001 Device 004: ID 15d9:0a37  
Bus 001 Device 001: ID 0000:0000  


So I know it should be there.

What should I do? I would like to get some recording done.

---

### Post by blablack on 2008-10-21
Did you try to unplug the UE-25EX, set the it to Basic Driver and then replug it.

Ubuntu or at least the usb-audio alsa module doesn't pick up when you change the Driver from Basic to Advanced with letting the card plugged...

Hope that helps, because I didn't have any problem to make it work in Basic Mode.

---

### Post by Joan Quintana on 2008-10-21
I'm ready to compile my kernel.
My kernel is from Ubuntu Studio (/usr/src/linux-headers-2.6.22-15-rt), who is  tuned for real-time operations.
under the folder /usr/src/linux-headers-2.6.22-15-rt/asound/usb I don't see usbquirks.h file.
It seems that the patch is for Debian with a 2.6.21... How to proceed?...

Thanks in advance,
Joan Quintana

---

### Post by blablack on 2008-10-21
I only applied the patch on the kernel 2.6.24, 2.6.26 and 2.6.27.

In 2.6.24, everything works fine even with RT enabled.

2.6.26, if the kernel is compiled with the RT option, Jackd will crash as soon as you try to use midi with the UA-25EX. Couldn't find out what the problem was...

2.6.27, RT is not available yet... But it works fine otherwise.

Your best option would be to upgrade the kernel to at least 2.6.24.

By the way, I use and created the patch under Ubuntu Studio too, so it is supposed to work ok...

Hope this helps !

---

### Post by [censored] on 2008-10-21
> Did you try to unplug the UE-25EX, set the it to Basic Driver and then replug it.

yah. Thanks, I tried that and it worked. But the strange thing was that it was already set on Basic Driver. So I unplugged it, set it to Advanced, then replugged it. Then unplugged it again, and set it to Basic, then replugged it, and now I'm able to record and play. Weird.

For some reason though, I get copious, ridiculous numbers of xruns using jack. So many that the system is unusable. If anybody knows how to set jack, or qtjackctrl for this USB device, please let me know the trick.

---

### Post by blablack on 2008-10-21
> For some reason though, I get copious, ridiculous numbers of xruns using jack. So many that the system is unusable. If anybody knows how to set jack, or qtjackctrl for this USB device, please let me know the trick.

Once you get it to work with the Advanced Driver, you will get less xruns... In addition, a properly recompiled kernel helps a lot.

Using Ubuntu Intrepid, kernel 2.6.27 with the Low Latency Scheduler and the patch for the UA-25EX, I get almost no xrun.

---

### Post by [censored] on 2008-10-22
Blablack, thanks an awful lot for the advice, but how do I apply this patch of yours? I've been looking through [the article you cited]("https://help.ubuntu.com/community/Kernel/Compile#Modify%20the%20source%20for%20your%20needs"), and I've got as far as getting the source for linux-image-2.6.24rt, but it doesn't seem to explain how I apply patches.

Do I save it as a file in linux-2.6.24/sound/usb ? 

If so, what do I call it? 

Also, am I supposed to pass some kind of command in the terminal after I save it?

Also, if you've got a moment,  how do I ensure that I compile my "kernel to activate the module snd-usb-audio"?

---

### Post by blablack on 2008-10-22
Hello [Censored]

I'm not in front of my computer right now, so i'll try to remember as much information as I can.

To apply the patch, copy the file into the sound/usb directory of the kernel source, go to the directory sound/usb then use this command:
```
patch < PatchUA25EX
```
where PatchUA25EX is the patch file.

Once that's done, run this command:
```
make gconfig
```
to access the kernel options, go to Device Driver->Sound->Alsa->USB and activate the module USB-Audio.

(again, I'm not in front of my computer, so it might not be the exact name and stuff, but i'm sure you'll find it pretty easily)

Finally, if you never compiled a kernel yourself, I would advise you to check this page:
[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

---

### Post by Joan Quintana on 2008-10-23
Hello,
I already installed Ubuntu Studio 8.04 (2.6.24), applied the patch for Advanced Mode i Edirol UA-25EX, with rt flavour. I think that everyting is all right.

But when I inserted my new Edirol UA-25 EX in advanced mode or normal mode, the first attempt is wrong.

$ cat /proc/asound/cards
cat: /proc/asound/cards: file or folder doesn't exist

I suppose that I made a mistake compiling the kernel
I followed step by step 
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
tutorial, and everything was OK, I think

Any ideas?

Joan Q

---

### Post by blablack on 2008-10-23
Hey Joan,

May be it has something to do with this:
[http://alsa.opensrc.org/index.php/Proc_asound_documentation]("http://alsa.opensrc.org/index.php/Proc_asound_documentation")

But I'm not 100% sure...
May be a module missing in the filesystem area, or one missing in the Alsa part.

/proc/asound/cards should at least exist and display your already existing card...

---

### Post by [censored] on 2008-10-23
> **blablack said:**
> Hello [Censored]

...... run this command:
```
make gconfig
```
to access the kernel options, go to Device Driver->Sound->Alsa->USB and activate the module USB-Audio.

Those precise options weren't there when the GUI popped up. So what I did instead was: I went to Device Drivers -> Sound -> Advanced Linux Sound Architecture -> USB Devices, double clicked USB Audio/Midi Driver (New). I then selected Save, and quitted the gui app. Is that close enough?

 > **blablack said:**
> 
(again, I'm not in front of my computer, so it might not be the exact name and stuff, but i'm sure you'll find it pretty easily)

Understood. Thanks for your time and effort.

> **blablack said:**
> 
Finally, if you never compiled a kernel yourself, I would advise you to check this page:
[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

I have been following that page very faithfully. 

I perform the make gconfig in the [https://help.ubuntu.com/community/Kernel/Compile#Modify%20the%20source%20for%20your%20needs]("https://help.ubuntu.com/community/Kernel/Compile#Modify%20the%20source%20for%20your%20needs") part of the howto. I always get this error after I perform the recommended "debian/rules updateconfigs"...

```
Running splitconfig.pl ... 

debian/scripts/misc/oldconfig: line 66: /home/reksub/downloads/kernel/src/linux-2.6.24/debian/scripts/misc/splitconfig.pl: Permission denied
make: *** [updateconfigs] Error 1

```

I then attempt to do "$AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-rt" I get this error ...

```
Using /media/disk3/stuff/wombatfiles/downloads/kernel/src/linux-2.6.24/debian/build/custom-source-rt as source for kernel
  /media/disk3/stuff/wombatfiles/downloads/kernel/src/linux-2.6.24/debian/build/custom-source-rt is not clean, please run 'make mrproper'
  in the '/media/disk3/stuff/wombatfiles/downloads/kernel/src/linux-2.6.24/debian/build/custom-source-rt' directory.
make[4]: *** [prepare3] Error 1
make[3]: *** [sub-make] Error 2
make[2]: *** [prepare] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/media/disk3/stuff/wombatfiles/downloads/kernel/src/linux-2.6.24/debian/build/custom-source-rt'
make: *** [/media/disk3/stuff/wombatfiles/downloads/kernel/src/linux-2.6.24/debian/stamps/stamp-custom-prepare-rt] Error 2
```

Anyone have any idea where I might be going wrong?

---

### Post by [censored] on 2008-10-25
I guess the answer to that is no.

Can anyone recommend a better usb sound card?  better = one that I can easily use with linux?

---

### Post by blablack on 2008-10-26
Hello [Censored],

The UA-25EX works perfectly with Linux, and it is always useful to know how to recompile a kernel :-)

I'll try to help the best I can:

> Those precise options weren't there when the GUI popped up. So what I did instead was: I went to Device Drivers -> Sound -> Advanced Linux Sound Architecture -> USB Devices, double clicked USB Audio/Midi Driver (New). I then selected Save, and quitted the gui app. Is that close enough?
Yes, that's the module I meant.

The error you get recompiling the kernel... Well it seems to be a bit my fault. The article I advised you to follow is REALLY detailed, but you don't need 3/4 of the information...

First thing first, I would decompress the archive you got for the kernel 2.6.24 into the directory /usr/src. It is where kernel sources are supposed to be.

Once you set up the kernel option using make gconfig and that everything seems to be ok, run this command AS THE ROOT at the root of the kernel source (/usr/src/linux-2.6.24):
```
CONCURRENCY_LEVEL=2 make-kpkg --initrd kernel_image kernel_headers
```

Once the compilation is done, install the kernel (still running those commands as root):
> cd /usr/src
dpkg -i *.deb

"Normally" everything should work ok, but don't be surprise if you get compilation errors the first time or if you computer behaves strangely after running the kernel. It is rare to get it right the first time !

But whatever errors you get, don't hesitate to ask the question here or google it a bit. You always get somebody else who got the exact same error as you do!

Good luck!

---

### Post by jhmos on 2008-10-27
After you get the kernel source installed, this is what worked for me (the -edirol is optional):
cd /usr/src/linux-source-2.6.24
sudo make-kpkg clean
sudo fakeroot make-kpkg --initrd --append-to-version=-edirol kernel-image kernel-headers

After that, you should have a couple of debian package files in /usr/src. In my example they are named: linux-headers-2.6.24.3-edirol_2.6.24.3-edirol-10.00.Custom_i386.deb
linux-image-2.6.24.3-edirol_2.6.24.3-edirol-10.00.Custom_i386.deb

Its those files you install with dpkg -i

---

### Post by jhmos on 2008-10-27
I don't have any hardware to test Midi functionality. Has anyone given the UA-25EX a good workout using Midi and all?
Just that I'm contemplating making an Ubuntu launchpad bug report that points to the patch, since no one else has yet.
I don't really want to forever have to manually install a bunch of restricted drivers (like NVIDIA) and other stuff every time there is a kernel update.
I guess we might get it quicker than a Ubuntu release if the patch could get into a stable kernel. What are the chances of that?

---

### Post by blablack on 2008-10-27
Hello Jhmos,

I have tested the MIDI part of the UA-25EX extensively and it seems to work ok with:
- 2.6.24 rt
- 2.6.26
- 2.6.27

But as soon as you use Midi with 2.6.26 rt, Jack crashed. Though I think the problem seems to come from Jack or the RT patch.
I couldn't test it on 2.6.27 yet as I don't think the RT patch is available.

What is the next step if we want the patch to be included into ALSA?

---

### Post by jhmos on 2008-10-27
Hi blablack,
I was hoping you knew, I was not even sure who the maintainer was that the patch would have to go through.
I will do some homework looking for the ALSA development list.
From the little I know of kernel patches, device driver patches tend to be more readily accepted and with a bit of luck might get into a 2.27.x kernel (which would apply to Ubuntu 8.10). If I bothered to read the linux kernel mailing list I might have a clue but I haven't done that for years (or had a clue :-).

Regards,
John.

---

### Post by jhmos on 2008-10-28
Looking for who has been most closely involved with submitted edirol patches lately, I found this extract from a recent git merge request:

[ALSA PATCH] alsa-git merge request
From: Jaroslav Kysela
Date: Fri Oct 10 2008 - 08:43:26 EST
...

Pedro Lopez-Cabanillas (2):
ALSA: snd-usb-audio: support for Edirol UA-4FX device
ALSA: usb-audio: dynamic detection of MIDI interfaces in uaxx-quirk

...

The principle ALSA developers are listed on [http://www.alsa-project.org/main/index.php/Alsa_Team]("http://www.alsa-project.org/main/index.php/Alsa_Team")

Maybe Pedro would be worth contacting to liaise with regarding a patch submission?

---

### Post by jhmos on 2008-11-03
Hey,
This is in ChangeLog-2.6.28-rc3 ! :-)

commit e2736261b4c85e36f7c8a66dd082ec0751230460
Author: Takashi Iwai <tiwai@suse.de>
Date:   Mon Oct 20 16:07:45 2008 +0200

    ALSA: usb - Add quirk for Edirol UA-25EX advanced modes
    
    Added the quirk for UA-25EX advanced modes.
    UA-25EX is almost compatible with UA-25.
    
    Tested-by: Serge Perinsky <sergebass@gmail.com>
    Signed-off-by: Takashi Iwai <tiwai@suse.de>

So it will at least be in the 2.6.28 kernel and hopefully will be into Intrepid at some time.

---

### Post by jhmos on 2008-12-08
I installed Jaunty alpha 1 on a test partition, since it uses a 2.6.28 release canditate. Audacity at least can see the UA-25EX and could successfully record with it. Have not tried much else yet but its a good start.

---

### Post by uBeer on 2009-01-20
Alsa 1.0.19 has been released and I noticed that the card should work in advanced mode as well (some quirks added, mentioned in the previous posts). Hope to see 1.0.19 in Jaunty :D

---

### Post by blablack on 2009-01-21
Yes, I checked the code of the kernel 2.6.28 and it seems to be really similar to the patch I created for alsa for the previous version of the kernel...

Great news so ! That means no need to patch the kernel every time a new version is released !

---

### Post by andjarnic on 2009-01-29
Hey all,

I've been reading all these posts... still trying to figure out how to get this stuff working.

Basically I just gave up my Windows "studio" setup with lots of good software to move to Ubuntu STudio. After some reading, it seemed 8.04 RT was the way to go over 8.10. I am overjoyed to see that the UA25EX is supported... to some degree.

I figured out my ALSA version is 1.0.16 and kernel is 2.6.24 x64 (intel quad core cpu). I'd really like to have ALSA 1.0.19. Is there any way I can get this while still having the 8.04 RT kernel?

Also, from what I've read, it seems that JACK is better suited for low latency audio? If this is true, can/is the Ediroal UA25EX capable of working with JACK at 24-bit in/out (48/96Khz) with low latency "comparable" to that of Windows? Please point me to how to get this working if it is doable.

I'm relatively new to all this lower level stuff. I've played with linux a bit here and there, but never beyond basic CLI and mostly GUI stuff, primarily java server stuff.

I also have a Edirol PCR-300 MIDI controller keyboard. I haven't plugged it in yet..it's USB based as well. Any chance this will work.. or is there going to be issues with USB controller keyboards? Do they support using MIDI over them.. or am I better off plugging my keyboard into the USB jack on my UA25EX and using that (and if so..does that work)?

Last question.. I was using software like SoundForge, Melodyne for vocals, Reaper, Reason 4, and Ableton Live on Windows. All good solid stuff. I know Audicity is pretty good.. although it's a bit quirky just yet for me. I've briefly looked at some of the apps, like the Ardour multi-track software.. all of it is pretty cryptic thus far. So.. what is the "best" software to replace Ableton Live and Reaper? Is there anything like Melodyne that can do solid vocal pitch shifting without the chipmunk effect for linux? For photos I see Gimp is solid.. I've used it.. again it's a bit awkward just yet, but should do the trick. The last one is Video editing. I saw Kino but it looks pretty vanilla. Is there an open-source Adobe PRemiere or Pinnacle STudio quality app that has effects and such with A/B timelines, transitions, etc? Oh yah.. and what about encoders/decoders for h.264, mpeg2, etc?

Sorry about the off-topic, be happy to have messages sent via the forum instead of posting here. I'm very excited to be off of windows and am really just eager to get my music studio going in the right direction as much as I can with Ubuntu Studio.

Thank you.

---

### Post by blablack on 2009-01-29
Hello Andjarnic,

I don't know what is the kernel version in 8.04 RT...
But below 2.6.28, the UA-25EX is not recognize directly...

Check with the commande ```
uname -r
``` what's the version of your kernel...

About your other questions, JACK is a really important component of creating music with Linux. It is definitely comparable to the low latency in Windows, and a lot of functionality are really useful (synchronizing application for example).

About your USB Keyboard, it should work... When I got mine, just plugged it into USB, started Jack and it automatically detected a new Midi Device. No need to set up anything...

About the softwares:
- Ardour: pretty powerful DAW.
- Hydrogen: excellent drum-machine
- Rosegarden

Personally, I use as well Seq24 (excellent sequencer), SooperLooper and Alsa Modular Synth.

But it is all a question of personal choice and try to see which ones suit your needs.

Finally, about the encoders/decoder... Well you will have to do your own reseach with Google :-) Not that I don't want to help you at all, but it depends what you need them for...

Hope that helped you a bit!
Aurélien

---

### Post by jher6334 on 2009-02-04
Instructions to make Edirol UA-25EX work with advanced driver in Ubuntu Hardy 8.04 LTS.

1. Create the work dir. It is safe to remove it after installation
```
~$ mkdir kernel-custom-modules
~$ cd kernel-custom-modules
```

2. Download below patch and save it with filename "edirolua25expatch" into previously created dir "kernel-custom-modules"
```
Add Alsa support for Roland Edirol UA-25EX in Advanced mode
(for MIDI support and sample rates of 48 kHz and 96 kHz)
usbquirks.h
===================================================================
diff -u ubuntu/sound/alsa-kernel/usb/usbquirks.h.00 ubuntu/sound/alsa-kernel/usb/usbquirks.h
--- ubuntu/sound/alsa-kernel/usb/usbquirks.h.00	2007-11-28 02:15:11.000000000 -0700
+++ ubuntu/sound/alsa-kernel/usb/usbquirks.h	2007-11-28 02:17:51.000000000 -0700
@@ -1311,6 +1311,37 @@
 	}
 },
 	/* TODO: add Edirol MD-P1 support */
+{	/*
+	 * This quirk is for the "Advanced" modes of the Edirol UA-25EX.
+	 * If the switch is not in an advanced setting, the UA-25EX has
+	 * ID 0x0582/0x00a4 and is standard compliant (no quirks), but
+	 * offers only 16-bit PCM at 44.1 kHz and no MIDI.
+	 */
+	USB_DEVICE_VENDOR_SPEC(0x0582, 0x00e6),
+	.driver_info = (unsigned long) & (const struct snd_usb_audio_quirk) {
+		.vendor_name = "EDIROL",
+		.product_name = "UA-25EX",
+		.ifnum = QUIRK_ANY_INTERFACE,
+		.type = QUIRK_COMPOSITE,
+		.data = (const struct snd_usb_audio_quirk[]) {
+			{
+				.ifnum = 0,
+				.type = QUIRK_AUDIO_EDIROL_UA700_UA25
+			},
+			{
+				.ifnum = 1,
+				.type = QUIRK_AUDIO_EDIROL_UA700_UA25
+			},
+			{
+				.ifnum = 2,
+				.type = QUIRK_AUDIO_EDIROL_UA700_UA25
+			},
+			{
+				.ifnum = -1
+			}
+		}
+	}
+},
 {
 	/* Roland SH-201 */
 	USB_DEVICE(0x0582, 0x00ad),
```
I have just updated patch paths to fit ubuntu modules tree dir. Original path can be found in [http://alsa.opensrc.org/index.php/Edirol_UA-25EX]("http://alsa.opensrc.org/index.php/Edirol_UA-25EX")

3. Install all the necessary compiling packages
```
~/kernel-modules$ sudo apt-get install linux-kernel-devel fakeroot build-essential
~/kernel-modules$ sudo apt-get build-dep linux
```

4. Download and prepare the kernel-modules
```
~/kernel-modules$ sudo apt-get build-dep linux-ubuntu-modules-$(uname -r)
~/kernel-modules$ apt-get source linux-ubuntu-modules-$(uname -r)
```

5. Patch
```
~/kernel-modules$ cd linux-ubuntu-modules-2.6.24-2.6.24
~/kernel-modules/linux-ubuntu-modules-2.6.24-2.6.24$ patch -p0 < ../edirolua25expatch
```

6. Compile and generate .deb for the RT (real time) kernel (if you are using it). If you use another kernel just replace "binary-modules-rt" by "binary-modules-<kerneltype>". E.g. for the generic kernel put "binary-modules-generic" instead of "binary-modules-rt". In order to compile the modules for all the kernel types just write "binary-debs" instead of "binary-modules-rt". The CONCURRENCY_LEVEL is related to the amount of cpus/cores in your computer, 2 in my case (dual core). You can avoid it without any risk.
```
~/kernel-modules/linux-ubuntu-modules-2.6.24-2.6.24$ CONCURRENCY_LEVEL=2 AUTOBUILD=1 fakeroot debian/rules binary-modules-rt
```

7. Supposing everything was OK, install the created linux-ubuntu-modules .deb
```
~/kernel-modules/linux-ubuntu-modules-2.6.24-2.6.24$ cd ..
~/kernel-modules$ sudo dpkg -i linux-ubuntu-modules-2.6.24-23-rt_2.6.24-23.36_amd64.deb
```

8. Enjoy and may the music be with you ;)

---

### Post by rlameiro on 2009-02-09
Well, I am not A linux geek, but in another post we have managed to patch the alsa driver. [http://ubuntuforums.org/showthread.php?t=1043691]("http://ubuntuforums.org/showthread.php?t=1043691") 
I put my ua-4fx working, without recompiling the kernel, just the modules/alsa driver. go to the post to see an easy way to do this only compiling alsa drivers and the kernel headers. I am thinking in make a python script that does all of this in an automated way, I can put the 3 patches, the ua4fx, ua 25 and ua-25ex.

Can anyone try this way? just to see if it works? remeber to use the ua25ex patch and not the ua24fx :)

---

### Post by manysounds on 2010-01-27
Here's a bit of weirdness-

In a fresh karmic, fully updated with nothing but media codecs installed:

My UA-25ex works fine on my EEEPc 900 in normal and advanced mode

My UA-25ex hangs my audio system on my Acer X3200 in both modes

Something with the NVidia subsystems?

---

