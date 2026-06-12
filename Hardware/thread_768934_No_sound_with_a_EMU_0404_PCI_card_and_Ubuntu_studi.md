---
title: "No sound with a EMU 0404 PCI card and Ubuntu studio 8.04"
date: 2008-04-26
forum: Hardware
---

### Post by zob on 2008-04-26
Hi.

If anyone can help me with this, they will make me very happy. And help me throw away windows once and for all. 

I'm having problem with getting sound from my EMU 0404 PCI card. I've heard a lot of people have it working, so I don't understand.

It seems the drivers don't load properly. I will just go ahead and post all the info I can think of could be useful to find a solution for this. So, here goes...

Fx. the output of
```
 cat /proc/asound/cards

 1 [K61e           ]: USB-Audio - Keystation 61e
                      Evolution Electronics Ltd. Keystation 61e at usb-0000:00:02.2-1.4, full speed

```

Only a UBS/MIDI keyboard from M-audio shows up - this is NOT an audio card.

More outputs - this time lspci -nn

```
lspci -nn

00:00.0 Host bridge [0600]: nVidia Corporation nForce3 250Gb Host Bridge [10de:00e1] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation nForce3 250Gb LPC Bridge [10de:00e0] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation nForce 250Gb PCI System Management [10de:00e4] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation CK8S USB Controller [10de:00e7] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation CK8S USB Controller [10de:00e7] (rev a1)
00:02.2 USB Controller [0c03]: nVidia Corporation nForce3 EHCI USB 2.0 Controller [10de:00e8] (rev a2)
00:05.0 Bridge [0680]: nVidia Corporation CK8S Ethernet Controller [10de:00df] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation CK8S Parallel ATA Controller (v2.5) [10de:00e5] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation CK8S Serial ATA Controller (v2.5) [10de:00ee] (rev a2)
00:0a.0 IDE interface [0101]: nVidia Corporation CK8S Serial ATA Controller (v2.5) [10de:00e3] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge [10de:00e2] (rev a2)
00:0e.0 PCI bridge [0604]: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge [10de:00ed] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AP [Radeon 9600] [1002:4150]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) [1002:4170]
02:09.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 03)

```

I'm not really sure what to look for here, but I guess that SB Audigy might have something to do with my EMU card, so this might actually be OK.

Now moving on, it starts to look worse:

```
dmesg |grep emu

[   34.652574] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   39.296101] scsi4 : SCSI emulation for USB Mass Storage devices
[   60.519108] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:822: emu1010: Special config.
[   60.519192] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:861: emu1010: EMU_HANA_ID=0x7f
[   60.519196] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:880: emu1010: filename emu/emu0404.fw testing
[   61.922889] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:681: firmware: emu/emu0404.fw not found. Err=-2
[   61.922898] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:885: emu1010: Loading Firmware file emu/emu0404.fw failed

```

As you see it doesn't find the firmware and so it doesn't load. Now it makes sense that I have no sound. But what might be the reason??

More symptoms... When I do this...
```
 alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

And the following...
```
aplay -l

**** List of PLAYBACK Hardware Devices ****

```

And nothing is listed.

Last thing... When I go...

```
sudo lshw -C multimedia

 *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=20 mingnt=2

```

I'd appreciate any help, thanks.

---

### Post by zob on 2008-04-27
Bump and:
I'm starting to worry that this is a general problem in 8.04 there's a lot of sound card problem post around today.

Anyway, as far as I can see, I'm one of the few who's not even able to start the alsamixer, because the driver doesn't load it seems.

My hardware, as is the case with the other sound card problems in this forum today, does get recognized. But in my case the driver doesn't load. There should be support for my EMU 0404 PCI sound card in this alsa version.

Why can this be? Please help.

---

### Post by zob on 2008-04-28
I had (to get a glimpse of the new KDE4) also downloaded the Kubuntu KDE4 Remix along with ubuntu studio. So, last night I tried to do a fresh install of that. The result was unfortunately exactly the same. Same output to the same commands.

So, not having gotten any closer to a solution, here's another Bump.

---

### Post by zob on 2008-04-28
As it seems no one can help, I'll just have a conversation with myself.

I am however very interested in experiences with current alsa version and EMU0404 - I suspect ALSA to be the "problem", because lspci and lshw sees the EMU hardware very well, but as soon as ALSA gets into the picture it starts failing.

Just did some testing with Knoppix Live-DVD (which is actually very cool with Compiz working on my rather old PC) version 5.3.1.
I has the same (current 1.0.16) ALSA version as Hardy, which should support the EMU 0404 PCI card.

The (disappointing) results are more or less the same as the ones I get with Hardy.

And this also shows up somewhere in my dmesg:
EMU10K1_Audigy: probe of 0000:02:09.0 failed with error -5

So here's another bump.

Remember I'm also interested in knowing if anyone has a working EMU-card in Hardy (or anywhere else with the 1.0.16 ALSA version).

Thanks.

---

### Post by srrr on 2008-05-01
As I found out with my E-MU 1616m: the alsa-firmware package is simply not shipped with Ubuntu.

You can perhaps use the one I used
[http://ppa.launchpad.net/tsmithe/ubuntu/pool/main/a/alsa-firmware/?C=S;O=D](http://ppa.launchpad.net/tsmithe/ubuntu/pool/main/a/alsa-firmware/?C=S;O=D) ,
this is not the new version from alsa (16), but the older one (15).

Or follow the instructions on [https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard](https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard) and compile the newest alsa-firmware package yourself.

(As you use Ubuntu-Studio, first try to find the package alsa-firmware in Synaptic, in Ubuntu it's not there, but in the studio version it could be different.)

---

### Post by zob on 2008-05-01
Thanks a lot srrr.

I'm afraid it didn't cure my system. I tried the .deb-package from tsmithe (the easy way). All the commands I mentioned before give the same output, except for dmesg which i slightly different but with the same kind of firmware error:

```
dmesg |grep emu
[   34.796399] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   40.182896] scsi6 : SCSI emulation for USB Mass Storage devices
[   59.441889] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:822: emu1010: Special config.
[   59.441973] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:861: emu1010: EMU_HANA_ID=0x7f
[   59.441978] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:880: emu1010: filename emu/emu0404.fw testing
[   61.714788] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:684: firmware size=0xd67c
[   66.548843] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:893: emu1010: Loading Hana Firmware file failed, reg=0x7f

```

Maybe I'm just to stupid to use linux. I guess I'll have to roll back to windows XP. Thanks though.

---

### Post by srrr on 2008-05-01
Can't help you directly now, but go here:
[https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1#comments](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1#comments)
and read, read, read :D... solution will be there. (Ignore much of the first comments, they are very old.)

---

### Post by zob on 2008-05-01
Thanks a lot srrr!!! That's very informative. I've posted my outputs there.

I does seem however, that a lot of people is having the same problem, and that no one really finds the answer.

I think, if I didn't misunderstand him, that someone suggested that there is some kind of hardware incompatibility in the first shipping of the 0404 PCI (that would include mine). I do hope he's mistaken.

But we'll see, thanks again.

---

### Post by tuxulin on 2008-08-20
im having this exact situation.

i have a emu 0404 that does not work plus i have the identical errors, logs, lshw, dmesg |grep emu, lspci -nn and dmesg response as shown by the poster of this thread.

i have to resort to my on board card to get sound.

i was wondering if there has been any progress with an appearance of a emu 0404 firmware file for linux as i too would love to use my card again or are there any 0404 users out there that can write a blow by blow on how to
get this card running.

Thanks
Tuxulin

---

### Post by zob on 2008-08-20
I'm afraid that our 0404 will not work ever. The problem seems to be that there was a first shipping 0404 with different firmware. Because it is working most people by now. I deduce that, the few of us who cannot get it to work have older versions of the card or something. Look the thread mentioned earlier:
[https://bugtrack.alsa-project.org/wi...nts=1#comments](https://bugtrack.alsa-project.org/wi...nts=1#comments)

I, at least, have followed all the different 0404 guides by now and I've not got any sound at all. If you've got the latest alsa version and it still doesn't work - forget it.

But if you manage to prove me wrong, I'm very interested (and I'll be very happy).

---

### Post by jpumphandle on 2008-08-24
I also have an EMU 0404 PCI card. So far no luck with directions on how to get it working. I made some progress tho ... Using these directions from the ALSA Wiki ...

[I]I'll try to help:

dl the latest alsa-driver / lib from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

unpack them, open a terminal.
in the terminal, do:

- sudo apt-get build-dep alsa-base

- go to the alsa-lib directory and type "./configure"

if no error is given (I had to do also "apt-get install python-dev" due to 8.04 not finding the libs), do:

- "make"

then

- "sudo make install"

Then, go to the alsa-driverxxxxxx you unpacked and do the same:

-"./configure", then "make" then "sudo make install"

reboot

If all goes well your 0404 should be detected now. You probably will have to select it as a default card using the gnome sound applet or something.

if you open a terminal and type "alsamixer" (sudo apt-get alsa-mixer or get and compile and install alsa-utils from the link I gave you above, is preferable), you'll be able to control a lot of parameters for your card (note: if you have several cards do "alsamixer -c x", where x is the number of the card you want to access).
In my 1212m, 0202DAC left and right must be set to DSP0 (left) and DSP1 (right). You'll see what is this that I am talking about, if you can run "alsamixer".

Good luck. [/I]

I downloaded the alsa-lib package and the alsa-driver package. I unpacked these in my Documents folder. Then followed the instructions above. All worked well down to the "make" of the alsa-driver. This apparently failed and the install also failed. Here are the errors I received. Maybe someone can givbe me a clue as to how to get arouind them ...

Errors:

Error from 'making' the driver ...
CC [M]  /home/johnny/Documents/alsa-driver-1.0.17/soc/soc-dapm.o
In file included from /home/johnny/Documents/alsa-driver-1.0.17/soc/soc-dapm.c:2:
/home/johnny/Documents/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c: In function ‘dapm_pop_time_store’:
/home/johnny/Documents/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c:834: error: implicit declaration of function ‘strict_strtoul’
make[3]: *** [/home/johnny/Documents/alsa-driver-1.0.17/soc/soc-dapm.o] Error 1
make[2]: *** [/home/johnny/Documents/alsa-driver-1.0.17/soc] Error 2
make[1]: *** [_module_/home/johnny/Documents/alsa-driver-1.0.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [compile] Error 2

Error from the driver install ...
johnny@ubu:~/Documents/alsa-driver-1.0.17$ sudo make install
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/johnny/Documents/alsa-driver-1.0.17/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
find /lib/modules/2.6.24-19-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.24-19-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.24-19-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.24-19-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/johnny/Documents/alsa-driver-1.0.17/acore'
mkdir -p /lib/modules/2.6.24-19-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.24-19-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/johnny/Documents/alsa-driver-1.0.17/acore'
make: *** [install-modules] Error 1


Any suggestions are welcome

---

### Post by Yellow Pasque on 2008-08-24
Old post. Please ignore.

---

### Post by jpumphandle on 2008-08-24
Thanks for the script. 

I followed the instructions and the script seemed to go fine. I got a message at the end telling me to reboot for the new devices. Seemed like about 10,000 messages, but I did not see any errors.

After reboot, I still can't find the EMU 0404 card. Is there some other hookup that I have to do? Here's what I see in Sound Preferences ....

[IMG]http://johnnypumphandle.com/johnny/images/SoundPreference.png[/IMG]

I get an error with all of these devices when testing and the ALSA mixer can't find anything?  Am I getting close?

---

### Post by lobo_blanco on 2008-08-24
Hi Zob,

The following link actually has to do with Intel onboard sound card but a lot of the information there deals with getting Alsa straightened out and points to an Alsa text file that has a large list of video cards.
The main problem I was having was that I had loaded and unloaded a number of packages to try to get my sound fixed so I ended up without all the Alsa files needed. Perhaps the following can shed some light on your sound issues as well. (I found it to be not just related to Intel sound issues)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Sure hope it helps.

Dave

p.s. Besides fixing my sound problems, it was a great command line tutorial as well, I learned a lot from it.:)

---

### Post by unitribute on 2008-10-05
How is it going Zob? Have the same troubles as you, any new suggestions? The script didn't work for me either...

---

### Post by jpumphandle on 2008-10-05
Still sitting here with no sound from my EMU 0404 card. I don't have a clue where to go from here.

---

### Post by heysean on 2008-11-14
This is beginning to scare me.
I want to kick Windows to the curb...
but being a music producer I HAVE to have my sound card work.

So for now Ubuntu stays on the cd and not my harddrive :/

Does ANYONE have a working 0404 PCI card in their machine?

---

### Post by Xan.In on 2008-11-20
Hi, I have too an emu 0404 card and my history is quite weird. After many time spent in front of the terminal I could install my emu 0404 card on Ubuntu 8.10 (Sorry, but I did so many things that I cant assure what was the right one).

Later I discovered Ubuntu Studio and, because I had to format the Hard disk so I started with de DVD of Ubuntu Studio. But now I can't make that my card works. But I know it can work :(, sure!!

In this case (with Ubuntu Studio 8.10) I can't go further of installing the drivers package,here is the error I have

/usr/src/alsa/alsa-driver-1.0.16/acore/timer.c: In function 'snd_timer_request':
/usr/src/alsa/alsa-driver-1.0.16/acore/timer.c:155: error: wrong type argument to unary exclamation mark
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.16/acore/timer.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.16/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.16] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [compile] Error 2
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /usr/src/alsa/alsa-driver-1.0.16/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/acore'
mkdir -p /lib/modules/2.6.27-7-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.27-7-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/acore'
make: *** [install-modules] Error 1

I hope that anybody can help us
Thanks

---

### Post by sanus|art on 2008-11-24
It worked for me.

Two suggestions:

[LIST=1]
[*]Download chmod to executable and run _[this]("http://www.sanusart.com/files/E-MU.sh")_ script. The script is a year old but updated to `wget` the latest alsas [ v.1.0.18 ].
[*]Go to [http://packages.medibuntu.org/](http://packages.medibuntu.org/) -> select your dist -> download and install alsa-firmware (and optionally add medibuntu repositories).
[/LIST]
EDIT: forgot to mention - worked on Intrepid.

---

### Post by zob on 2009-01-06
Hi sanus|art

Thanks. I followed your suggestion. Still no luck. The same errors as in the output that I posted when I started this thread. But...

You know what guys (I hope you're all still listening), I'm starting to suspect what the error might be.

Since a lot of people seem to get it installed without any problems whatsoever, and a few of just have no luck at all, I was thinking that maybe It is simply a question of moving the 0404 PCI to a different PCI-slot. As far as I remember, nobody tried that yet - in these forums at least. I do remember however that, when I first got it (the 0404) and I was following the forums on people having installation problems on XP, some people found that it would work in one PCI-slot and not in others.

These days I'm a bit to busy to try it out myself, thereby risking having to reinstall (or something) my music production partition, which is on this very same PC, just on an XP-partition.

But if anyone is willing to give it a go, I would certainly be interested to here the result.

Best method would surely be swapping slot and doing a clean install. But hey, maybe it will work with the most recent liveCD as well (latest openSUSE and Fedora both have alsa 1.0.18 - so that would maybe be the place to start).

Could someone with a working 0404 PCI, please check if it works "out of the box" with a liveCD?

Hope to hear from someone...

---

### Post by sanus|art on 2009-01-06
I had to adjust the volume levels and restart for it to work. I don't think different PCI slot will solve the issue.

---

### Post by zob on 2009-01-06
Please don't discourage anyone to try sanus|art. I'm insisting. I could very well be some kind of IRQ-conflict or what do I know...

There is no better explanation as far as I can see, given the fact that a lot of people have their 0404PCI's running and some just cant make it work.

As far as for adjusting the volume level. If it's the slider you're thinking of, merely touching gives me an error, 'cause no sound-card is loaded - you can refer to the outputs of my first post and also post #6 in this thread.

If you want to help sanus|art, what would be interesting to see your outputs of those same commands, so if you feel like, please post them here. Maybe especially the dmesg |grep emu (Or anyone else with a working 0404 PCI).

But again. If someone with no sound and a 0404 PCI card have the time and the guts to experiment, please refer to post #20 in this thread. And if someone wants to read more about IRQ-conflicts, [here's a link to a july '04 article from Sound on Sound.]("http://www.soundonsound.com/sos/jul04/articles/qa0704-1.htm")

---

### Post by luispa on 2009-01-11
> **zob said:**
> Since a lot of people seem to get it installed without any problems whatsoever, and a few of just have no luck at all, I was thinking that maybe It is simply a question of moving the 0404 PCI to a different PCI-slot. As far as I remember, nobody tried that yet - in these forums at least. I do remember however that, when I first got it (the 0404) and I was following the forums on people having installation problems on XP, some people found that it would work in one PCI-slot and not in others.

I changed the 0404 to a different PCI slot with no luck. I did not a complete reinstall.

---

### Post by zob on 2009-01-11
Thanks luispa.

I just don't get it. Why don't our 0404's work, when other people have theirs working???
I guess it must be firmware related then. Which means that we might just as well trash the 0404's that are not working, 'cause they never will.

I don't think it a software (or ALSA) problem. I've tried at least ten different distros and I haven't succeded in getting a sound in any of them (Ubuntu, Mint, OpenSUSE, Sabayon, PCLinuxOS, Mandriva, 64Studio, Musix, UbuntuStudio, Knoppix...).

It must be a problem with the firmware-loader. Remember that the following command:
```
dmesg |grep emu
```

gives this output:
```
[    1.743845] input: Macintosh mouse button emulation as /devices/virtual/input/input0

[   30.997605] emu1010: Special config.

[   30.997686] emu1010: EMU_HANA_ID=0x7f

[   30.997688] emu1010: filename emu/emu0404.fw testing

[   30.997690] firmware: requesting emu/emu0404.fw

[   33.056012] emu1010: Loading Hana Firmware file failed, reg=0x7f

```

(The first line is of course of no interest).

Still, what would be very interesting is, if someone with a working 0404 could post his/her outputs on this command and maybe more fx. this one:
```
sudo lshw -C multimedia

```

Also for the people who haven't read and who may understand what it means (I afraid I don't), in /usr/share/doc/alsa-firmware/ you should have a README file explaining something about the firmware-loaders, which, if read by the right person, might be of some help.

---

### Post by Glynnux on 2009-01-15
Hi Zob, I got the 1.0.16-0medibuntu1 alsa firmware from medibuntu.

In Synaptic package manager I now have 

alsa firmware = 1.0.16-0medibuntu1  

and 

alsa firmware loader = 1.0.15-2ubuntu4

both checked and interdependant (as in you can't uninstall the 1.0.15-2 package without uninstalling the other)

My EMU is now recognised and working........

...but I can't capture from it at the moment so I am using an Alesi multimix8 with poor latency of 23. I am working on that but fast running out of options that I haven't tried.

In Jack setup I have EMU0404 as the interface, USB audio as the input and EMU0404 as the output. I have to set the 'frames/period' to 512 which isn't ideal for live instruments. If I set EMU as the input I can set frames/period to a much lower figure with no xruns...probably because I can't get anything from the mixer.

My sound is set up to use the EMU and all playback and input is set to Alsa.(I get the same result by setting to multichannel playback and multichannel capture but I prefer the Alsa setting as Jack connections just comes up with so many inputs and outputs set the other way)
Alsamixer is set to use EMU0404.

The sound output of Hydrogen is so much more present and rich than the it was with the onboard Intel-hda! 
If I get EMU to work as the input I'll post how I did it (and hope the latency is better than the USB latency)

I have a P4 3.0 on an Asus P4P800 board with EMU0404 pci. 

I hope this is helpful. :)   ...and meanwhile take care with your XP partition.

Glynnux

---

### Post by zob on 2009-01-15
Hi Glynnux
Thanks for helping. Please tell me your outputs of:
```
lspci -nn
```
and
```
sudo lshw -C multimedia
```
and
```
dmesg |grep emu
```

I've tried with the 1.0.16 alsa as well. Now I'm on 1.0.17.
I'd wish I could get to the point where I could choose any alsa settings. I guess if you list you alsa playback hardware devices with:
```
aplay -l
```
you get something. I don't have any... yet...

But I would be very grateful if you, or someone else with a recognized 0404 PCI, would post the outputs on the commands I mentioned first thing in this post.

Thanks.

By the way. Have a look at the linux driver thread over at productionforum.com if you wish:
[http://www.productionforums.com/viewtopic.php?f=24&t=3768]("http://www.productionforums.com/viewtopic.php?f=24&t=3768")

---

### Post by Glynnux on 2009-01-16
Okay Zob,

lspci -nn =

gee@STUDIO-glynnux:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] [1002:4e48]
01:00.1 Display controller [0380]: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary) [1002:4e68]
02:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 46)
02:05.0 Ethernet controller [0200]: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] [10b7:1700] (rev 12)
02:0b.0 Multimedia audio controller [0401]: Creative Labs SB0400 Audigy2 Value [1102:0008]
gee@STUDIO-glynnux:~$ 


-C multimedia gives..

gee@STUDIO-glynnux:~$ sudo lshw -C multimedia
[sudo] password for gee: 
  *-multimedia            
       description: Multimedia audio controller
       product: SB0400 Audigy2 Value
       vendor: Creative Labs
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1
  *-multimedia
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

grep emu gives..

gee@STUDIO-glynnux:~$ dmesg |grep emu
[   32.821160] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   47.785775] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:822: emu1010: Special config.
[   47.785865] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:861: emu1010: EMU_HANA_ID=0x3f
[   47.785874] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:880: emu1010: filename emu/emu0404.fw testing
[   49.794997] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:684: firmware size=0xd67c
[   51.025106] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:897: emu1010: Hana Firmware loaded
[   51.025157] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:900: Hana ver:1.1
[   51.025216] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:905: emu1010: Card options=0x1
[   51.025243] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:907: emu1010: Card options=0x1
[   51.025737] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:945: emu1010: Card options3=0x1
[   51.041538] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:226: Audigy2 value: Special config.
[   51.041791] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1520: EMU outputs on
[   51.041797] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1568: EMU2 inputs on


and finally aplay -l

gee@STUDIO-glynnux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: EMU0404 [E-mu 0404b [4002]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: EMU0404 [E-mu 0404b [4002]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: EMU0404 [E-mu 0404b [4002]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by zob on 2009-01-18
Thanks a lot Glynnux. That was very interesting to see. Not that I'm now know what the problem is. But I can see some interesting differences in your outputs and mine (refer to the first post in this thread, if you are interested).
Well, as for your problem. Have you ever tried to unplug your Alesis and, more importantly, turn of the build-in AC'97 sound card in BIOS. If not, go for it. And then see if you can mingle with the settings and find a record option for your 0404.
I can see that both your in's and out's on the EMU-card gets turned on. So theoretically you should be able to make it work.

Good luck. And thanks for your help.

PS. If you prefer not to use your build-in sound card for anything, you should turn it of in BIOS anyway IMHO. (It's probably listed as something like AC'97 under integrated peripherals.)

---

### Post by Glynnux on 2009-01-20
The onboard AC97 was only reconnected for a couple of days so my grandson could play a game on LinuxMint.;)

I had to crack on Saturday and fired up XP. Having found my Reason DVD I was able to put Reason back into working order and within an hour I had a drum track and guitar track recorded on Cubase.

I have to say that Cubase is a brilliant piece of software...and my latency is around 4ms.

It's interesting that I only have the EMU connected for XP and all sound works ..including capture.

Now I've started recording with Cubase again it has taken the pressure off so I will re-install Ubuntu Studio and see if I can get the EMU working in full Duplex. I'll approach it a little more scientifically this time and make more notes. 

Sorry to veer slightly off topic. I'll keep checking your progress and post if my progress improves. I'd like to have Ubuntu Studio and Ardour working.;)

Glynn

---

### Post by juppalo on 2009-02-04
Eeh just a crazy idea... Might these problem have something to do with the diffrence between the 64bit version of ubuntu and the 32bit? I'm myself are running a 64 bit version and ain't getting it to work... 

So well if you have a 64 where you got it to work.. please reply... cause reinstalling ubuntu seem like quite the fuzz atm for me

---

### Post by zob on 2009-02-05
Nope, I'm on 32 bit so that's probably not the case. Though tryin' to get it to work on a 64 bit system is probably twice as difficult as on the 32 bit. (That, in my case, is impossible times two).
Good luck though.

---

### Post by Glynnux on 2009-02-05
I hope I'm not behind the game with the following comments...

I installed Mint KDE a couple of days ago and had no sound card listed so I did the following.


If you have Hardy..paste this into your terminal..
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

add the GPG key..
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
(if you are told the package can't be authenticated ACCEPT it anyway.)

I then checked down the list on my package manager (Adept Manager in KDE Mint Elyssa) and installed the firmware and firmware loader. The manager suggested alsa 1.0.16 as the drivers and offered to install them but when I accepted the install it was automatically interrupted because it would break installed packages (I had already installed the alsa 1.0.19 driver, libs and utils)

Then mentally crossing my fingers I restarted...and was greeted by the little tune when my desktop came up!! Yippee.

I went the long way about installing the drivers and it turned out that my adventurousness was simply a waste of time as the package manager would have brought them for me. 
I know that alsa 1.0.16 works in Ubuntu and Ubuntustudio... I now know that alsa 1.0.19 works in my Mint Elyssa KDE install (based on Hardy).

 I STILL HAVEN"T FIGURED WHY THE LINE INPUTS AREN"T WORKING!


I truly hope that helps.:KS

Most of the above was copied and pasted from ...
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Which you will need to visit if you have Intrepid or such..

My only cleverness being to Google the correct query. :) (oh and some nifty one fingered typing)

---

### Post by zob on 2009-02-08
Hi Glynnux.

I truly appreciate your help. I'm not quite sure what you're to tell me this time though. Maybe it's just my poor English. But as far I can see, your advice is to install at least alsa version 1.0.16. I'm running ubuntu 8.10 now. And I have the default 1.0.17 drivers (they should do the job I think) and I don't even get close to getting it recognized. The problem is that the firmware fails to load.

Is there something that I should do according to you, that I haven't done?

---

### Post by sanus|art on 2009-02-09
Hi,

I just made a fresh Ibex install and ran this script of mine and nothing happened after the reboot, so I ran it another time and it all works nice now.

tri this:

[LIST]
[*]Remove all ALSAs
[*]Save the script bellow as *E-MU.sh*
[*]"*chmod 0777 /what/ever/it/is/E-MU.sh*" it
[*]Run it ones
[*]Reboot
[*]Run it second time
[/LIST]
Don't know right now why the double run, but it should work.

```

#!/bin/sh
#
#######################################################
### [NOTE] - You must be root to execute this script. #
### Use: 'sudo sh /path/to/E-MU.sh'
#######################################################

# Dependensies.
apt-get install build-essential ncurses-dev gettext
apt-get install linux-headers-`uname -r`

# Stop alsa.
/sbin/alsa unload
/etc/init.d/alsasound stop

# CHMOD dsp,mixer,sequenser and midi (if exists).
echo '\033[31;47mCHMOD dsp,mixer,sequenser and midi ...\033[m';
chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi
echo '-- OK --';
# Files to download.
echo '\033[31;47mDownloading alsa packages ...\033[m';
wget http://alsa.cybermirror.org/driver/alsa-driver-1.0.19.tar.bz2
wget http://alsa.cybermirror.org/lib/alsa-lib-1.0.19.tar.bz2
wget http://alsa.cybermirror.org/firmware/alsa-firmware-1.0.19.tar.bz2
wget http://alsa.cybermirror.org/utils/alsa-utils-1.0.19.tar.bz2

echo '\033[31;47mExtracting alsa packages ...\033[m';
tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-firmware*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

echo '\033[31;47mSetting alsa for compilation ...\033[m';
mkdir -p /usr/src/alsa
mv alsa-* /usr/src/alsa

# alsa-driver
echo '\033[31;47mInstalling alsa-driver ...\033[m';
cd /usr/src/alsa/alsa-driver*
./configure --with-cards=emu10k1 --with-sequencer=yes --with-kernel=/usr/src/linux-headers-$(uname -r) --with-oss=yes
make
make install

# alsa-lib
echo '\033[31;47mInstalling alsa-lib ...\033[m';
cd /usr/src/alsa/alsa-lib*
./configure
make
make install

# alsa-firmware
echo '\033[31;47mInstalling alsa-firmware ...\033[m';
cd /usr/src/alsa/alsa-firmware*
./configure
make
make install

# alsa-utils
echo '\033[31;47mInstalling alsa-utils ...\033[m';
cd /usr/src/alsa/alsa-utils*
./configure
make
make install

# Load modules into kernel (not always needed but do not harm)
echo '\033[31;47mLoad modules into kernel ...\033[m';
modprobe snd-emu10k1
modprobe snd-pcm-oss
modprobe snd-mixer-oss
modprobe snd-seq-oss

# Set E-MU to default
echo '\033[31;47mSet E-MU to default ...\033[m';
asoundconf set-default-card EMU0404

echo " ";
echo '\033[31;47mIMPORTANT !!!\033[m';
echo " ";
echo " ";
echo "Now reboot your machine, and hope to enjoy the better sound quality with E-MU";
echo " ";
echo '\033[31;47m NOTE \033[m Mixer might be muted by default !';
echo " ";
echo '\033[31;47m NOTE \033[m You need to go to System => Preferences => Sound, to select your card with Multichannel playback';
echo " ";

```

---

### Post by zob on 2009-02-12
Hi sanus|art

I'm thankful that you're still trying to help.
When I try to remove alsa in synaptic, it says that ubuntu-desktop will be removed as well??????? Why on earth would that be?????

I'm kind of scared of that. What would be your trick to purge alsa without removing ubuntu-desktop (or gdm and fast-user-switch applet which it threatens to remove as well)?

/zob

---

### Post by sanus|art on 2009-02-13
I guess lines 13-14 in the script will be enough as well - as they are unloading the ALSAs and by installing the compiled once, causes them to be overwritten.

Just try to double run the script as mentioned above - let's see if it helps without the 'remove'.

---

### Post by zob on 2009-02-13
Ok. I've followed your recommendations. Made the E-mu.sh double-run. It seemed to be "doing something". I still can't load the HANA firmware (see my first post in this thread - I get the same outputs).
However when I check the alsa version (cat /proc/asound/version) I get version 1.0.18. Am I supposed to have 1.0.19 after running the script. It does say that it was compiled today though...:confused:

---

### Post by zob on 2009-02-14
Hey.
I finally succeeded in altering something. When I switched my onboard AC'97 soundcard in BIOS back on, I couldn't get a sound from that either. Which leaves me with not even bad sound. At least it's a new situation. I guess it's just a question of reinstalling the intrepid version of ALSA, but I think I'm taking a break from this for a while.
Again thanks to everyone trying to help out on this, and please post any new ideas in this thread.

/zob

---

### Post by zajaro on 2009-02-18
Hi zob

I'm also with the emu 0404 trying everything,... tonight I'm going to try de scripts although not having conexion at my house yet gonna try doing with the sources downloaded in another machine and the copied to the one with the emu,...
the problem with the card not working may be related to the fact that at the end of the script it tries to set the emu as default
" asoundconf bla bla" hope it helps,... 
sorry to bother and count me in to try anything,... 
best regards.

---

### Post by zajaro on 2009-02-18
I correct myself
by "the card not working" I meant "the AC'97 not working after running the scripts and re-enabling the card in the bios"
sorry.

---

### Post by sanus|art on 2009-02-18
@zajaro:
We do want emu as the default, no? So why not set it as the default?

---

### Post by zajaro on 2009-02-18
yeah you're right it's just that in the particular case that zob is writing about he re-enabled his ac'97 and couldn't get sound from that one either,... so I was guessing that maybe it was because even with the ac'97 the card thats alsa was trying to use was the emu,... so in order to get out of this "new" situation he was talking about being in I ask him to check if changing that would get him sound out of the ac'97,... by the way,.. I'm concerned with the fact that we still can't know for sure if the cards that you and glynnux posses have different hardware versions of the ones that zob and I have,.. knowing a way to settle that would surely help every one that's depending on this thing being resolved to enjoy audio in linux.
Anybody know of a way?,... version of the driver in windows?,.. some markings on the cards? or maybe the box( in which they came)?

---

### Post by zajaro on 2009-02-18
speaking of which I don't even know which version mine is,.. so I know even less about zob's.

---

### Post by zob on 2009-02-18
You're both right. E-MU should of course be set to default in that script. But as I had no success with the script, zajaro was just pointing out why my AC'97 had stopped working. Thanks!

My E-MU 0404 PCI card has firmware version 1.0. You can check it if you have a Windows installation with E-MU drivers installed through the Pacthmix-software. Actually a bit tricky to find. But when you open patchmix you will see the E-MU logo at the top (in the middle), if you right click there, you will see the "about E-MU". Click there and you'll get all the info about driver version, patchmix version, firmware version, etc.

You are right though. It would be very interesting if people would report what firmware-version they have, and if they made it work in linux or not.

/zob

---

### Post by zajaro on 2009-02-19
I'take a look tonight to that,... by the way, the output of lspci -nn in my machine says that my card is exactly the same as the output for glynnux but it says [1102:0004] at the end,... could be there that resides the problem?,... I read at the bugzilla page from alsa that there were some patches for the alsa driver for the emu card and they basically went around adding especification or definitions for differents types of that I believe,.. well anyway anything is welcome.

---

### Post by zob on 2009-02-19
Yeah. I too have [1102:0004], whatever that means...

But let that be a request to people with 0404 PCI cards to post their output of lspci -nn here, and to state if they have it working or not. You never know maybe you're on to something...

---

### Post by zajaro on 2009-02-20
well,... had a look last night and, yes, the firmware version is 1.0; hoping to get lucky I tried to see if I could find some way to pass beyond that message, " loading firmware failed", in the loading stage, I edited the emu10k1_main.c in the alsa-drivers source folder, found the if block that doesn't passes and commented it and recompiled and installed,... the result? the driver goes mad and tries to load the " Audio Dock Firmware" and keeps doing it with error and it won't stop trying so have to went back the changes to the code and reinstall,.. don't know,... it looks like, in order to load the firmware properly the result in a register ( 0x7f ) has to be something like ( 0x55) but the if block in the driver says something like "if ((reg & 0x3f) != 0x15) then {"load failed"} ,  I don't understand what it does but it seems to me like something that comes out of knowledge of how the hardware has to be initialized,... and I don't know what the registers are or what the value means. All I can say is that the card is correctly detected and the firmware that the driver tries to load is the correct one.
I read the patches available at the bugzilla page from alsa,.. the ones that this james guy published and they look like patches to the new version of the card [1102:0008] so I'm lost.
Hope it helps someone.
After all, the card works and I don't believe there's no way to make it work with alsa it's just a matter of knowing how to properly load the firmware in this particular version. or maybe ( wild guessing here) to add an if block in the firmware source of alsa and make another firmware for this version,... don't know where to get it or how to make it, though.

---

### Post by Nab!!daN on 2009-02-23
Hi All,

I think you are right, there is 2 versions of this card.

We make runs most of EMU0404 by installing manually or via script.

Please find a link here under:

[http://doc.ubuntu-fr.org/emu0404](http://doc.ubuntu-fr.org/emu0404)

We even made a script to choose onboard or emu0404 when needed.

All works as expected, but a few users are reporting the same error as you:

> [   43.841253] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:893: emu1010: Loading Hana Firmware file failed, reg=0x7f

Full compilation logs are here under:

[http://didouchk.free.fr/logcomplet](http://didouchk.free.fr/logcomplet)

> xxx@yyyy:~$ ls -la /lib/firmware/emu/hana.fw
-rw-r--r-- 1 root root 78756 2009-02-06 21:08 /lib/firmware/emu/hana.fw


Still investigating but sounds like to be an issue with alsa itself regarding this card release :(

See you !

---

### Post by Nab!!daN on 2009-02-23
lspci --nn   on a WORKING EMU0404 card:

> xxx@yyy:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82P965/G965 Memory Controller Hub                          [8086:29a0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82P965/G965 PCI Express Root Port [                         8086:29a1] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation 82562V 10/100 Network Conn                         ection [8086:104c] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI C                         ontroller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI C                         ontroller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI                          Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Con                         troller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Po                         rt 1 [8086:283f] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI C                         ontroller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI C                         ontroller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI C                         ontroller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI                          Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev f                         2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HH (ICH8DH) LPC Interface Cont                         roller [8086:2812] (rev 02)
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA RAID Controller                          [8086:2822] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8                         086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Geforce 9600 GT 512                         mb [10de:0622] (rev a1)
03:02.0 Multimedia audio controller [0401]: Creative Labs SB0400 Audigy2 Value [                         1102:0008]
xxx@yyy:~$


lspci on a NOT working card:

> xxx@qqqqq:~$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
02:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)


---

### Post by sanus|art on 2009-02-23
Working card.

```

[~]$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
03:00.0 Multimedia audio controller [0401]: Creative Labs SB0400 Audigy2 Value [1102:0008]
[~]$ 


```

---

### Post by Nab!!daN on 2009-02-23
Hi,

If any logs are needed i can indeed managed to provide it :)

See you !

---

### Post by zajaro on 2009-02-24
Nab!!daN by the looks of it I believe that there's no problem with the cards with identifiers [1102:0008], but with the ones that have 0004 as their hardware identifier,... I believe there's a difference in their firmware,... and that's why they fail to be programmed ( i.e. load firmware at detection time )the problem is that I have no spec ( description of the registers in the card) nor idea of what the code of the firmware does,...if I had any of those,... I could try to change either the paramaters in the object creation table ( emu10k1_main.c circa line 144 ) for the emu 0404 version 1,... which if you take a look are somewhat different that the parameters of the creation of the object for the emu 0404 v2.
maybe the register ( the one that's checked at line 880 in emu10k1_main.c) was in another addres in the firmware version 1.0 or perhaps should have to have another value as a result of the fpga programming,... but not knowing the available address or what the values should been,... there's not much that could but try random values till it load succesfully,... I don't know better,.. hope someone can throw me a bone here.
if any one care to take a look you will see that in the line 880 of the code there's a check (( reg & 0x3f) != & reg 0x15 ) {
 printf " the card failed to be programmed reg = 0x3f ") or something like that,... that's the check that the 0008's pass and the 0004's don't,... I believe that if the programming goes well then there is a value in that register that must be something like 0x55 or 0x15 and if they're different then the code breaks out and fail.
if I take that out then the driver can't load the firmware so I can think of two choices to test 1) memory ranges from one card to the other varies and then is a matter of finding which ones are the good ones for the old card.
2) the firmware must be different and then therehas to be added an "if"block of code  to the driver code in order to load one out of two different firmware for this particular card.( don't know how the other firmare can be constructed).
sorry to be so vague but that's want I can understand,...way out of my limited knowledge here.

---

### Post by zob on 2009-02-24
Nab!!daN. Thanks for you're informative posting. Nice 0404 site you have there!

zajaro. I think you're right. Though I can only judge that by way of intuition. I afraid this is getting so technical that I can't be of any help. Well, one thing I can do. I can and I will cross my fingers. Let's see if that helps.

/zob

---

### Post by Nab!!daN on 2009-02-24
Hi all,

I perfectly understand your point of view Zajaro.

I think you right at 100%

I will try to have more information from creative support but by experience I know the kind of response you can expect when using Linux...

Like Zob, it is now out of the scope of my little knowledge, I can only help further with logs and testing.

Thanks a lot for your response :)

I'm going to harass creative support :p

See you !

---

### Post by sanus|art on 2009-03-17
This is my E-MU0404PCI 'about' screen with versions and all. 
[ATTACH]106705[/ATTACH]

---

### Post by zob on 2009-03-17
Thanks sanus|art.

I think we're getting closer to the problem. My 'about screen' has the same output except from one crucial point. I get firmware version 1.0.
My guess is that everybody with firmware version 1.1 (or maybe higher if that exists) should be able to make their 0404's work under linux/alsa. Whereas the firmware 1.0 guys - we're doomed.

---

### Post by zajaro on 2009-03-17
I think the same,... the problem is that I don't know where does the firmware file emu0404.fw in the alsa firmware package comes from,.. I mean does it come from some crosscompiling thing or is it entirely a binary made by james coultier? if it is we could grab the source and see if there's some modification regardless of the hardware address where it expects to write and read himself, respectively,... in the alsa-firmware source the file gets made by writing bit a bit which means that its already a hex file embbeded inside a c source file. I can get james to answer my mail ( which I believe he is entirely in his right to do ) and don't want to bother the alsa mailing list a bout it but I believe that it all comes from the fact that the firmware was made with the 1.1 firmware cards in mind and without knowledge of another cards being in existence having another version of firmware.

---

### Post by zajaro on 2009-03-17
any way i'm learning to program pic mcu's so i'm learning a little of C and a little o assembler and I would have no problem in trying to work this out,.. is just that a I need some pointing in the right direction.

---

### Post by zob on 2009-03-17
I just wrote E-MU to ask them if there is any way, under windows which they support, that the firmware can be update.
I guess the answer is no, but I'm afraid it's the only thing I can do to contribute by now.
This is getting terribly complicated. And that's why we have brainy guys like zanjaro. I really hope you'll find a solution zanjaro. And please keep us informed.

Still. If anyone, who are dual-booting Linux/Xp, with a working card in linux, would follow sanus|art's example and post their firmware version here, I would be grateful. That way we can verify our hypothesis.
Thanks.

---

### Post by sanus|art on 2009-03-18
Just a thought - 
Maybe some build dependencies for alsa are missing. It might compile well without them, but will not work. I'll suggest ' sudo apt-get build-dep alsa-tools alsa-utils alsa-base' before any kind of alsa compilation.


Quoting zajaro:
> 
... does it come from some crosscompiling thing or is it entirely a binary made by james coultier ...
As of alsa suggestion - 
```
--with-cards=emu10k1
```parameter should be passed to ./configure of `alsa-driver`. Or am I confused?

---

### Post by zajaro on 2009-03-18
what you say is correct sanus,... but what that does is make sure that the module for the emu gets compiled but the problem is not that the module compile ( which it does ) but that at the boot phase of the system when the kernel tries to load the driver there's a discovery stage in which the driver detects the card and it does it ok even to the point of acknowledging that our cards is the of the old firmware version. the problem arises because the branch in the process that deals with our cards fails. and it fails because the firmware that it tries to load into the card doesn't get written in the place that the driver expects it to find it ( or so I guess ).
Hope to be of some assistance to some one better suit than me to figure it out.
any way thanks for your kind words zob but it looks that i'm nowhere near brainy or I may have solved it by now, hahahahah.
( in my country there's a figure of speech that roughly translates to " you lack a granny( grandma)" meaning I believe to much of myself haahaha!)

---

### Post by zob on 2009-03-19
E-MU support answered me faster than I thought they would. That was the good part. Now the bad:

> Dear Valued E-MU Customer;

We are sorry to inform you that there is no firmware update for the E-MU 0404 PCI product. The update is burned in to memory chips and the chips with the new firmware are assembled in the factory. In order to get a 0404 PCI with FW v1.1, you would need to buy a recent 0404 PCI product.


So. I guess it's new cards (how would you even know if the thing in the store has firmware 1.1?) or we have to find a solution ourselves.

---

### Post by sanus|art on 2009-03-20
That's a pitty! 
But I think/hope in the end someone will come-up with solution as it is one fine sounding but cheap card.

---

### Post by sgx on 2009-04-04
> **sanus|art said:**
> That's a pitty! 
But I think/hope in the end someone will come-up with solution as it is one fine sounding but cheap card.
Has anyone tried setting uo a regular root user, and a fully root owned wine, and installing all the e-mu driver, patchmix etc in there?

---

### Post by zob on 2009-04-04
hi sgx.
If you are suggesting wine to be a solution to our cards with old firmware not being able to load, I can predict it won't help us.

If you are asking what would happen if you tried to use patchmix trough wine with a working 0404, I don't know the answer. I don't think it would work, but it could be fun to try. Mostly because if I could try it out, it would be because I had a working card;)

---

### Post by zajaro on 2009-05-08
still the possibility remains that just as the cards with the firmware 1.1 can ( and have been made to) work with alsa, to be able to contruct a firmware file that programs the 1.0 version cards and make the branch in the driver in order to load this fiel instead of the original upon the discovery of the older card.
only problem is that I don't know how to make this firmware or where does one  need to look to develop it.
I can imagine how to make the branching on the driver source dough.

---

### Post by Krakeur on 2009-05-24
Ok, after much consternation, I got my 0404 pci to work.  Hope this helps others - 

1)The system needed the 'emu0404 firmware'.  This must be installed from Medibuntu repositories - 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

follow directions for adding repository for particular installation (jaunty, etc.) then do 'add the gpg key'.

2)Open synaptic (System>Administration>Synaptic Package Manager) 
put 'alsa firm' in quick search field (don't need to hit enter). Install 'alsa-firmware' and 'alsa-firmware-loaders'

3) Reboot computer.

4)open the volume control - I had to make 'front' appear via preferences button to get full sound.  

This worked for me - ymmv
Phew!  Almost returned my new sound card because of this nonsense.  ](*,)

---

### Post by zob on 2009-05-24
Seeing Krakeurs post made me wonder. Any news zajaro? Do you think the 0404 PCI with firmware 1.0 will ever work? I'd wish I had a 1.1 version like Krakeur. Just install alsa-firmware-loader-thingy and there you go...

---

### Post by wuglr on 2009-05-27
Gripping thread guys!
At least, up until the point my machine spat out 1102:0004..
If I knew even the slightest more about drivers (and linux) then I'd work myself stupid figuring a solution. I simply don't have enough money to buy another card.
Looks like I'll be settling for the lesser quality of hda for a now,
.. whilst keeping my fingers crossed.

Good luck to anyone taking on this challenge.

---

### Post by zob on 2009-05-27
I feel with you wuglr.
Well, we may have non-working 0404's, but we have this thread. It's gives my life a purpose. Actually I'm scared that if one day my 0404 would be working, I would sink into an existential crisis.
Thank you E-MU, if it wasn't for your non-working hardware, I would have lost myself in the fluidity of post-modern society.

---

### Post by adwsail on 2009-05-30
I have agonized over this problem through the last 2 major ubuntu releases and today I solved it. First let me say I am running Ubuntu 9.0.4 with the Alsa 1.0.20 complete drive package. There are issues with the directions in this package for emu cards (mine is a 1212m, uses emu10k1 drivers on a quad core q6600 in an Asus P5K mb, 4GB ram). The directions cannot be executed as printed on my machine, you get boatloads of errors. Specifically, putting "./configure ; make ; make install" on one line and hitting enter is a guaranteed compile fail on my machine. Each step needed to be done separately. 

But most importantly and the one step that made it all suddenly start working is the following switches for compiling the alsa-driver-1.0.20.  "./configure --with-cards=emu10k1 --with-sequencer=yes --with_isapnp=no". That last switch simply tells linux to not scan the bus for isa cards. Otherwise, the default is scan for isa cards ONLY, at least on my setup. Since I have a PCI card which was detected (as indicated in lspci) but there was no scanning for pci audio. Like you, I kept getting the lspci results showing my card but running "aplay -l" would always say "no cards found". Frustrating to say the least but I have full functionality now. Hope this helps.

---

### Post by zajaro on 2009-06-24
Zob Hope I had news but I'm not
although I took the stickers off of my card and found that the fpga ( the other chip in the card besides the emu10k1 one  from emu ) to be a Xilinx Spartan II but I don't know exactly which version,...so well that's the advance status report for you,... ;-)  
by the way what adwsail says could be good I've never trying specifically disabling isa discovering with this card,... but since he has a m1212 and those were already working with alsa can't say for sure,... wishing it helps a little and not having time to learn to program the fpgas I guess this is all I can do for the moment.

pd: the note about the name of the fpga comes in handy if you have in mind that the reason for the driver failing in the 1102:0004 cards being that the fpga progamming process in the driver-load phase exits with an error.
for more detailed info read my earlier posts

---

### Post by unitribute on 2009-10-05
Hope you're still on it people. I really think it'd be possible to program the file, since I mean it works for the 1.1 firmware version. I myself haven't got a clue on how but I know people out there emancipates in this programming business... :)

---

### Post by zob on 2009-10-05
I kind of gave up. I bought a RME 9632 which works fine (not with pulseaudio though). I still have my 0404 PCI card, and I guess I will plug it back in (together with the RME) if one day there is progress.
Thanks to all the clever people who participated in the troubleshooting though, and sorry I was weak.

---

