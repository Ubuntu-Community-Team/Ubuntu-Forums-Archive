---
title: "ATTENTION HP dvX laptop owners with speaker sound issues ..."
date: 2009-02-17
forum: Hardware
---

### Post by jstalnak on 2009-02-17
... the alsa developers have a solution for this issue:

When you boot you get no sound from your internal laptop speakers though you do get sound from the headphone jack. 

 The cause, according to some alsa developers, is an incorrect 'pin' assignment (in the BIOS, perhaps) whereby sound output meant for the internal speakers gets routed to the wrong place.

If you have an HP dv4, dv5, and perhaps a dv7 model series laptop, you may have this issue.

The latest alsa-driver snapshot provides a fix for this issue. I'm listening to a Keith Jarrett jazz cd right now through the internal speakers of my HP Pavilion dv4 1225 laptop after downloading, compiling, and installing the latest snapshot.  You can get it here:

[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)

After downloading and gzip/tarring the files, you'll need sudo privileges to:

```
#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
#> sudo reboot
```

After restart, you should have sound from the laptop speakers.

If you do not, you should consider the alsa developers your best resource. They have some tools you can use to discover what's happening and since they write the code that goes into the kernel for the sound drivers, they can hopefully fix your problem.  Just go to the alsa web site and find the alsa-devel email list and join up.  

NOTE: this does not require a kernel build :-)  I post this to the ubuntu forum with the permission of several of the alsa developers I've been working with.

---

### Post by XxX_VLAD_XxX on 2009-02-19
Hello,

My Laptop is a HP dv4 1129la and I have problems with the sound, I think it's because of my processor 'cause it came with Windows Vista 64-bit And I installed Intrepid 8.10 but I think I installed de 32-bit version. Most of the packages I've installed are for i328, everything works fine except sound.

In the Log in of Ubuntu I can hear the 'duh bump' but doesn't sound right it repeats every half second of it several times, like a scratch CD after that no sound. RythmBox crashes if I try so open a file, 'cause of an error with the audio, there is no playback device.

If you can help it would be great, 'cause sound is the only thing left to do in my Ubuntu, if you need more information I can give it to you.

Thanks a lot

By the way that link to download DOESN'T work, maybe if I try what you suggest it can be fix, but I can download the fix. Thanks again

---

### Post by XxX_VLAD_XxX on 2009-02-19
It may work try this link. I haven't try it yet but will give it a shot

[http://ubuntuforums.org/showthread.php?t=984538](http://ubuntuforums.org/showthread.php?t=984538)

---

### Post by OpenMercury on 2009-02-20
> **jstalnak said:**
> ... the alsa developers have a solution for this issue:

When you boot you get no sound from your internal laptop speakers though you do get sound from the headphone jack. 

 The cause, according to some alsa developers, is an incorrect 'pin' assignment (in the BIOS, perhaps) whereby sound output meant for the internal speakers gets routed to the wrong place.

If you have an HP dv4, dv5, and perhaps a dv7 model series laptop, you may have this issue.

The latest alsa-driver snapshot provides a fix for this issue. I'm listening to a Keith Jarrett jazz cd right now through the internal speakers of my HP Pavilion dv4 1225 laptop after downloading, compiling, and installing the latest snapshot.  You can get it here:

[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)

After downloading and gzip/tarring the files, you'll need sudo privileges to:

```
#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
#> sudo reboot
```

After restart, you should have sound from the laptop speakers.

If you do not, you should consider the alsa developers your best resource. They have some tools you can use to discover what's happening and since they write the code that goes into the kernel for the sound drivers, they can hopefully fix your problem.  Just go to the alsa web site and find the alsa-devel email list and join up.  

NOTE: this does not require a kernel build :-)  I post this to the ubuntu forum with the permission of several of the alsa developers I've been working with.

This worked Beautifully for me.  Yeah, beautiful sound.  I put hp-dv4 in where it calls for dv5.  All sounds work..Did exact procedure.

Machine is: hp pavilion dv4-1222nr.

---

### Post by balak on 2009-02-21
jstalnak : You the man. Worked perfectly on the hp dv4z (AMD Turion X2) version. 
Awesome!!!

So this is fixed in alsa version 1.0.19
Now to wait for ubuntu to pick this up by default.. till that happens, will we have to recompile the alsa module for every kernel upgrade ? Can this be installed using dkms.

---

### Post by bongtothesoo on 2009-02-23
thank you so much this fixed my speaker issues with my dv4z.
is there a similar fix to get the internal mics to work?
thanks again

---

### Post by jr2 on 2009-02-28
Hi, I'm new to Ubuntu (actually new to Linux, even though I have dabbled with Mandriva a bit in the past), I'm running the AMD-64 version of Ubuntu 8.10, and I have a Pavilion dv4-1275mx.  Can someone tell me where to unzip the archive to?

---

### Post by jstalnak on 2009-03-03
jr2: I put all my downloads in the same dir and go from there. No need to put the archive/unzipped files anywhere special.  When you 'sudo make install' that will put the files where they need to be for the system to find/use them.

Regards

---

### Post by carlos_listas on 2009-03-08
I&#7743; having troubles during the configure

Linux hp-work 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
--------------
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
---------------
head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD71B7X

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040
------------------------------
cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd2500000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xd2410000 irq 19


.........
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
./configure: line 13325: ALSA_TOPLEVEL_SELECT: command not found
./configure: line 13327: ALSA_PARSE_KCONFIG: command not found
./configure: line 13329: ALSA_TOPLEVEL_DEFINES: command not found
./configure: line 13339: ALSA_TOPLEVEL_OUTPUT: command not found
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  'Makefile.conf.in' seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: error: cannot find input file: include/config1.h.in

---

### Post by dep01 on 2009-03-08
> **carlos_listas said:**
> I&#7743; having troubles during the configure

Linux hp-work 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
--------------
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
---------------
head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD71B7X

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040
------------------------------
cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd2500000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xd2410000 irq 19


.........
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
./configure: line 13325: ALSA_TOPLEVEL_SELECT: command not found
./configure: line 13327: ALSA_PARSE_KCONFIG: command not found
./configure: line 13329: ALSA_TOPLEVEL_DEFINES: command not found
./configure: line 13339: ALSA_TOPLEVEL_OUTPUT: command not found
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  'Makefile.conf.in' seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: error: cannot find input file: include/config1.h.in

same exact problem. can anyone help?

---

### Post by dep01 on 2009-03-08
Hello everyone. I have a HP Pavilion 1275mx and doing the following solved it:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

add the following to the end of the file.

```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1
```

Cheers,
dep

---

### Post by idream on 2009-03-12
jstalnak!!!
Thank you!!! 3 months I have been struggling with this problem!! 
I LOVE MY LINUX NOW! Thank you!!:D

---

### Post by anetizen on 2009-03-13
Dear jstalnak

AWESOME work on sound...thanks dude...

AnEtIzEn

---

### Post by topcoder on 2009-03-14
Thanks jstalnak. I (finally) got sound working on my Compaq CQ-45 106AU Laptop. The microphone does not work as of now. Is there any fix to this? Surprisingly, I have problems with sound in Vista now:(. Somehow, the windows audio driver gets corrupt with every system restart!

---

### Post by carlos_listas on 2009-03-15
dv4-1220us
2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
=================
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
=======================
# head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD71B7X

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040
======================================
# cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd2500000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xd2410000 irq 2298
===========================================================
#End of alsa-base file

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1

I tried snd-hda-intel model with hp-dv4 and hp-dv5 to,
but works only headphones, external speakers and microphone don't work.

---

### Post by PatrickMoore on 2009-03-15
> **dep01 said:**
> Hello everyone. I have a HP Pavilion 1275mx and doing the following solved it:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

add the following to the end of the file.

```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1
```

Cheers,
dep


i must say this was far easier than compiling the driver. thank you dep you saved me much frustration.

---

### Post by grogo on 2009-03-15
For anyone with Intel's onboard (ICH9) such as I've got on a dv4-1117ca, find and follow soundcheck's alsa upgrade script and add the following lines to your /etc/modprobe.d/alsa-base

options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

I'm guessing that the dv5 line should work for most dv4, dv5 and dv7 laptops to fix the connector recognition issues.  I can confirm that the headphone outputs on both the laptop and my HP QuickDock work properly, haven't played with the digital outs yet.

---

### Post by dhruvkanal on 2009-03-17
@topcorder
dude i have the same laptop...my laptop speakrs are still not working,though sound is coming out of the headphone jack...despite trying al these settings...can u give me de exact copy of ur alsa config file and also which driver version of alsa you using?

---

### Post by xMoDx on 2009-03-20
> **dep01 said:**
> Hello everyone. I have a HP Pavilion 1275mx and doing the following solved it:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

add the following to the end of the file.

```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1
```

Cheers,
dep

hello dep,

not working on my Compaq Presario CQ40-340TU please help

---

### Post by uticamarco on 2009-03-22
[SOLVED] HP Pavilion dv4-1220us no sound, error compiling alsa snapshot.  Issues with "include/config1.h.in" and "no makefile."

I'm just a linux newb, and I've been havin' issues for a while with sound on my HP laptop.  Finally, I read this thread, compiled the driver, added "options snd_hda_intel model=hp-dv5," and sound worked.  Then, however, after a month, after a new update, sound stopped working.  I formatted my partition, so I could not roll back anything even if I knew how to.  But I have sound working again, and here's how (I don't know if all these steps are necessary):

First, I went to the synaptic package manager, typed in gcc, right-clicked and "marked for complete removal."

Then I tried some older compilers, and think I settled on this one: [http://packages.debian.org/etch/gcc-3.4](http://packages.debian.org/etch/gcc-3.4)

The dependencies are listed at the top of the page, the package itself downloadable at the bottom of the page (AMD64).  Some of the dependencies have dependencies, too.  Be sure to install all the dependencies and their dependencies, in order.  Choose to open with gdebi package installer.

Then, I had to go back to synaptic, and add install gcc.  Next, I had to go to the update manager and update three 3.4 compiler packages to newer versions.  (These last two steps make have been performed in reverse order). 

Finally, I used a different snapshot from the same source: [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz)

I followed the steps from the first post after this point, and everything worked.

Just a pointer to other newbs, I downloaded the file to my desktop, extracted it there, went to places, home folder.  I created a folder named compiled.  I opened the compiled folder, and created a folder named alsa.  I renamed the folder I extracted to my desktop to "alsa-driver."  I then dragged it into the alsa folder I created.  Then, I deleted the zipped version I downloaded.  Then I went to applications, accessories, terminal.  Typed in "cd compiled/alsa/alsa-driver."  Then you ctrl+C from the first post and ctrl+SHIFT+V into your terminal, one step at a time (don't include the "#>").  Always use SHIFT when copying or pasting inside the terminal.

Good luck.  

I figure someone will come by and tell me that much of this was not necessary.  Oh well.

---

### Post by crazyMochi on 2009-03-28
The following steps will enable sound on the internal speakers for the HP dv4-1225dx

sudo gedit /etc/modprobe.d/alsa-base

Add the following lines:

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 

perform sudo reboot after saving your changes


Thank you, NaplesBill, for your posting on this fix!

---

### Post by Binary Bandit on 2009-04-04
Hi, I'm relatively new to Ubuntu and would be thrilled for any assistance anyone can provide me with this problem. I have an HP DV4 1228ca. Just like everyone, I did have sound through my front audio jack and could listen to with headphones. Unfortunately after trying all of your helpful suggestions, I don't even have audio in my front jack anymore. If I go into my sound properties, it doesnt seem to recognize my sound card anymore. I beleive this has to do with the entry in the alsa base file. 
Here are my results:

[I]"[CODE]#> ./configure --enable-dynamic-minors
#> make"[/I]

winblows@ubuntu:~/Desktop/AlsaDriver/alsa-driver$ make
make dep
make[1]: Entering directory `/home/winblows/Desktop/AlsaDriver/alsa-driver'
make[2]: Entering directory `/home/winblows/Desktop/AlsaDriver/alsa-driver/acore'
copying file alsa-kernel/core/info.c
/home/winblows/Desktop/AlsaDriver/alsa-driver/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/winblows/Desktop/AlsaDriver/alsa-driver/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/winblows/Desktop/AlsaDriver/alsa-driver'
make: *** [include/sndversions.h] Error 2

*#> sudo make install-modules*

This is where my noobishness may shine through. I wasn't quite sure what to take from the make process above so I continued...
winblows@ubuntu:~/Desktop/AlsaDriver/alsa-driver$ sudo make install-modules
[sudo] password for winblows: 
find /lib/modules/2.6.27-11-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.27-11-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.27-11-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.27-11-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/winblows/Desktop/AlsaDriver/alsa-driver/acore'
mkdir -p /lib/modules/2.6.27-11-generic/kernel/sound/acore
cp snd-hrtimer.ko snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-timer.ko snd.ko /lib/modules/2.6.27-11-generic/kernel/sound/acore
cp: cannot stat `snd-hrtimer.ko': No such file or directory
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/winblows/Desktop/AlsaDriver/alsa-driver/acore'
make: *** [install-modules] Error 1


[I]#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.][/I]


I have tried each of the following, rebooting in between them:

options snd_hda_intel model=hp-dv5

options snd_hda_intel model=hp-dv4

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp=dv4 
options snd-hda-intel enable_msi=1

I have also tried using the 3.4 compiler and "unstable" alsa snapshot package recommended by uticamarco.

If anyone has any suggestions, I would be most grateful. Thank you very much.

---

### Post by mal2104 on 2009-04-11
same problem as above, but that was after upgrading to Jaunty, I had it fixed in 8.10

---

### Post by Binary Bandit on 2009-04-15
GREAT NEWS!!

I was finally able to get my sound to work perfectly on my HP DV4-1228ca.

My first problem was that I did not have "patch" installed and that was giving me the problem listed in my previous post. I installed this "patch" and tried to compile. I then got an error similar to this:

config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
make dep
make[1]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/usr/src/Alsa-1.0.19/alsa-driver-1.0.19'
make[2]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/usr/src/Alsa-1.0.19/alsa-driver-1.0.19/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #2 FAILED at 155.
Hunk #3 succeeded at 162 (offset -5 lines).
Hunk #4 succeeded at 172 (offset -5 lines).
Hunk #5 succeeded at 203 (offset -5 lines).
Hunk #6 succeeded at 490 (offset -5 lines).
Hunk #7 FAILED at 530.
Hunk #8 FAILED at 994.
Hunk #9 succeeded at 1018 (offset -10 lines).
3 out of 9 hunks FAILED -- saving rejects to file info.c.rej
make[2]: *** [info.c] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[2]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/usr/src/Alsa-1.0.19/alsa-driver-1.0.19/acore'
make[1]: *** [dep] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/usr/src/Alsa-1.0.19/alsa-driver-1.0.19'
make: *** [include/sndversions.h] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
alsa-driver-1.0.19 make failed

I contacted the alsa dev's and they had me do several different diagnostics. They then suggested using the latest snapshot found here: [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.bz2](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.bz2)

I was finally able to compile this snapshot, restart (using the following in my alsa base):
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=m4

Once up, I made sure the audio was not muted and behold, SOUND :) :)

I hope this helps someone.

-Jesse

---

### Post by topcoder on 2009-04-18
@mal2104
The problem in Jaunty is solved if you use the latest alsa driver [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090415.tar.bz2](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090415.tar.bz2)
Then the steps are same as mentioned by jstalnak in the beginning of this thread.

---

### Post by BadgerKid on 2009-04-23
Interesting. Until a few days ago, sound on my dv5z "just worked".  Apparently an update to alsaplayer-alsa 0.99.80-3ubuntu1, alsaplayer-gtk 0.99.80-3ubuntu1, alsaplayer-common 0.99.80-3ubuntu1 borked my sound (i.e., speaker could be made to work by plugging in the headphones). 

I'll look into this new alsa-driver.

---

### Post by And1945 on 2009-04-26
Sorry to say...

I am having a hard time understanding how this works, because I do not have an intel chipset. I have an AMD/ATI something I cant recall. Even though it specificly specifies "intel" in the line ...

A little note, I had to add ".conf" and change vim to gedit :)

But none the less, it works.

Thanks!

---

### Post by manolis_nestor on 2009-04-26
Hi.
I had a problem. NO SOUND from my Pavilion DV6 laptop. The laptop works perfect with UBUNTU 8.10 Everething WAS PERFECT (sound, web camera, bluetooth, graphics, cd-rom) I had only a small problem with camera's mic , but it was ok to me.
After upgrade the new release ( 9.02 ) there was **no sound** at all. If I press esc during boot and choose **2.6.27-11** generic kernel then the **sound works fine**, but cpu works only at the maximum speed. By choosing the **2.6.28-11** option, the sound **does not work** but CPU clock changes to consume buttery power (on demand option). So, I have to choose between sound or cpu_power_save.

---

### Post by And1945 on 2009-04-27
Uhm... now I get no sound from my headphones.

Does it matter that I do not have an intel chipset? My soundcard is called IDT something.

---

### Post by DaneGrinder on 2009-04-27
Hi.

Totally new to Linux.

I have a HP DV7 and when I installed Ubuntu 8.1 I had "bongo drums" from the login page. After it bootet into the OS i was still there just had to turn the volume up to 100% to hear it. (By Bongo drums I mean, it sounds like a bongo drum beeing hit rapidly)

Then I tried 9.02 and now the "bongo drums" goes away after a little while, but still no sound.

This is both in the build in speakers and the headphone jack.

SO, I tried what was decriped in the first post in this thread. BUT my alsa-base file is completly empty... Seeing that all of you say "add this 'XXXX' at the end of the file" I'm guessing it's not suppose to be empty?

Do I reinstall?
And when this bug has been known for some time, why isn't it fixed in 9.02?
------------------------------------
Hope you understand my english

---

### Post by webs37 on 2009-04-27
Same problem as above, in my CQ40-401AU use Ubuntu 9.04 with AMD Turion X2 Mobile Processor RM-74 - 2x 2.2 GHz

first download [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090428.tar.bz2](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090428.tar.bz2)
try the new  alsa-driver-*tar.bz2

and use sudo privileges

```
#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo gedit /etc/modprobe.d/alsa-base.conf
```add "options snd_hda_intel model=hp-dv5" in the end of this
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd_hda_intel model=hp-dv5
```

save and sudo reboot

but its only work for internal speakers, thanks for u all and I hope there anyone can do more for the external speaker.

---

### Post by And1945 on 2009-04-28
> **dep01 said:**
> Hello everyone. I have a HP Pavilion 1275mx and doing the following solved it:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

add the following to the end of the file.

```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1
```

Cheers,
dep

This works on my DV5-1150eo. Thank you very much!!!

---

### Post by And1945 on 2009-04-28
whoops... sorry.

---

### Post by ashim.dubey on 2009-04-29
Hi,

I have Ubuntu 9.04 Ubuntu on my laptop Compaq CQ45-106AU and I have no sound over my internal speakers though I do get sound over my earphones jack. Since I am very new to linux, I can't get the hang of the commands people have given in this discussion. It would be great if someone could explain me these steps in a simple step-by-step procedure.

Here's my lspci output:

python@The-Black-Pearl:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Any help would be welcome..

Thanks in advance!!

---

### Post by MadJester on 2009-04-30
Thank you, thank you, thank you...

I have an HP DV7T.

I compiled the driver snapshot, added the line "options snd_hda_intel model=hp-dv5" to alsa-base.conf and I had sound upon reboot.

Great thread!

---

### Post by topcoder on 2009-04-30
@ashim.dubey
Hi,
I also have the same laptop. I would recommend you to download the alsa driver snapshot I mentioned in my previous post. Then untar it, and open a terminal in the untarred folder. There with super-user permissions(su) enter the following commands in exact order

./configure --enable-dynamic-minors
make
make install-modules

After this, open the file /etc/modprobe.d/asla-base (still as super user) with the command

gedit /etc/modprobe.d/alsa-base

and add the following line to the end of the file

options snd_hda_intel model=hp-dv5

then save the file and restart your computer. Your sound card should be working fine. However, the internal microphones still do not work, and you shall have to use an external mic. Hope this solves your problem. By the way, my BIOS veersion is F.36. Please ensure that you have the latest BIOS version or update it from the Compaq site. However, you shall have to be in Windows to do this. Do reply on the forum if you find these instructions unclear.

---

### Post by ashim.dubey on 2009-04-30
@topcoder

The driver snapshot you suggested [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090415.tar.bz2](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090415.tar.bz2) says 404 not found. Should I try the snapshot given in the reply just above yours??

---

### Post by ashim.dubey on 2009-04-30
I checked my BIOS version and it's same as yours F.36. I could not download the driver snapshot you suggested [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090415.tar.bz2](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090415.tar.bz2) so I downloaded the snapshot [http://ftp.kernel.org/pub/linux/kern...090428.tar.bz2](http://ftp.kernel.org/pub/linux/kern...090428.tar.bz2).

But after I untarred the folder on my desktop and after I type the command
sudo ./configure --enable-dynamic-minors, i get the following error:

sudo: ./configure: command not found

What do I do?

---

### Post by ashim.dubey on 2009-05-01
@topcoder

I'm sorry I was configuring from inside the wrong folder. I got my speakers working!! Thanks a lot!! It feels so good that my internal speakers are working on ubuntu!! Thanks again!!

---

### Post by topcoder on 2009-05-01
@ashim.dubey
I realise that. I too tried unsuccessfully many times before I came upon this solution. Just one more thing, you need to do this everytime your linux kernel is upgraded. However, in that case you shall need to download the latest snapshot.

---

### Post by frncz on 2009-05-01
This is great. Sounds now work. Many thanks

---

### Post by ashim.dubey on 2009-05-02
@topcoder

I'll do that. But from where shall I get new snapshots of the drivers??

---

### Post by topcoder on 2009-05-02
@ashim.dubey
I got the snapshot from here:
[http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/)
> **ashim.dubey said:**
> But from where shall I get new snapshots of the drivers??

---

### Post by hubriz on 2009-05-02
> **jstalnak said:**
> ... the alsa developers have a solution for this issue:

When you boot you get no sound from your internal laptop speakers though you do get sound from the headphone jack. 

 The cause, according to some alsa developers, is an incorrect 'pin' assignment (in the BIOS, perhaps) whereby sound output meant for the internal speakers gets routed to the wrong place.

If you have an HP dv4, dv5, and perhaps a dv7 model series laptop, you may have this issue.

The latest alsa-driver snapshot provides a fix for this issue. I'm listening to a Keith Jarrett jazz cd right now through the internal speakers of my HP Pavilion dv4 1225 laptop after downloading, compiling, and installing the latest snapshot.  You can get it here:

[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)

After downloading and gzip/tarring the files, you'll need sudo privileges to:

```
#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
#> sudo reboot
```After restart, you should have sound from the laptop speakers.

If you do not, you should consider the alsa developers your best resource. They have some tools you can use to discover what's happening and since they write the code that goes into the kernel for the sound drivers, they can hopefully fix your problem.  Just go to the alsa web site and find the alsa-devel email list and join up.  

NOTE: this does not require a kernel build :-)  I post this to the ubuntu forum with the permission of several of the alsa developers I've been working with.

Will this work on COMPAQ PRESARIO CQ40 Laptops?

---

### Post by Foxbat250 on 2009-05-02
Thanks jstalnak

It worked perfectly in my HP dev5. before, I was almost thinking that the speakers are broken!!!

This happens just if you make a new installation of Ubuntu 9.04. Otherwise, if you upgrade your 8.10, this problem couldn't happen.

Ciao

---

### Post by ron66 on 2009-05-03
> **dep01 said:**
> Hello everyone. I have a HP Pavilion 1275mx and doing the following solved it:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

add the following to the end of the file.

```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1
```

Cheers,
dep

Thanks. Worked for me on a HP Pavilion dv6t-1000. However my system does not have the file /etc/modprobe.d/alsa-base, only /etc/modprobe.d/alsa-base.conf, so I edited it instead. After reboot I had SOUND!

---

### Post by Fughley on 2009-05-04
Hey there 
I have a HP DV^-1030us and it sounds like we are having the exact same problem, did you get the sound to work?

---

### Post by uhappo on 2009-05-05
I have HP Pavilion dv5-1035-eo

All I did was ```

gksudo gedit /etc/modprobe.d/alsa-base.conf
```

```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
```

Nothing else, and after reboot sound works, wuhuu!!!

Immediately laptop mic is working also!

---

### Post by flavanoid on 2009-05-07
I have a dv7-2040us and I upgraded alsa to 1.0.20 using instructions here:

 [http://monespaceperso.org/blog-en/2009/05/01/upgrade-alsa-1019-on-ubuntu-jaunty-904/]("http://monespaceperso.org/blog-en/2009/05/01/upgrade-alsa-1019-on-ubuntu-jaunty-904/")

Then I added the model=hp-dv5 stuff to the alsa-base file and all was good!

I don't know if upgrading alsa was necessary but I did it before I found this thread!

Thanks and I hope this helps someone out!

Edit* The upgrade to alsa 1.0.20 is necessary!

---

### Post by kgas on 2009-05-08
options snd_hda_intel model=hp-dv5

this option worked fine on **hp dv5 1145ee** laptop.

```

here is the lspci | grep -i audio output

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]

The processor is AMD ( AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-84)


```

This is for the confirmation and any one with the same laptop can resolve this issue.

Note: in Jaunty the file to be edited is  /etc/modprobe.d/alsa-base.conf 


Thanks to OP

---

### Post by ehabh on 2009-05-10
Thanks a million really this worked very well on my HP DV6-1125ee notebook.


> **webs37 said:**
> Same problem as above, in my CQ40-401AU use Ubuntu 9.04 with AMD Turion X2 Mobile Processor RM-74 - 2x 2.2 GHz

first download [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090428.tar.bz2](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090428.tar.bz2)
try the new  alsa-driver-*tar.bz2

and use sudo privileges

```
#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo gedit /etc/modprobe.d/alsa-base.conf
```add "options snd_hda_intel model=hp-dv5" in the end of this
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd_hda_intel model=hp-dv5
```

save and sudo reboot

but its only work for internal speakers, thanks for u all and I hope there anyone can do more for the external speaker.

---

### Post by ehabh on 2009-05-11
As in above your solution got me working, on my DV6-1125ee but i logged in KDE rather than gnome and there was no sound. I rebooted and still no sound. I redid the installation of the modules and rebooted and still no sound. 

This is really frustrating to get sound only once. Can you think of why this happended?

---

### Post by ehabh on 2009-05-11
Ok now fixed and stable across at least one reboot by doing above BUT


changing to 
options snd-hda-intel model=hp-m4 enable_msi=1


> **ehabh said:**
> As in above your solution got me working, on my DV6-1125ee but i logged in KDE rather than gnome and there was no sound. I rebooted and still no sound. I redid the installation of the modules and rebooted and still no sound. 

This is really frustrating to get sound only once. Can you think of why this happended?

---

### Post by ehabh on 2009-05-11
Take care to set volume of speaker in alsa-mixer.

---

### Post by MrPapersHead on 2009-05-12
Thank you so much for posting this. Really excited to be able to find a way to have sound on my laptop.

Having a slight issue though. Trying to use the newest alsa drivers, downloaded from the main alsa page. When I gzip the file, it says:
mrtheplague@Portable-Plague:~/src/alsa$ tar -xvpf alsa-driver-1.0.20.tar.bz2.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors


```
~/src/alsa$ tar -xvpf alsa-driver-1.0.20.tar.bz2.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors

```

Am I missing a step? Doing something incorrectly? I am rather new to everything and was hoping someone could point me in the right direction. Thanks.

---

### Post by MrPapersHead on 2009-05-12
So I am a dork and figured out how to properly unzip the file. Continuing through the install process I still run into:

```
~/src/alsa/alsa-driver-1.0.20$ make
make dep
make[1]: Entering directory `/home/mrtheplague/src/alsa/alsa-driver-1.0.20'
make[2]: Entering directory `/home/mrtheplague/src/alsa/alsa-driver-1.0.20/acore'
copying file alsa-kernel/core/info.c
/home/mrtheplague/src/alsa/alsa-driver-1.0.20/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/mrtheplague/src/alsa/alsa-driver-1.0.20/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/mrtheplague/src/alsa/alsa-driver-1.0.20'
make: *** [include/sndversions.h] Error 2
mrtheplague@Portable-Plague:~/src/alsa/alsa-driver-1.0.20$ 

```

Any reason for the error codes?

Thanks again.

---

### Post by uhappo on 2009-05-13
Why not try just adding a proper line to .conf-file?

My sound came alive just by adding lines, no alsa updates etc

---

### Post by MrPapersHead on 2009-05-13
That would have been a far simpler solution. Tried appending that and still received no sound. Realized my sound card is no longer being recognized:

```
mrtheplague@Portable-Plague:~$ aplay -l
aplay: device_list:217: no soundcards found...

```

Then I followed the help documentation to reinstall the modules and ran this command:

```
sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
```

It found nothing:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-11-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-11-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```


EDIT: Need to not do this while tired apparently. Missed the whole uname = username part. Even adjusting that, it still does not find any modules.

---

### Post by jstalnak on 2009-05-13
MRPAPERSHEAD:

One of the things you run into when compiling software is whether or not you have all the components of a build environment.  Those are the compilers and ancillary applications, like patch.  I read your error to say that the application 'patch' cannot be found.  I believe that there is an earlier post where someone describes what he had to do to compile the alsa drivers (which includes needed applications). Alternatively, you can use a package manager that organizes packages by type and do an install (or reinstall) of a development environment.

Regards.

---

### Post by nallen00 on 2009-05-17
Hello everyone.  Long time stalker, first time poster.

Firstly, big thanks to [[COLOR=Blue]_jstalnak_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6753560#post6753560") for putting in the initial footwork on this issue.  Following his instructions, I ran into the same errors outlined earlier by [[COLOR=Blue]_Binary Bandit_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7076608#post7076608"), and since he never actually describes what the "patch" is or where to find it, I did a little searching on my own and ended up with the following solution:


[LIST]
[*]Open the terminal and run the following command (this will fix the "patch" issue described by [[COLOR=Blue]_Binary Bandit_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7076608#post7076608")):
[/LIST]
```
#> sudo apt-get install build-essential
```
[LIST]
[*]Locate the latest alsa snapshot [[COLOR=Blue]_HERE_[/COLOR]]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/") (file should end with *.tar.gz);
[*]Download the archive;
[LIST]
[*]Right-click the archive and select "Extract Here" (this will create a folder named "alsa-driver" or "alsa-driver-unstable" depending on the version you downloaded)...
[*]Right-click this folder and select "Open in Terminal" (if you don't see this option, install "nautilus-open-terminal" from the Synaptic Package Manager)...
[/LIST]
 
[*]In the terminal, simply follow the commands outlined by [[COLOR=Blue]_jstalnak_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6753560#post6753560") (replacing "vim" with "gedit" as highlighted):
[/LIST]
```
#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo [COLOR=Red]**vim**[/COLOR] /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
#> sudo reboot
```Sound is now working 100% on my dv5-1235dx using the [[COLOR=Blue]_17-May-2009_[/COLOR]]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz") unstable snapshot, internal mic included.  I tried [[COLOR=Blue]_dep01's_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6860920#post6860920") solution, but had to crank the volume to hear anything, and was still missing system sounds.  I appreciate his help, but this didn't seem to actually fix the problem, and it only takes a couple minutes longer to perform a proper driver install.

Thanks again everyone.  Hope this helps...

---

### Post by DNAtsol1 on 2009-05-18
thanks nallen00 & jstalnak! 

I had the same compiling problem noted by MRPAPERSHEAD. This solution worked for me on a HP dv5. I now can get on with completing my exit from VISTA!

Thanks everyone on the boards and the ALSA dev team for keeping on this issue.

---

### Post by MrPapersHead on 2009-05-20
Thank you so much everyone for all of your help and advice. I have sound again =). Now to deal with the battery not displaying.

---

### Post by uhappo on 2009-05-22
> **MrPapersHead said:**
> Thank you so much everyone for all of your help and advice. I have sound again =). Now to deal with the battery not displaying.

So what did you do? ALSA upgrade, or just adding proper lines to conf?

---

### Post by MrPapersHead on 2009-05-27
> **uhappo said:**
> So what did you do? ALSA upgrade, or just adding proper lines to conf?

Actually wiped the drive completely and reinstalled 8.10. Sounds card was once again recognized, but not on and working. Appended the lines to the conf file and got sound....but it sounded really grainy, almost midi quality.

Updated to 9.04 and then did the ALSA upgrade using the code string nallen00 listed. No errors appeared, and sounds is great now. =). 

Probably an over-dramatic reaction to get it to work, but I needed a small amount of drive space for Vista so HP tech would actually help me with the battery issue.

---

### Post by tigars on 2009-05-29
Nothing of the previous worked for me but I found the solution through this: [http://www.box.net/shared/454ic17as0](http://www.box.net/shared/454ic17as0) to see far [http://ubuntuforums.org/archive/index.php/t-1013750.html](http://ubuntuforums.org/archive/index.php/t-1013750.html).

There is still one problem, my headphones don't work so I have to activate them. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870).

I have HP DV6 1124, AMD Athlon X2 64 with Jaunty.

---

### Post by ricardog7 on 2009-05-31
> **nallen00 said:**
> Hello everyone.  Long time stalker, first time poster.

Firstly, big thanks to [[COLOR=Blue]_jstalnak_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6753560#post6753560") for putting in the initial footwork on this issue.  Following his instructions, I ran into the same errors outlined earlier by [[COLOR=Blue]_Binary Bandit_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7076608#post7076608"), and since he never actually describes what the "patch" is or where to find it, I did a little searching on my own and ended up with the following solution:


[LIST]
[*]Open the terminal and run the following command (this will fix the "patch" issue described by [[COLOR=Blue]_Binary Bandit_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7076608#post7076608")):
[/LIST]
```
#> sudo apt-get install build-essential
```
[LIST]
[*]Locate the latest alsa snapshot [[COLOR=Blue]_HERE_[/COLOR]]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/") (file should end with *.tar.gz);
[*]Download the archive;
[LIST]
[*]Right-click the archive and select "Extract Here" (this will create a folder named "alsa-driver" or "alsa-driver-unstable" depending on the version you downloaded)...
[*]Right-click this folder and select "Open in Terminal" (if you don't see this option, install "nautilus-open-terminal" from the Synaptic Package Manager)...
[/LIST]
 
[*]In the terminal, simply follow the commands outlined by [[COLOR=Blue]_jstalnak_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6753560#post6753560") (replacing "vim" with "gedit" as highlighted):
[/LIST]
```
#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo [COLOR=Red]**vim**[/COLOR] /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
#> sudo reboot
```Sound is now working 100% on my dv5-1235dx using the [[COLOR=Blue]_17-May-2009_[/COLOR]]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz") unstable snapshot, internal mic included.  I tried [[COLOR=Blue]_dep01's_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6860920#post6860920") solution, but had to crank the volume to hear anything, and was still missing system sounds.  I appreciate his help, but this didn't seem to actually fix the problem, and it only takes a couple minutes longer to perform a proper driver install.

Thanks again everyone.  Hope this helps...


Hi guys

I'm new in ubuntu. I'm using Ubuntu 9.04 in a HP DV5-1235dx laptop.

When I just installed Ubuntu on my laptop my sound didnt work so I fixed it adding this lines to my alsa-base file.

options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel

This fixed my sound problem but my microphone still didn't work. Recently I was looking for a solution to the mic issue and tried the solution above. The result: NO mic and...  NO SOUND :(.

When I go into System -> Preferences -> Sound... Default Mixer Tracks Section I got "Playback: Null Outuput (Pulse Audio Mixer)".

The alsa snapshot that I used to fix the problem was [COLOR=Navy]***[this]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-20090531.tar.gz")***[/COLOR], then repeated the process  using the [[COLOR=Blue]_17-May-2009_[/COLOR]]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz") unstable snapshot as mentioned above but the problem persists.

So, now I dont care about the mic issue, I just want to get my audio back LOL. Is there any way to rollback the process I did and get my original driver? or what can I do to get my audio back?? I just dont want to re-install ubuntu again.

Any suggestions???

Thank you very much.

---

### Post by eigenman on 2009-05-31
Just want to report that this solution worked perfectly for my DV2-1028 (Azalia chipset, codec IDT 92HD75B2X5). I'm curious, when will this make it back in the distribution? 

Also, as a side note, the sound was working fine in 8.10, and only after the upgrade the problem started showing up. So, an alternative solution for the sound, is to downgrade to 8.10 (my video playback had issues in Ipex, but for some of you, that might not be an issue).

Thanks again,
Eigenman

---

### Post by Bill Zimmerly on 2009-06-08
> **uhappo said:**
> I have HP Pavilion dv5-1035-eo

All I did was ```

gksudo gedit /etc/modprobe.d/alsa-base.conf
``````
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
```Nothing else, and after reboot sound works, wuhuu!!!

Immediately laptop mic is working also!

> **flavanoid said:**
> I have a dv7-2040us and I upgraded alsa to 1.0.20 using instructions here:

 [http://monespaceperso.org/blog-en/2009/05/01/upgrade-alsa-1019-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/01/upgrade-alsa-1019-on-ubuntu-jaunty-904/)

Then I added the model=hp-dv5 stuff to the alsa-base file and all was good!

I don't know if upgrading alsa was necessary but I did it before I found this thread!

Thanks and I hope this helps someone out!

Edit* The upgrade to alsa 1.0.20 is necessary!

[SIZE=4]Thanks Guys! This is what I needed to solve my system's audio problem! I also learned some new BASH tricks from the website that you referenced, flavanoid.[/SIZE] ;)

---

### Post by commonmanthemes on 2009-06-17
Hey everyone...  Maybe someone has experienced this with this solution.  I could use some help.

I have a dv4-1225dx (AMD platform) and followed the original solution exactly.  It solved the issue of no sound coming through my speakers, but now my mute button doesn't work properly.  The light is always white (on), though Ubuntu's notifier shows mute going on and off.  However, the speakers never turn off.  In addition, plugging headphones in does not mute the laptop speakers.

Any ideas?

---

### Post by mr_raider on 2009-06-20
I just upgraded kernels and the sound stopped working again. Do I need to recompile from the tarball again and re-install?

---

### Post by ertayone on 2009-06-20
Nullen00's solution worked perfectly for my dv6-1030us :)

---

### Post by pyrox_pro on 2009-06-26
I did what was suggested, rebooted, and my laptop speakers are working now, sweet.

HP DV7T w/ATI 512mb

However, my headphones are not working, I plug them in and sound continues to come out of the laptop speakers.

Also confusing to me, is that I didn't have /etc/modprobe.d/alsa-base, instead I see /etc/modprobe.d/alsa-base.conf. 

I added: options snd_hda_intel model=hp-dv5 to both files anyway.

---

### Post by pyrox_pro on 2009-06-26
Now I have headphones working, via a shell script to switch from speakers to headphones, and back again:

I got this here:
[http://ubuntuforums.org/archive/index.php/t-1136670.html](http://ubuntuforums.org/archive/index.php/t-1136670.html)

A post by RangerX_308

Note that the port replicator doesn't seem to work as he notes.

> Upgrade ALSA to 1.0.20 per [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
 Reboot. Sound should be working from speakers at this point.
 Create a folder in your Home directory with a name like .audiofix
 In terminal browse to your new directory
 Download & install hda-verb:wget -c [ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz](ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz)
tar xvzf hda-verb-0.3.tar.gz
cd hda-verb-0.3
sudo apt-get update
sudo apt-get install build-essential
make

 Move the file to your .audiofix directory
 cp hda-verb ~/.audiofix
 You can now delete the remaining hda-verb-0.3 files & directory if you wish
You now need to "activate" your headphones with the following command. sudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0f SET_CONNECT_SEL 1 You should now have sound out of speakers AND headphones.
 Now to create your scripts to switch between headphones & speakers.
 Using GEdit, create 2 new text files, one called Headphones.sh & one called Speakers.sh.
 For Headphones script, enter this code:gksudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0f SET_CONNECT_SEL 1
gksudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0f SET_PIN_WIDGET_CONTROL 0x40
gksudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0d SET_PIN_WIDGET_CONTROL 0 Note: the first line of this script is a repeat of the Headphone "activiation" code. This code needsto be run every time you reboot your system, so I put it in here.
 For Speakers script, enter this code:gksudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0f SET_PIN_WIDGET_CONTROL 0
gksudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0d SET_PIN_WIDGET_CONTROL 0x40
 Now create some application launchers for your scripts & you are all set.

Info for this "fix" found here-
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870)
[http://ubuntuforums.org/showthread.php?t=984081&page=2](http://ubuntuforums.org/showthread.php?t=984081&page=2)

While this workaround gives me headphones, I still can't figure out how to get the line out on my docking station to work. If anyone figures that out, please reply to this thread.

---

### Post by Khaled Khalil on 2009-06-29
thanks jstalnak very much :KS


> #> sudo reboot
it was enough to
```
$ sudo alsa force-reload
```

---

### Post by nallen00 on 2009-07-01
> **ricardog7 said:**
> I'm using Ubuntu 9.04 in a HP DV5-1235dx laptop...
The steps outlined in my previous post should work, but I'm guessing that you already have at least one conflicting "solution" in place.  Sooo...let's try starting with a clean slate:

[LIST]
[*]Open the Synaptic Package Manager, select "Multimedia" in the left pane, and mark "alsa-base" for complete removal.  Apply and reboot;
[*]Open a terminal and run the following command (this will replace the above package, and related packages, with their defaults):```
#> sudo apt-get install ubuntu-desktop
```
[*]Reboot and try again.
[/LIST]
 Hope this helps. Tried it myself for giggles, and again, sound is working flawlessly ;)

---

### Post by ertayone on 2009-07-03
Hey guys,

Today after restarting my computer I did the usual fix and this happened:

```
~/hda-verb-0.3$ sudo hda-verb /dev/snd/hwC0D0 0x0f SET_CONNECT_SEL 1
open: No such file or directory
```

I checked my /dev/snd/ directory and sure enough, there aren't any hw files. Should I reinstall ALSA or something?

---

### Post by edsellsstuff on 2009-07-07
Hi, everyone, new to the forum. I had the same problem with no sound with a Compaq Presario CQ40. It has the IDT 92HD71B7X 0, LSI ID1040 and Itel G45 DDEV CTG.

I made the following changes as recommended here in the forum within the alsa-base.conf file located in etc/modprob.d folder:
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1
Thanks for the help everyone and did not need to download the recently announced patch for the alsa-drivers.
PS: I did. but received config error trying to load for some reason. This was a lot easier

---

### Post by schievelbein on 2009-07-09
Thanks to everyone working on this issue.
I have a DV7-2043.
I have followed the instructions listed here and have the sound working..SORTA.
When I play a file, the music is coming out of what sounds like the bade speaker on the bottom and not the main speakers.  Everything sounds real muffled and I have to have everything in the ALSAmixer cranked up to maximum to even hear anything.  Additionally, it sounds like everything is echoing.  Any suggestions?


> **nallen00 said:**
> Hello everyone.  Long time stalker, first time poster.

Firstly, big thanks to [[COLOR=Blue]_jstalnak_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6753560#post6753560") for putting in the initial footwork on this issue.  Following his instructions, I ran into the same errors outlined earlier by [[COLOR=Blue]_Binary Bandit_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7076608#post7076608"), and since he never actually describes what the "patch" is or where to find it, I did a little searching on my own and ended up with the following solution:


[LIST]
[*]Open the terminal and run the following command (this will fix the "patch" issue described by [[COLOR=Blue]_Binary Bandit_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7076608#post7076608")):
[/LIST]
```
#> sudo apt-get install build-essential
```
[LIST]
[*]Locate the latest alsa snapshot [[COLOR=Blue]_HERE_[/COLOR]]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/") (file should end with *.tar.gz);
[*]Download the archive;
[LIST]
[*]Right-click the archive and select "Extract Here" (this will create a folder named "alsa-driver" or "alsa-driver-unstable" depending on the version you downloaded)...
[*]Right-click this folder and select "Open in Terminal" (if you don't see this option, install "nautilus-open-terminal" from the Synaptic Package Manager)...
[/LIST]
 
[*]In the terminal, simply follow the commands outlined by [[COLOR=Blue]_jstalnak_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6753560#post6753560") (replacing "vim" with "gedit" as highlighted):
[/LIST]
```
#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo [COLOR=Red]**vim**[/COLOR] /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
#> sudo reboot
```Sound is now working 100% on my dv5-1235dx using the [[COLOR=Blue]_17-May-2009_[/COLOR]]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz") unstable snapshot, internal mic included.  I tried [[COLOR=Blue]_dep01's_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6860920#post6860920") solution, but had to crank the volume to hear anything, and was still missing system sounds.  I appreciate his help, but this didn't seem to actually fix the problem, and it only takes a couple minutes longer to perform a proper driver install.

Thanks again everyone.  Hope this helps...

---

### Post by jjwoznia on 2009-07-26
Hey, just wanted to let everyone know that the method from the first post worked perfect on a HP Pavilion DV2-1030us. 

Thanks a bunch!!!

---

### Post by joseinbaraj on 2009-07-26
> **dep01 said:**
> Hello everyone. I have a HP Pavilion 1275mx and doing the following solved it:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

add the following to the end of the file.

```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1
```

Cheers,
dep



thanks a lot .. i was in trouble for the last four month ..

now i am able to hear the sound in my internal speaker  , but there is no sound through my headphone and micro phone ..:(

can  someone help ??


My machine is  :Compaq cq40 - 145 tu

---

### Post by Sardonism on 2009-07-31
Hey guys, I just upgraded my kernel from 2.6.28-13 to 2.6.28-14 and I get these errors while making:

```
tyler@tyler-laptop:~/Desktop/alsa-driver$ make
if [ ! -d include/sound -a ! -L include/sound ]; then \
      ln -sf ../alsa-kernel/include include/sound ; \
    fi
cp -puvf include/version.h include/sound/version.h
make dep
make[1]: Entering directory `/home/tyler/Desktop/alsa-driver'
if [ ! -d include/sound -a ! -L include/sound ]; then \
      ln -sf ../alsa-kernel/include include/sound ; \
    fi
cp -puvf include/version.h include/sound/version.h
make[2]: Entering directory `/home/tyler/Desktop/alsa-driver/acore'
copying file alsa-kernel/core/info.c
/home/tyler/Desktop/alsa-driver/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/tyler/Desktop/alsa-driver/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/tyler/Desktop/alsa-driver'
make: *** [include/sndversions.h] Error 2

```Anyone know a fix for the new kernel?  It worked just fine before i upgraded, now it wont even make... :(

---

### Post by alex2311 on 2009-08-01
Thanks [COLOR=Black]jstalnak [/COLOR]and nallen00 worked for me on a dv7-2070.

---

### Post by Xac1909 on 2009-08-02
> **jstalnak said:**
> ... the alsa developers have a solution for this issue:

When you boot you get no sound from your internal laptop speakers though you do get sound from the headphone jack. 

 The cause, according to some alsa developers, is an incorrect 'pin' assignment (in the BIOS, perhaps) whereby sound output meant for the internal speakers gets routed to the wrong place.

If you have an HP dv4, dv5, and perhaps a dv7 model series laptop, you may have this issue.

The latest alsa-driver snapshot provides a fix for this issue. I'm listening to a Keith Jarrett jazz cd right now through the internal speakers of my HP Pavilion dv4 1225 laptop after downloading, compiling, and installing the latest snapshot.  You can get it here:

[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)

After downloading and gzip/tarring the files, you'll need sudo privileges to:

```
#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
#> sudo reboot
```

After restart, you should have sound from the laptop speakers.

If you do not, you should consider the alsa developers your best resource. They have some tools you can use to discover what's happening and since they write the code that goes into the kernel for the sound drivers, they can hopefully fix your problem.  Just go to the alsa web site and find the alsa-devel email list and join up.  

NOTE: this does not require a kernel build :-)  I post this to the ubuntu forum with the permission of several of the alsa developers I've been working with.

Ante todo pido mil disculpas ya que no escribo bien en ingles pero si lo leo, quiero expresar mi agradecimiento a todos por esta solucion ya que dure muchos dias buscando y leyendo hasta que por fin la consegui esto funciona perfectamente para una HP PAVILION DV6-1030US, de nuevo mil gracias!! the next time i will try to writte in english

---

### Post by Askar450 on 2009-08-03
Does anyone know how to make this work on a Gateway P-6831FX? cat /proc/asound/card0/codec#* | grep Codec shows I have the IDT 92HD71B8X, I've tried all of the models listed but none work just the headphones. I'm using Ubuntu 9.04 32-bit with the latest ALSA driver 1.0.20 any advice would be appreciated or where too look for the problem.

---

### Post by kamaleon75 on 2009-08-04
edit the file with the next command

gksudo gedit /etc/modprobe.d/alsa-base.conf

add this lines at end of the file

```
options snd slots=snd-hda-intel,snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1
```

sound work fine at dv4-1213la with ubuntu 9.04 hope help to more people to fix this issue with sound speakers.

---

### Post by Askar450 on 2009-08-05
Not sure if that was for me kamaleon75 but I tried it anyways and it didn't work :/ this is killing me. Any other advice is welcome ; ;

---

### Post by Askar450 on 2009-08-05
Nvm... I had 1.0.19 I installed 1.0.20 and they work now...d(^0^)b you rock dude. Now to figure out how to increase the volume without getting distorted.

---

### Post by ramidavis on 2009-08-05
Thanks to this topic, I was able to get sound on my HP Pavilion dv7-2185dx. However, I still have no mic, and sound is output through headphone and speakers at same time. The dv7-2185dx has two headphone jacks, i tested the one nearest the dvd drive, when i switched to the other jack, i lost headphone *and* speaker sound. Have to reboot for sound to work when that happens.

---

### Post by talonx on 2009-08-08
Hi,

First, I would like to say thank you for all the contribution from everyone. I tried all the codes from this thread but it still doesn't work. I have a laptop dv6-1050US. I don't know if my dv6 is different somehow to dv4, dv5, and dv7.

---

### Post by alvaro00 on 2009-08-09
thanks a lot for this post, save my day i been looking for this for 2 weeks

---

### Post by joshjh on 2009-08-13
Im sorry i am new to Ubuntu. I have a HP dv7t and i have no sound. I downloaded the snapshot but im not sure what to do after that. I tried to enter the command in the screen shot on the first page but nothing happened. Please help.

---

### Post by topcoder on 2009-08-14
@joshjh:
This is what you must do. Copy the downloaded file to your home folder, and then right click on it and click on the 'extract here' option. This should create a folder called 'alsa-driver'. Then you should open a terminal (Applicaitions>Accessories>Terminal) and type in 
cd ./alsa-driver
./configure --enable-dynamic-minors
make
sudo make install-modules
sudo gedit /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
sudo reboot

After your computer has restarted, you can try typing in alsamixer in the terminal, and adjust the mixer levels to adjust the volume on your speakers. The default value is too low, and it would be better to increase that.

Hope that this was helpful.

---

### Post by MyOwnOwner on 2009-08-14
The method described by **jstalnak** worked on my [COLOR="Red"]HP Pavilion dv7 1018eg[/COLOR]. 
I followed the instrucions, the only thing I changed was the 4th. command from:
[COLOR="Yellow"]sudo vim /etc/modprobe.d/alsa-base[/COLOR] into
[COLOR="Red"]sudo nano /etc/modprobe.d/alsa-base.conf[/COLOR]

(The file names are different and I am using a different program, because vim is not installed)

Only the subwoofer doesnt work like it does on my Vista installation. But i donot care, even if the bass under Vista rocks ^^.

WOOHOOOO ! 
Thanks a lot ! !
Now I am finally independent from Vista ! ! !

---

### Post by kage52124 on 2009-08-14
Dep:

Your solution fixed my speaker issue (Pavilion dv5 1235dx)  Thank you SO MUCH!  Still working on fixing hibernation/standby issues, and that'll fix everything.

Kage

---

### Post by topcoder on 2009-08-15
This thread should fix all the known issues with HP-dvx laptops
[http://ubuntuforums.org/showthread.php?t=1079111](http://ubuntuforums.org/showthread.php?t=1079111)

---

### Post by joshjh on 2009-08-15
thanks i now have sounds, but i think its only mono, is there any way to fix that? seems like its coming out of the left speaker. Also i tried to play an AVI file and i got video but no sound. Any ideas?

---

### Post by Dreadlock man on 2009-08-15
Hi all, I've followed the steps given by webs37, jstalnak and others and now the sound works perfectly in my hp pavilion dv4-1413la, thanks a lot to all of you. 
I wonder  if anyone else has a problem with the mute button's light. It should be going red when I mute and going white when I unmute, but the thing is that is always white, however the mute control works fine. 

Thanks

---

### Post by michaeljbergin on 2009-08-17
I have an HP dv7-2180us and this solution worked.  I updated to the snapshot provided of the alsa-driver and added: options snd-hda-intel model=hp-dv5 and it works great.  Thank you very VERY much to the original poster

---

### Post by nu2u on 2009-08-19
Thanks nallen00! This has been bugging me all summer.

I have a hp dv6-1030us that was working fine with Gutsy. No sound since installing Jaunty until today.

I followed directions exactly but I did have to do one more thing:

In kmixer the master was muted but I didn't actually hear anything until I turned up the speaker level.

Thanks again!

---

### Post by Ozymandias' Broken Dreams on 2009-08-23
Hi,
Massive thanks to jstalnak (#1) and topcoder (#92)
Worked a charm for me (total newb)
and my dv5-1004ax.

---

### Post by satyrslynx on 2009-08-24
Thank you, Nallen00!! I am a complete Ubuntu n00b, but my husband convinced me to give it a go (read: formatted my brand new laptop & installed Ubuntu when I wasn't looking). It's ok, I didn't want Vista anyway (<shudder>)

Anyway, I have an HP dv6 and my sound wasn't working, either. Your directions were easy to follow, I only got hung up once, and that was when I didn't enter the command correctly.

Thank you, thank you, thank you! Now my spiffy laptop is spiffier!

---

### Post by 2optimize on 2009-09-25
> **dep01 said:**
> Hello everyone. I have a HP Pavilion 1275mx and doing the following solved it:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

add the following to the end of the file.

```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1
```

Cheers,
dep

adding this didn't help me anything.
I Have HP 6735s.

---

### Post by buknoii on 2009-09-25
hi there! im using an hp pavilion dv2 and i can hear some sound when im using a headphone i did the command below

```

#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
#> sudo reboot

```

and after doing it even the sound coming from my headphones disappeared.. but the weird thing is i hear a beep sound everytime i shutdown my laptop or if i use the terminal and if i press the left and right arrows i can hear a beeping sound.

can somebody help me with this.

---

### Post by weblinkbuilders on 2009-09-25
We've had so many issues with using any other OS apart from what has shipped with them (namely vista).

I heard that HP entered into an agreement with M/S to not provide support for any other OS apart from Vista.  I don't agree with that.

---

### Post by topcoder on 2009-09-26
The problem arising after installing the alsa snapshot could be because your mixer levels are turned low or muted. For this, please start alsamixer (terminal>alsamixer) and check the sound levels. Hope this solves the problem.

The fact about HP not supporting any other OS other than Vista(and 7 now) is true, and this can be confirmed by one call to their customer care number.

---

### Post by Velvet_Man on 2009-10-12
Thank you so much for posting this. After more than a month of trying other solutions that never made any difference, this one finally worked and I'm listen to music on my HP dv5-1334 as I type this.

One note for anyone else using Kubuntu Jaunty, I followed the instructions in the original post almost verbatim, but I had to change "sudo vim /etc/modprobe.d/alsa-base" to "sudo kate /etc/modprobe.d/alsa-base.conf".

---

### Post by Factoryworks on 2009-10-14
Also big thanks from myself to nallen00 and all the alsa-folks. It works great on my HP Pavilion DV6-1260sg. The file is called alsa-base.conf. Use model=hp-dv5 even for the dv6. I called alsamixer from the terminal afterwards to put all levels to max because I can reduce them afterwards in my apps.

---

### Post by Velvet_Man on 2009-10-22
I thought I should put an update in here.

I booted up my laptop this morning and found a few updates waiting for me. I can't remember exactly, but something about the linux kernal (when I boot up now the big string of numbers for the linux kernal version now ends in 16 instead of 15).

Anyway, I performed the update, rebooted, and was surprised to find I no longer had sound. Again.

So I performed these steps again (also the alsa-base.conf file already had the proper model listed this time).

But after a reboot, I now have sound again. I don't know why the update undid the changes from this tutorial, but it did.

---

### Post by BoneheadBarbarian on 2009-10-24
Thanks so much, I am a complete noob (15 mins in) and your walk through was easy to follow and has Worked!:P

I do have one question though: the speaker volume even at max is pretty soft, is there anyway I can increase the volume?

Thanks again man

---

### Post by BoneheadBarbarian on 2009-10-24
Please ignore my question, I was busy being an idiot.

---

### Post by topcoder on 2009-10-25
This is something that always occurs.... Every kernel recompilation kills the alsa update.

But how does it matter? All it takes is an occasional 5 minutes of work.

> **Velvet_Man said:**
> I thought I should put an update in here.

I booted up my laptop this morning and found a few updates waiting for me. I can't remember exactly, but something about the linux kernal (when I boot up now the big string of numbers for the linux kernal version now ends in 16 instead of 15).

Anyway, I performed the update, rebooted, and was surprised to find I no longer had sound. Again.

So I performed these steps again (also the alsa-base.conf file already had the proper model listed this time).

But after a reboot, I now have sound again. I don't know why the update undid the changes from this tutorial, but it did.

---

### Post by bhupsi on 2009-10-30
> **dep01 said:**
> Hello everyone. I have a HP Pavilion 1275mx and doing the following solved it:

```
gksudo gedit /etc/modprobe.d/alsa-base
```add the following to the end of the file.

```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1
```Cheers,
dep


This worked for me.  After loading karmic on my new HP G71 laptop I only had sound through headphones not through the internal speakers.  It all works now.  I noticed that Windows 7 was using the IDT audio Codec and not the Intel Codec but found no way to get IDT working under karmic.  It seems to be working fine with the above settings.  Thanks to the original poster.

---

### Post by topcoder on 2009-10-31
Guys,

I think I found a good solution to the sound issues. Just upgrade to Karmic. :)

All issues with sound on my laptop are resolved under Karmic. I have an IDT soundcard.

---

### Post by danastasio on 2009-10-31
Hiya everyone!
sadly none of the solutions listed on this massive thread helped me :( BUT! If you installed the "software modem" proprietary driver, remove it! apparently it has a nasty bug that makes your computer all unhappy and unable to play sound. But removing solves the problem :D

though on start i noticed that the volume was automatically muted, so to solve this install aumix
```
sudo apt-get install aumix
```

and add the following to your startup scripts
```
aumix -v 50
```

this will set the main volume on your computer to 50%

---

### Post by gamerman61 on 2010-01-06
It works but to get it to fully work I had to go into sound preferences and go to the Hardware tab, setting the dropdown to Analog Stereo Output. Thanks for the post. Did you know this is my first time in a forum? I guess that's why I'm a Linux newb. Good day everyone! :D

---

### Post by fiklein on 2010-01-10
I have a HP DV6-1030 that initially, after following the instructions in: [http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090) worked through the speakers but not the headphones. Using the most recent ALSA snapshot, sound now works in headphones and speakers.

---

### Post by opethfan89 on 2010-02-04
jstalnak,

THANK YOU SO MUCH! This work perfectly with my HP Pavillion DV7-3060US laptop, running Win 7 / Ubuntu 9.10 Karmic dual boot. For the longest time since installing 9.10 I couldn't play any music or watch videos, and now sound works perfectly!

Just one thing I should add to people reading this guide, unzip the files onto your desktop, then make sure to cd to that Desktop directory, code something like 'cd Desktop' and then cd again to the name of the folder, it should be like alsa-mixer.

Works great (volume is a LITTLE low but I'm sure I will figure that out) and I'm very happy, thanks SO much again!

---

### Post by topcoder on 2010-02-04
For volume, the default speaker volume is generally set low after the patch. Type in "alsamixer" (without the quotes) in terminal and increase the speaker volume to a comfortable level. BTW, I do not understand why the patch is required in Karmic at all... Almost all my issues with the sound card went away on the upgrade to Karmic.

---

### Post by opethfan89 on 2010-02-04
> **topcoder said:**
> For volume, the default speaker volume is generally set low after the patch. Type in "alsamixer" (without the quotes) in terminal and increase the speaker volume to a comfortable level. BTW, I do not understand why the patch is required in Karmic at all... Almost all my issues with the sound card went away on the upgrade to Karmic.


Thanks topcoder. I am aware of the alsamixer in terminal, and that is what I used to adjust my volume, although it would be nice if I were able to set the default volume for all applications across the board, so I don't have to keep tweaking with it. Hopefully, in Lucid this problem will be fixed.  Just want to state once again that I'm using an HP Pavillion DV7-3060US (brand new laptop manufactured just months ago) and this solved my problem. I DID change the code with options snd_hda_intel model=hpdv5 to dv7 to reflect my computers model, and it works great. Thanks again!

---

### Post by Gunnys on 2010-02-08
Fixed my DV7-3165dx... I wasn't getting audio from speakers or headphone jack. Thanks!!!

---

### Post by zhylas on 2010-02-14
Thanks a lot for this jstalnak! Now my HP Pavilion DV6-2070 works again. Wonderful :D

---

### Post by myromance123 on 2010-03-22
> **crazyMochi said:**
> The following steps will enable sound on the internal speakers for the HP dv4-1225dx

sudo gedit /etc/modprobe.d/alsa-base

Add the following lines:

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 

perform sudo reboot after saving your changes


Thank you, NaplesBill, for your posting on this fix!


I want to thank you very much crazyMochi, that solution worked wonders.
PS: when typing 'sudo gedit /etc/modprobe.d/alsa-base' I got a blank text editor. Nonetheless I pasted the following commands provided by crazyMochi and saved. Then performed the sudo reboot. It all works now :)

 You saved me seriously. 
*I'm using Xubuntu 9.10 on HP Laptop dv3500 with an IDT card ```
Codec: IDT 92HD71B7X
Codec: LSI ID 1040

```.

---

### Post by willseun on 2010-07-28
I downloaded using the link [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz) and following the information you gave on using sudo privileges/commands below. After reboot, i can't hear any sound again both from my internal speakers and my headphone. Please help me. It's urgent. My laptop is HP compaq 6730s
Many thanks
[EMAIL="willseun@gmail.com"]willseun@gmail.com[/EMAIL]


#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]

---

### Post by nate_nightroad on 2010-08-12
> **willseun said:**
> I downloaded using the link [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz) and following the information you gave on using sudo privileges/commands below. After reboot, i can't hear any sound again both from my internal speakers and my headphone. Please help me. It's urgent. My laptop is HP compaq 6730s
Many thanks
[EMAIL="willseun@gmail.com"]willseun@gmail.com[/EMAIL]


#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]

same here, i'm using ubuntu 10.04 64bit,FYI....

please help :)

---

### Post by Ethereal429 on 2012-07-02
> **dep01 said:**
> Hello everyone. I have a HP Pavilion 1275mx and doing the following solved it:

```
gksudo gedit /etc/modprobe.d/alsa-base
```add the following to the end of the file.

```
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1
```Cheers,
dep


This worked like a charm. I have a dv6 dx1245 and I wasn't getting any sound when I put through a new install. After researching different methods and coming up with nothing but failure. After applying this fix and rebooting, everything works just fine. Thanks for posting this, saves time and is way easier.

---

