---
title: "Alsa+Ubuntu+SBLIVE! 24Bit module CA0106 How?"
date: 2005-03-11
forum: Hardware &amp; Laptops
---

### Post by Jesterace on 2005-03-11
Well I've been a dedicated slackware user for quite sometime and I have the dreaded value SB Live! 24Bit!. I was able to get it to work in slackware after I compiled alsa from cvs. But sitting here with Ubuntu I am at a loss I get wierd errors and when I tried to remove the original Alsa package it said gnome would have to be removed as well as a dependancy. 

So this left me on a mission, if it would work in slackware well surely it would work in something newer. As well as I have come from a background of alternative win32 shells bleeding edge and crashes were something I'm used to so I decided to upgrade to Hoary and so far Hoary has given me no issues. As well these instructions will work on hoary since they depend on the hoary universe repositories. crimsum from these forums and irc was so kind to give me a hand with this problem. So I wrote the steps down for others to use.

1st Step - assuming you're running Hoary with the deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe uncommented in /etc/apt/sources.list

> sudo apt-get install build-essential fakeroot linux-headers-$(uname -r) alsa-source kernel-package

2nd Step - This will change you to the proper directory and decompress the alsasource.

> cd /usr/src/ && sudo tar jfx alsa-driver.tar.bz2 

3rd Step - This will allow you to configure the alsa source. 

> sudo dpkg-reconfigure alsa-source, and say no to PnP, yes to debug, and choose the ca0106 driver 

4th Step - Now it's time to make the Package

> cd modules/alsa-driver && sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r) 

5th Step -This will check for the package

> cd .. && ls *.deb 

here's my output

> alsa-modules-2.6.10-4-k7_1.0.8-4ubuntu1_i386.deb 

However if you notice I'm using a kernel for an Athlon processor so my driver package would be pretty useless for others to use unless you have the same kernel as I.

6th Step - Install the drivers (assuming you've stayed in the same directory this whole time.

> sudo dpkg -i *.deb 

7th Step - Time to install the drivers, However i had some strange messages with that package so what I had done now was to load the ca0106 module into the kernel like so. 

> sudo modprobe snd-ca0106 

Then I went to System > Preferences > Multimedia System Selectors and tested my audo and low and behold my Sound Blaster Live! 24bit was playing me some sound. I'm listening to Demons & Wizards in xmms at the time of this writing :)

---

### Post by psoulocybe on 2005-03-20
I'm trying this, but i get a hangup

```

psoulocybe@psoulocybe:/usr/src/modules/alsa-driver$ sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/KVERS=$(uname -r)
CC="gcc" ./configure --prefix=/usr --with-kernel=/usr/src/linux-headers-2.6.10-5-386/KVERS=2.6.10-5-386 --with-build=/usr/src/linux-headers-2.6.10-5-386/KVERS=2.6.10-5-386 --with-moddir=/lib/modules/unknown/updates/alsa --with-sequencer=yes --with-isapnp=no --with-debug=detect --with-cards="all"
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/modules/alsa-driver
checking cross compile...
checking for directory with kernel source... /usr/src/linux-headers-2.6.10-5-386/KVERS=2.6.10-5-386
checking for directory with kernel build... /usr/src/linux-headers-2.6.10-5-386/KVERS=2.6.10-5-386
checking for kernel version... The file /usr/src/linux-headers-2.6.10-5-386/KVERS=2.6.10-5-386/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.10-5-386/build).
make: *** [configure-stamp] Error 1

```

So, how exactly does a n00b change my input to fix this.... i'm using kubuntu btw.... so it's hoary 5.04

Thanks for working on this....

---

### Post by psoulocybe on 2005-03-20
Fixed it....  used a different method
thanks though.

---

### Post by fmanji on 2005-04-02
[QUOTE=Jesterace]Well I've been a dedicated slackware user for quite sometime and I have the dreaded value SB Live! 24Bit!. I was able to get it to work in slackware after I compiled alsa from cvs. But sitting here with Ubuntu I am at a loss I get wierd errors and when I tried to remove the original Alsa package it said gnome would have to be removed as well as a dependancy. 

So this left me on a mission, if it would work in slackware well surely it would work in something newer. As well as I have come from a background of alternative win32 shells bleeding edge and crashes were something I'm used to so I decided to upgrade to Hoary and so far Hoary has given me no issues. As well these instructions will work on hoary since they depend on the hoary universe repositories. crimsum from these forums and irc was so kind to give me a hand with this problem. So I wrote the steps down for others to use.

1st Step - assuming you're running Hoary with the deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe uncommented in /etc/apt/sources.list



2nd Step - This will change you to the proper directory and decompress the alsasource.

 

3rd Step - This will allow you to configure the alsa source. 

 

4th Step - Now it's time to make the Package

 

5th Step -This will check for the package

 

here's my output

 

However if you notice I'm using a kernel for an Athlon processor so my driver package would be pretty useless for others to use unless you have the same kernel as I.

6th Step - Install the drivers (assuming you've stayed in the same directory this whole time.

 

7th Step - Time to install the drivers, However i had some strange messages with that package so what I had done now was to load the ca0106 module into the kernel like so. 

 

Then I went to System > Preferences > Multimedia System Selectors and tested my audo and low and behold my Sound Blaster Live! 24bit was playing me some sound. I'm listening to Demons & Wizards in xmms at the time of this writing :)[/QUOTE]
 Same problem for me with my SB Live! 24, and they won't let me exchange it!

I tried what you said, everything worked until the end where I got:

[I]root@fmfmfm:/usr/src/modules # sudo dpkg -i *.deb
(Reading database ... 80860 files and directories currently installed.)
Preparing to replace alsa-modules-2.6.10-5-k7 1.0.8-4ubuntu4 (using alsa-modules-2.6.10-5-k7_1.0.8-4ubuntu4_i386.deb) ...
Unpacking replacement alsa-modules-2.6.10-5-k7 ...
Setting up alsa-modules-2.6.10-5-k7 (1.0.8-4ubuntu4) ...
 * Terminating processes:
 18933 (failed; still running: 19025).
Reloading sound driver modules: (none to reload).
You should now stop all applications using sound devices
and run "/etc/init.d/alsa force-reload" to load the new modules.[/I]

So I tried:

[I]root@fmfmfm:/usr/src/modules # /etc/init.d/alsa force-reload
 * Terminating processes:
 19025.
Unloading ALSA sound driver modules: snd-bt87x snd-pcm-oss snd-mixer-oss snd-pcm snd-timer snd-page-alloc (failed; not removed: snd-bt87x snd-mixer-oss snd-pcm snd-timer snd-page-alloc).
Reloading sound driver modules: snd-bt87x snd-pcm-oss snd-mixer-oss snd-pcm snd-timer snd-page-allocFATAL: Error inserting snd_pcm_oss (/lib/modules/2.6.10-5-k7/updates/alsa/acore/oss/snd-pcm-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)
 (failed).[/I]

So then I tried:
[I]
root@fmfmfm:/usr/src/modules # sudo modprobe snd-ca0106
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.10-5-k7/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.10-5-k7/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ca0106 (/lib/modules/2.6.10-5-k7/updates/alsa/pci/ca0106/snd-ca0106.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_ca0106[/I]

My soundcard is definetely not working, any suggestions with these errors?

Please help a newbie!!

---

### Post by fmanji on 2005-04-02
Okay, figured it out, went to 'init 1' and ran the commends from there, my SOUndblaster Live! 24" finally works!!!

---

### Post by mumford on 2005-04-03
Hey, terribly new to Linux here and looking to get my Audigy LS running on Hoary. I got to step one and unfortunately ran into a problem. When I try to run the apt-get on the alsa-source it says it cannot find package alsa-source. I've checked in the Synaptic manager and the only packages for Alsa I have in there are utils and base. 

What would I have to do to get the alsa-source package available?

Thanks.

---

### Post by veda_sticks on 2005-04-08
have sucesfully installed via this message, had no sound at first but thats cause the mixer volumes were all down, also produces choppy sound, esd cant start, open thread sound system is fine. and so does oss. does anyone know how to get mic input working, i have no channels in my mixer, i also have an extra tab names switches that has ac97 in , spdif out, spdiff in, spdif out, src out, i2s in and i2s mixer out.

Anyone know how to get mic input working?? i need it for teamspeak.
Thanxs, great guide i thought i was stuck as i accidentaly bought the live 24bit thinking it was the ct4760 card. Sounds great it Ubuntu.

---

### Post by jd_ on 2005-04-11
Hi.

My SB Live! 24Bit works (almost) fine, thanks to the instructions above. Thank you!
I have one problem, yet. I must re-do steps 6 and 7 every time I start my computer, and I really don't know why...

On step 6, the "Tune controler" (?) (in French, it is "Contrôleur de volume", located in "Applications > Sound and video" Gnome menu) crash and has to be reloaded. After a *sudo modprobe snd-ca0106*, it works fine again. It is weird, isn't it?

A simple *sudo modprobe snd-ca0106* does not work. I can get the SB Live! work only if the Tune controler crash.

Is there a way to make the SB Live! working every time?
I'm using Hoary with kernel 2.6.10-5-386.

Thank you.

---

### Post by psycose on 2005-04-14
Yes, there is a simple way;

1- Open the /etc/modules file

> sudo gedit /etc/modules 

2- Add the following line in the file

> snd-ca0106 

3- Save the file & exit 

4- At the next boot, your sound driver wiill be loaded ;-)


-- 
korek ça !

---

### Post by jallen7usa on 2005-04-14
[QUOTE=psoulocybe]Fixed it....  used a different method
thanks though.[/QUOTE]
How did you fix this?  What was your different method?  I'm getting the same error.

I tried the:
```
sudo gedit /etc/modules 
``` 
but still no sound.

---

### Post by psycose on 2005-04-15
Hi jallen7usa,

Have you tried the 7 steps proposed by Jesterace (first post of this thread)? , and then the 3 steps of my previus post ? 
Please give details ...

1- What is the output of the following shell command ? :
*This command tell us what software handle the /dev/dsp character device *

> lsof /dev/dsp 
2- What is the output of the following shell command ? :
*This command give us all kernel driver modules that contain the word "snd"*

>  sudo lsmod | grep snd 
3- Have you tried running the alsamixer tools ?, and be sure to unmuted all Analog* Items :

> alsamixer 
*You can read further on alsamixer by running :*

> man alsamixer 
4- May be could you store your alsa setting using  :

> alsactl store 

--
korek ca !

---

### Post by jd_ on 2005-04-16
[QUOTE=psycose]Yes, there is a simple way;
1- Open the /etc/modules file
2- Add the following line in the file
3- Save the file & exit 
4- At the next boot, your sound driver wiill be loaded ;-)
[/QUOTE]

 Thank you.
I already added snd-ca0106 to /etc/modules, though.
Well, I found that what was disturbing my sound card was my usb webcam (a Logitech Quickcam pro 4000). I also unplugged my internal Dell SB Live! and plugged the other external SB Live! in the first usb slot (I used to had two SB Live!, not using the Dell one since it is a modified SB Live! chipset and it worked fine with Fedora Core 3). Now it works like a charm.

Thanks :)

---

### Post by inbrednedd on 2005-04-26
Hi all.
I was hoping someone could enlighten me here...
following Jesterace's instructions, I succesfully installed the proper module (ca0106) for my Audigy ls card. Initially, Hoary had used the emu10k module.

At the end of his instructions, I reach the point where I go to the preferences and test alsa. It works initially.

Im able to use alsa and sound programs such as cd player...works great...until I logged out.

When I return into gnome (or flux), there is sound at the bootup splash screen. when I go to use any sound program, nada. Cd player even refuses to play. I go to test alsa in system, multimedia, but it says that it cannont construct an alsa pipeline. However the enlightened SOund Daemon is now working properly, although very few programs cooperate with it.

I have added snd-ca0106 to the /ect/modules file, no change upon logging in.

* on my first install of ubuntu I foolowed jesters instructions...sound only failed after I started up the volume meter program (something to do with the ESD again?)

when I try steps 7 and 8 upon re entering gnome,
i got the same message as fmanji:
"root@fmfmfm:/usr/src/modules # sudo dpkg -i *.deb
(Reading database ... 80860 files and directories currently installed.)
Preparing to replace alsa-modules-2.6.10-5-k7 1.0.8-4ubuntu4 (using alsa-modules-2.6.10-5-k7_1.0.8-4ubuntu4_i386.deb) ...
Unpacking replacement alsa-modules-2.6.10-5-k7 ...
Setting up alsa-modules-2.6.10-5-k7 (1.0.8-4ubuntu4) ...
* Terminating processes:
18933 (failed; still running: 19025).
Reloading sound driver modules: (none to reload).
You should now stop all applications using sound devices
and run "/etc/init.d/alsa force-reload" to load the new modules."

-except for the fact that my alsa-modules was for the 686 kernel

upon going into init 1 I am able to install properly, however the Enlightened SOund Daemon is still active, alsa pipeline still doesn't work.

Can anyone tell me what next?

Pat Mahoney

---

### Post by inbrednedd on 2005-04-27
some more info

the result for the comand

pat@ubuntu:~$  lsof /dev/dsp
COMMAND  PID USER   FD   TYPE DEVICE SIZE NODE NAME
esd     7509  pat    5w   CHR   14,3      6008 /dev/dsp
pat@ubuntu:~$


pat@ubuntu:~$  alsactl store
alsactl: save_state:1221: Cannot open /var/lib/alsa/asound.state for writing

pat@ubuntu:~$  sudo lsmod | grep snd
snd_ca0106             26532  2
snd_ac97_codec         67320  1 snd_ca0106
snd_pcm_oss            55712  1
snd_mixer_oss          18048  2 snd_pcm_oss
snd_pcm                91016  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              24580  1 snd_pcm
snd                    59780  6 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc         10116  2 snd_ca0106,snd_pcm

anyone know what my next course of action is?
Pat Mahoney

---

### Post by pelikan on 2005-04-28
Thank you so much for this guide. I have been working on getting my Audigy 2 Value working for days. After following your guide I opened alsamixer and un-muted the Analog/Digital output jack by pressing "m". I am very happily listening to music right now.

---

### Post by inbrednedd on 2005-04-28
haha whats the equivalent of bump on this board?

---

### Post by pirast on 2005-04-29
Hi,
I have got a problem:

I disabled onboard sound put my new audigy 2 zs in my computer and started Ubuntu. No sound. So I followed the steps in the howto.

I found out that /dev/dsp doesn't exist. And I could not enable the KDE sound system because I dont know what the path of my device is.

How can I find out what the part of my device is?

Thanks for help,
Martin

---

### Post by SqdnGuns on 2005-05-01
[QUOTE=Jesterace]
1st Step - assuming you're running Hoary with the deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe uncommented in /etc/apt/sources.list

Blah, blah, blah.............[/QUOTE]

YOU ROCK, this solved my problem!!! Funny thing is that my SBLIVE! 24 bit was working great with Slack 10.1 and DLG.........................I was about to wipe the drive and re-install it till I found this solution. Buku Thanks!!

---

### Post by adventurepants on 2005-05-01
Great Guide!

got ALSA working on a Dell Inspiron 8600 using the Intel8x0 driver for my AC97 soundcard.

The only problem is that if i restart and log back in, then ESD still works, but when i select ALSA in the multimedia systems selector and test it, i get the cannot construct pipeline error. 

but if i follow the second last step of the guide and do 

sudo dpkg -i *.deb

to the alsa-modules-2.6.10-5-386_1.0.8-4ubuntu.deb file.

Then ALSA works again! i dont even have to load the module, just unpack that file.

I then test Alsa on ryhthmbox and a couple games, and it works fine.
 

What is going on? 

And how do i nail this down so that it works on a restart?

---

### Post by jzietman on 2005-05-09
how would i go through this process (in hoary 386) for an sb live! 5.1 card? :newbie:

---

### Post by jzietman on 2005-05-09
anyone?

---

### Post by elfoe on 2005-05-10
Thanks for your help.

But my Sb live 24 bit works only on 2.1...
How do I to make it works on 5.1 ??

Is it because my output is 

```
alsa-modules-2.6.10-5-386_1.0.8-4ubuntu4_i386.deb 
```

when i do ```
cd .. && ls *.deb 
```on the 5th Step ?

The **sudo lsmod | grep snd** command gives me :

```
snd_ca0106             26532  0
snd_ac97_codec         67320  1 snd_ca0106
snd_pcm_oss            55712  0
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                91016  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              24580  1 snd_pcm
snd                    59780  6 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc         10116  2 snd_ca0106,snd_pcm
``` 

The ```
 lsof /dev/dsp
``` returns nothing ??

I've ran alsamixer and unmutted all Analog output...

(Sorry if my english is poor...) 

Need Help  Please...
Thanks.

---

### Post by jzietman on 2005-05-16
[QUOTE=jzietman]how would i go through this process (in hoary 386) for an sb live! 5.1 card? :newbie:[/QUOTE]

or hoary-686

---

### Post by jrincon87 on 2005-06-02
Does this instruction work with the SB Live 24 bits external (USB)?
Thanks.

---

### Post by crimsun on 2005-06-08
[QUOTE=jrincon87]Does this instruction work with the SB Live 24 bits external (USB)?
Thanks.[/QUOTE]

A usb device will use the snd_usb_audio ALSA driver and thus is not affected by these instructions.

---

### Post by crimsun on 2005-06-08
[QUOTE=elfoe]But my Sb live 24 bit works only on 2.1...
How do I to make it works on 5.1 ??[/QUOTE]

You need to use the plug:surround51 virtual device. For instance, in beep-media-player, in the preferences for the ALSA output plugin, place "plug:surround51" in the device selection.

---

### Post by crimsun on 2005-06-08
[QUOTE=jzietman]or hoary-686[/QUOTE]
The sblive 5.1 (**not** the OEM Dell sblive nor the 24-bit/7.1 sblive) uses the normal snd_emu10k1 driver. What precisely are you attempting to accomplish?

---

### Post by icedog90 on 2005-06-17
Arrgh, I did this guide and everything went well, but when I rebooted and unmuted everything in kmix the sound came out very choppy.  I tried increasing the sound buffer and tweaking several other things in the control center but nothing affected anything, except increasing the sound buffer got rid of a little bit of the skipping.  It's definitely impossible to listen to music... and the sound either doesn't work at all in some games or in games such as Battlefield 1942 all I get is a white noise sound and it makes the game run extremely slow... someone please help.   :(

---

### Post by RobLewis on 2005-06-17
I'm another very recent Ubuntu convert. I've used Linux a little, but I'm still pretty much ignorant about how to do many simple tasks.

My problem with the steps in the first post occurs at the first command, > sudo apt-get install build-essential fakeroot linux-headers-$(uname -r) alsa-source kernel-package. I get this output:
> Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
fakeroot is already the newest version.
linux-headers-2.6.10-5-386 is already the newest version.
E: Couldn't find package alsa-source
.

I checked the Package Manager for something similar, and found alsa-base; I tried the command using that instead of alsa-source (I hope doing this didn't cause any problems), and it finished on the line > Setting up build-essential (10.1ubuntu1) .... However, the next command > cd /usr/src/ && sudo tar jfx alsa-driver.tar.bz2
 fails because alsa-driver.tar.bz2 does not exist.

Can any of you more experienced folks help me out? Thanks a lot!

---

### Post by RobLewis on 2005-06-19
Well, for some reason it worked today! My card works perfectly now. Thanks for the guide!

---

### Post by Appleday on 2005-06-22
Thank you.

Psycose's solution solved my horrible background noise problem.

---

### Post by HeadUp on 2005-06-27
Hi!
I think we can say i'm a newbie in linux world, just a little experience....

So I got a SBlive 24bit!, I follow step by step this thread : [http://www.ubuntuforums.org/showthread.php?t=19307](http://www.ubuntuforums.org/showthread.php?t=19307) and I got sound, but no microphone.
Alsamixer shows me only 8 or 9 different volumes level, and no input (or only one called capture ??!?).

I need Teamspeak and Enemy territory working in the same time, it's the last way to makes me removing Windows.

Please help me I won't give up Linux, and I wanna avoid Windows.

P.S. : I have Hoary

---

### Post by action09 on 2005-07-09
Hi all :)
Thanks man for this guide :)

I'm trying to install my audigy LS with this guide..ok til Step 4 (make the pkg)

i did:
-------

root@WOPR:/usr/src/modules # cd modules/alsa-driver && sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)
bash: cd: modules/alsa-driver: Aucun fichier ou répertoire de ce type
root@WOPR:/usr/src/modules # cd ..
root@WOPR:/usr/src # cd modules/alsa-driver && sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)
/usr/bin/make  compile
make[1]: entrant dans le répertoire « /usr/src/modules/alsa-driver »
make[2]: entrant dans le répertoire « /usr/src/modules/alsa-driver/acore »
copying file alsa-kernel/core/sound.c
patching file sound.c
Hunk #2 succeeded at 165 with fuzz 2.
Hunk #3 succeeded at 366 (offset -4 lines).
Hunk #4 succeeded at 381 (offset -6 lines).
Hunk #5 succeeded at 496 (offset -7 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #1 succeeded at 1341 (offset 25 lines).
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #1 succeeded at 995 (offset 26 lines).
Hunk #2 succeeded at 1805 (offset 72 lines).
Hunk #3 succeeded at 1833 (offset 52 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
Hunk #1 succeeded at 321 (offset 29 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
gcc-3.3 -D__KERNEL__ -DMODULE=1 -I/usr/src/modules/alsa-driver/include  -I/usr/src/linux-headers-2.6.10-5-386//include -I/usr/src/linux-headers-2.6.10-5-386//include -O2  -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include   -DEXPORT_SYMTAB -c memalloc.c
gcc-3.3 -D__KERNEL__ -DMODULE=1 -I/usr/src/modules/alsa-driver/include  -I/usr/src/linux-headers-2.6.10-5-386//include -I/usr/src/linux-headers-2.6.10-5-386//include -O2  -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include  -DKBUILD_BASENAME=sgbuf   -c -o sgbuf.o sgbuf.c
gcc-3.3 -D__KERNEL__ -DMODULE=1 -I/usr/src/modules/alsa-driver/include  -I/usr/src/linux-headers-2.6.10-5-386//include -I/usr/src/linux-headers-2.6.10-5-386//include -O2  -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include  -DKBUILD_BASENAME=memory_wrapper   -c -o memory_wrapper.o memory_wrapper.c
gcc-3.3 -D__KERNEL__ -DMODULE=1 -I/usr/src/modules/alsa-driver/include  -I/usr/src/linux-headers-2.6.10-5-386//include -I/usr/src/linux-headers-2.6.10-5-386//include -O2  -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include   -DEXPORT_SYMTAB -c pcm.c
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #5 succeeded at 2843 with fuzz 2.
gcc-3.3 -D__KERNEL__ -DMODULE=1 -I/usr/src/modules/alsa-driver/include  -I/usr/src/linux-headers-2.6.10-5-386//include -I/usr/src/linux-headers-2.6.10-5-386//include -O2  -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include  -DKBUILD_BASENAME=pcm_native   -c -o pcm_native.o pcm_native.c
Dans le fichier inclus à partir de /usr/src/linux-headers-2.6.10-5-386/include/linux/irq.h:21,
          à partir de /usr/src/linux-headers-2.6.10-5-386/include/asm/hardirq.h:6,
          à partir de /usr/src/linux-headers-2.6.10-5-386/include/linux/hardirq.h:6,
          à partir de /usr/src/linux-headers-2.6.10-5-386/include/linux/interrupt.h:11,
          à partir de /usr/src/modules/alsa-driver/include/sound/timer.h:27,
          à partir de pcm_native.c:35:
/usr/src/linux-headers-2.6.10-5-386/include/asm/irq.h:16:25: irq_vectors.h : Aucun fichier ou répertoire de ce type
In file included from /usr/src/linux-headers-2.6.10-5-386/include/asm/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.10-5-386/include/linux/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.10-5-386/include/linux/interrupt.h:11,
                 from /usr/src/modules/alsa-driver/include/sound/timer.h:27,
                 from pcm_native.c:35:
/usr/src/linux-headers-2.6.10-5-386/include/linux/irq.h:71: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.10-5-386/include/linux/irq.h:73,
                 from /usr/src/linux-headers-2.6.10-5-386/include/asm/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.10-5-386/include/linux/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.10-5-386/include/linux/interrupt.h:11,
                 from /usr/src/modules/alsa-driver/include/sound/timer.h:27,
                 from pcm_native.c:35:
/usr/src/linux-headers-2.6.10-5-386/include/asm/hw_irq.h:28: error: `NR_IRQ_VECTORS' undeclared here (not in a function)
/usr/src/linux-headers-2.6.10-5-386/include/asm/hw_irq.h:32: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.10-5-386/include/asm/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.10-5-386/include/linux/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.10-5-386/include/linux/interrupt.h:11,
                 from /usr/src/modules/alsa-driver/include/sound/timer.h:27,
                 from pcm_native.c:35:
/usr/src/linux-headers-2.6.10-5-386/include/linux/irq.h:78: error: `NR_IRQS' undeclared here (not in a function)
make[2]: *** [pcm_native.o] Erreur 1
make[2]: quittant le répertoire « /usr/src/modules/alsa-driver/acore »
make[1]: *** [compile] Erreur 1
make[1]: quittant le répertoire « /usr/src/modules/alsa-driver »
make: *** [build-stamp] Erreur 2
root@WOPR:/usr/src/modules/alsa-driver #



No idea with the compilation NOK. any advice please ? :)

---

### Post by filemanager on 2005-07-13
It worked!! THANK YOU for posting this!!!! It completely solved my sound problem I've been battling since forever!!!   \\:D/    :grin:    :)  :smile: 

*happy dance*

---

### Post by Nais on 2005-07-14
i followed these instructions and still have had no luck.

My sound is from my onboard chip, a ca0106. Does it make a difference that it's onboard? 
The board is an MSI K8N Neo4 Platinum, Running Ubuntu AMD64

---

### Post by popeygone on 2005-07-16
Many thanks jesterace, I followed your instructions and now have a working sb live 24 at last  :grin:

---

### Post by potatohead on 2005-07-19
[QUOTE=jallen7usa]How did you fix this?  What was your different method?  I'm getting the same error.

I tried the:
```
sudo gedit /etc/modules 
``` 
but still no sound.[/QUOTE]
 I've got the same card. Has anyone gotten any more than 2 channels to work? if so, how? On my mixer, I have controls for analog rear and analog 'unknown' (guessing supposed to be center), but they don't do anything.

Any ideas?

---

### Post by mjhaynes on 2005-07-30
Just wanted to say thanks. Everything works great!

---

### Post by jeffe on 2005-08-03
well 

this has been a long day

i finally got my sound working today using this guide.

then i decided to update kde

and now my sound is broken again, and i can't fix it using this guide anymore  ](*,) 


errors during the final step..

---

### Post by webmaven on 2005-08-03
Your instructions were very helpful, but have you managed to get the microphone working as well?

---

### Post by TiMBuS on 2005-08-13
this worked GREAT for the most part.
It removed a few changes I had made to the kernel .config but that was ok because I fixed it. The real problem began when I installed my video card drivers. The sound modules won't even load.. this is what happens:

```
# modprobe snd-ca0106
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-5-386/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.10-5-386/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-5-386/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.10-5-386/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ca0106 (/lib/modules/2.6.10-5-386/updates/alsa/pci/ca0106/snd-ca0106.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_ca0106
```

Fun! What's going on here? I was told that xmms might have a problem with the nvidia driver unless I installed a mod, which I did. Should I just remake the driver?

EDIT: Can't remake the driver.

---

### Post by mtoledo on 2005-08-17
[QUOTE=crimsun]You need to use the plug:surround51 virtual device. For instance, in beep-media-player, in the preferences for the ALSA output plugin, place "plug:surround51" in the device selection.[/QUOTE]

I also have it working with 2.1 channels, a good way to test if it's working all channels is using speaker-test, for example:

Produce 5.1 speaker sound from three stereo jacks:

speaker-test -Dsurround51 -c6

This doesn't work for me, it stays there forever. I would like to have 5.1 channels or at least route to the others speakers too. Anyone that succeeded care to share?

---

### Post by mtoledo on 2005-08-17
[QUOTE=HeadUp]Hi!
I think we can say i'm a newbie in linux world, just a little experience....

So I got a SBlive 24bit!, I follow step by step this thread : [http://www.ubuntuforums.org/showthread.php?t=19307](http://www.ubuntuforums.org/showthread.php?t=19307) and I got sound, but no microphone.
Alsamixer shows me only 8 or 9 different volumes level, and no input (or only one called capture ??!?).

I need Teamspeak and Enemy territory working in the same time, it's the last way to makes me removing Windows.

Please help me I won't give up Linux, and I wanna avoid Windows.

P.S. : I have Hoary[/QUOTE]
 The microphone support has entered about two weeks ago in the cvs (2005-08-17), so either you will have to wait or download the cvs version.

---

### Post by sunrex on 2005-08-18
thezombiehunter@thezombiehunter:~$ sudo apt-get install build-essential fakeroot linux-headers-$(uname -r) alsa-source kernel-package
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
fakeroot is already the newest version.
linux-headers-2.6.10-5-386 is already the newest version.
alsa-source is already the newest version.
kernel-package is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
thezombiehunter@thezombiehunter:~$ cd /usr/src/ && sudo tar jfx alsa-driver.tar.bz2
thezombiehunter@thezombiehunter:/usr/src$ sudo dpkg-reconfigure alsa-source, and say no to PnP, yes to debug, and choose the ca0106 driver
Package `alsa-source,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: alsa-source, is not installed
thezombiehunter@thezombiehunter:/usr/src$ sudo dpkg-reconfigure alsa-source
thezombiehunter@thezombiehunter:/usr/src$ cd modules/alsa-driver && sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)
/usr/bin/make  compile
make[1]: Entering directory `/usr/src/modules/alsa-driver'
if [ ! -d include/sound -a ! -L include/sound ]; then \
  ln -sf ../alsa-kernel/include include/sound ; \
fi
cp -auvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
/usr/bin/make dep
make[2]: Entering directory `/usr/src/modules/alsa-driver'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[3]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[4]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers'
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[3]: Entering directory `/usr/src/modules/alsa-driver/synth'
make[4]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/azx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/azx'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[3]: Entering directory `/usr/src/modules/alsa-driver/usb'
make[4]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
/usr/bin/make -C /usr/src/linux-headers-2.6.10-5-386/ SUBDIRS=/usr/src/modules/alsa-driver O=/usr/src/linux-headers-2.6.10-5-386/ modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /usr/src/modules/alsa-driver/acore/oss/mixer_oss.o
In file included from include/linux/sched.h:191,
                 from include/linux/module.h:10,
                 from /usr/src/modules/alsa-driver/include/adriver.h:51,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:22:
include/linux/aio.h:151: error: field `wq' has incomplete type
In file included from include/linux/module.h:23,
                 from /usr/src/modules/alsa-driver/include/adriver.h:51,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:22:
include/asm/module.h:56:2: #error unknown processor family
In file included from /usr/src/modules/alsa-driver/include/adriver.h:587,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:22:
include/linux/pci.h:515: error: field `dev' has incomplete type
include/linux/pci.h:595: error: field `class_dev' has incomplete type
include/linux/pci.h:649: error: field `driver' has incomplete type
In file included from include/asm/pci.h:105,
                 from include/linux/pci.h:877,
                 from /usr/src/modules/alsa-driver/include/adriver.h:587,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:22:
include/asm-generic/pci-dma-compat.h: In function `pci_dma_supported':
include/asm-generic/pci-dma-compat.h:15: warning: implicit declaration of function `dma_supported'
include/asm-generic/pci-dma-compat.h: In function `pci_alloc_consistent':
include/asm-generic/pci-dma-compat.h:22: warning: implicit declaration of function `dma_alloc_coherent'
include/asm-generic/pci-dma-compat.h:22: warning: return makes pointer from integer without a cast
include/asm-generic/pci-dma-compat.h: In function `pci_free_consistent':
include/asm-generic/pci-dma-compat.h:29: warning: implicit declaration of function `dma_free_coherent'
include/asm-generic/pci-dma-compat.h: In function `pci_map_single':
include/asm-generic/pci-dma-compat.h:35: warning: implicit declaration of function `dma_map_single'
include/asm-generic/pci-dma-compat.h:35: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_unmap_single':
include/asm-generic/pci-dma-compat.h:42: warning: implicit declaration of function `dma_unmap_single'
include/asm-generic/pci-dma-compat.h:42: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_map_page':
include/asm-generic/pci-dma-compat.h:49: warning: implicit declaration of function `dma_map_page'
include/asm-generic/pci-dma-compat.h:49: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_unmap_page':
include/asm-generic/pci-dma-compat.h:56: warning: implicit declaration of function `dma_unmap_page'
include/asm-generic/pci-dma-compat.h:56: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_map_sg':
include/asm-generic/pci-dma-compat.h:63: warning: implicit declaration of function `dma_map_sg'
include/asm-generic/pci-dma-compat.h:63: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_unmap_sg':
include/asm-generic/pci-dma-compat.h:70: warning: implicit declaration of function `dma_unmap_sg'
include/asm-generic/pci-dma-compat.h:70: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_single_for_cpu':include/asm-generic/pci-dma-compat.h:77: warning: implicit declaration of function `dma_sync_single_for_cpu'
include/asm-generic/pci-dma-compat.h:77: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_single_for_device':
include/asm-generic/pci-dma-compat.h:84: warning: implicit declaration of function `dma_sync_single_for_device'
include/asm-generic/pci-dma-compat.h:84: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_sg_for_cpu':
include/asm-generic/pci-dma-compat.h:91: warning: implicit declaration of function `dma_sync_sg_for_cpu'
include/asm-generic/pci-dma-compat.h:91: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_sg_for_device':
include/asm-generic/pci-dma-compat.h:98: warning: implicit declaration of function `dma_sync_sg_for_device'
include/asm-generic/pci-dma-compat.h:98: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_mapping_error':
include/asm-generic/pci-dma-compat.h:104: warning: implicit declaration of function `dma_mapping_error'
In file included from /usr/src/modules/alsa-driver/include/adriver.h:587,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:22:
include/linux/pci.h: In function `pci_get_drvdata':
include/linux/pci.h:970: warning: implicit declaration of function `dev_get_drvdata'
include/linux/pci.h:970: warning: return makes pointer from integer without a cast
include/linux/pci.h: In function `pci_set_drvdata':
include/linux/pci.h:975: warning: implicit declaration of function `dev_set_drvdata'
In file included from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:27:
/usr/src/modules/alsa-driver/include/sound/core.h: At top level:
/usr/src/modules/alsa-driver/include/sound/core.h:166: error: field `free_workq' has incomplete type
make[6]: *** [/usr/src/modules/alsa-driver/acore/oss/mixer_oss.o] Error 1
make[5]: *** [/usr/src/modules/alsa-driver/acore/oss] Error 2
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [compile] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [build-stamp] Error 2
thezombiehunter@thezombiehunter:/usr/src/modules/alsa-driver$ cd .. && ls *.deb
ls: *.deb: No such file or directory
thezombiehunter@thezombiehunter:/usr/src/modules$ alsa-modules-2.6.10-4-k7_1.0.8-4ubuntu1_i386.deb
bash: alsa-modules-2.6.10-4-k7_1.0.8-4ubuntu1_i386.deb: command not found
thezombiehunter@thezombiehunter:/usr/src/modules$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
thezombiehunter@thezombiehunter:/usr/src/modules$ sudo modprobe snd-ca0106
FATAL: Module snd_ca0106 not found.
FATAL: Error running install command for snd_ca0106
thezombiehunter@thezombiehunter:/usr/src/modules$



ok i messed up somwere couse it wont work

can i delete all this and then redo it if so whats the command

---

### Post by Gaweph on 2005-08-19
Just wanted to say, THANX!

The abopve walkthrough on how to install my new Sound Card worked perfectly.

Thanx Again  :razz:

---

### Post by BTJustice on 2005-08-19
The directions in the original post worked for me, but my sound is both choppy and scratchy.  What might be causing that and how can I fix it?  I use Kubuntu.

---

### Post by Jackfrost on 2005-08-23
mat@ubuntumat:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
mat@ubuntumat:~$ apt-get install build-essential fakeroot linux-headers-$(uname -r) alsa-source kernel-package
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mat@ubuntumat:~$  sudo apt-get install build-essential fakeroot linux-headers-$(uname -r) alsa-source kernel-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package alsa-source
mat@ubuntumat:~$
 so i take it that step 1 is not gonna work for me wat to do?

---

### Post by Jackfrost on 2005-08-23
> **sunrex]thezombiehunter@thezombiehunter:~$ sudo apt-get install build-essential fakeroot linux-headers-$(uname -r) alsa-source kernel-package
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
fakeroot is already the newest version.
linux-headers-2.6.10-5-386 is already the newest version.
alsa-source is already the newest version.
kernel-package is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
thezombiehunter@thezombiehunter:~$ cd /usr/src/ && sudo tar jfx alsa-driver.tar.bz2
thezombiehunter@thezombiehunter:/usr/src$ sudo dpkg-reconfigure alsa-source, and say no to PnP, yes to debug, and choose the ca0106 driver
Package `alsa-source,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: alsa-source, is not installed
thezombiehunter@thezombiehunter:/usr/src$ sudo dpkg-reconfigure alsa-source
thezombiehunter@thezombiehunter:/usr/src$ cd modules/alsa-driver && sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)
/usr/bin/make  compile
make[1]: Entering directory `/usr/src/modules/alsa-driver'
if [ ! -d include/sound -a ! -L include/sound ] said:**
> : Entering directory `/usr/src/modules/alsa-driver'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[3]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[4]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers'
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[3]: Entering directory `/usr/src/modules/alsa-driver/synth'
make[4]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/azx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/azx'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[3]: Entering directory `/usr/src/modules/alsa-driver/usb'
make[4]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
/usr/bin/make -C /usr/src/linux-headers-2.6.10-5-386/ SUBDIRS=/usr/src/modules/alsa-driver O=/usr/src/linux-headers-2.6.10-5-386/ modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /usr/src/modules/alsa-driver/acore/oss/mixer_oss.o
In file included from include/linux/sched.h:191,
                 from include/linux/module.h:10,
                 from /usr/src/modules/alsa-driver/include/adriver.h:51,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:22:
include/linux/aio.h:151: error: field `wq' has incomplete type
In file included from include/linux/module.h:23,
                 from /usr/src/modules/alsa-driver/include/adriver.h:51,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:22:
include/asm/module.h:56:2: #error unknown processor family
In file included from /usr/src/modules/alsa-driver/include/adriver.h:587,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:22:
include/linux/pci.h:515: error: field `dev' has incomplete type
include/linux/pci.h:595: error: field `class_dev' has incomplete type
include/linux/pci.h:649: error: field `driver' has incomplete type
In file included from include/asm/pci.h:105,
                 from include/linux/pci.h:877,
                 from /usr/src/modules/alsa-driver/include/adriver.h:587,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:22:
include/asm-generic/pci-dma-compat.h: In function `pci_dma_supported':
include/asm-generic/pci-dma-compat.h:15: warning: implicit declaration of function `dma_supported'
include/asm-generic/pci-dma-compat.h: In function `pci_alloc_consistent':
include/asm-generic/pci-dma-compat.h:22: warning: implicit declaration of function `dma_alloc_coherent'
include/asm-generic/pci-dma-compat.h:22: warning: return makes pointer from integer without a cast
include/asm-generic/pci-dma-compat.h: In function `pci_free_consistent':
include/asm-generic/pci-dma-compat.h:29: warning: implicit declaration of function `dma_free_coherent'
include/asm-generic/pci-dma-compat.h: In function `pci_map_single':
include/asm-generic/pci-dma-compat.h:35: warning: implicit declaration of function `dma_map_single'
include/asm-generic/pci-dma-compat.h:35: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_unmap_single':
include/asm-generic/pci-dma-compat.h:42: warning: implicit declaration of function `dma_unmap_single'
include/asm-generic/pci-dma-compat.h:42: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_map_page':
include/asm-generic/pci-dma-compat.h:49: warning: implicit declaration of function `dma_map_page'
include/asm-generic/pci-dma-compat.h:49: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_unmap_page':
include/asm-generic/pci-dma-compat.h:56: warning: implicit declaration of function `dma_unmap_page'
include/asm-generic/pci-dma-compat.h:56: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_map_sg':
include/asm-generic/pci-dma-compat.h:63: warning: implicit declaration of function `dma_map_sg'
include/asm-generic/pci-dma-compat.h:63: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_unmap_sg':
include/asm-generic/pci-dma-compat.h:70: warning: implicit declaration of function `dma_unmap_sg'
include/asm-generic/pci-dma-compat.h:70: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_single_for_cpu':include/asm-generic/pci-dma-compat.h:77: warning: implicit declaration of function `dma_sync_single_for_cpu'
include/asm-generic/pci-dma-compat.h:77: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_single_for_device':
include/asm-generic/pci-dma-compat.h:84: warning: implicit declaration of function `dma_sync_single_for_device'
include/asm-generic/pci-dma-compat.h:84: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_sg_for_cpu':
include/asm-generic/pci-dma-compat.h:91: warning: implicit declaration of function `dma_sync_sg_for_cpu'
include/asm-generic/pci-dma-compat.h:91: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_sg_for_device':
include/asm-generic/pci-dma-compat.h:98: warning: implicit declaration of function `dma_sync_sg_for_device'
include/asm-generic/pci-dma-compat.h:98: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_mapping_error':
include/asm-generic/pci-dma-compat.h:104: warning: implicit declaration of function `dma_mapping_error'
In file included from /usr/src/modules/alsa-driver/include/adriver.h:587,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:22:
include/linux/pci.h: In function `pci_get_drvdata':
include/linux/pci.h:970: warning: implicit declaration of function `dev_get_drvdata'
include/linux/pci.h:970: warning: return makes pointer from integer without a cast
include/linux/pci.h: In function `pci_set_drvdata':
include/linux/pci.h:975: warning: implicit declaration of function `dev_set_drvdata'
In file included from /usr/src/modules/alsa-driver/acore/oss/mixer_oss.c:27:
/usr/src/modules/alsa-driver/include/sound/core.h: At top level:
/usr/src/modules/alsa-driver/include/sound/core.h:166: error: field `free_workq' has incomplete type
make[6]: *** [/usr/src/modules/alsa-driver/acore/oss/mixer_oss.o] Error 1
make[5]: *** [/usr/src/modules/alsa-driver/acore/oss] Error 2
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [compile] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [build-stamp] Error 2
thezombiehunter@thezombiehunter:/usr/src/modules/alsa-driver$ cd .. && ls *.deb
ls: *.deb: No such file or directory
thezombiehunter@thezombiehunter:/usr/src/modules$ alsa-modules-2.6.10-4-k7_1.0.8-4ubuntu1_i386.deb
bash: alsa-modules-2.6.10-4-k7_1.0.8-4ubuntu1_i386.deb: command not found
thezombiehunter@thezombiehunter:/usr/src/modules$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
thezombiehunter@thezombiehunter:/usr/src/modules$ sudo modprobe snd-ca0106
FATAL: Module snd_ca0106 not found.
FATAL: Error running install command for snd_ca0106
thezombiehunter@thezombiehunter:/usr/src/modules$



ok i messed up somwere couse it wont work

can i delete all this and then redo it if so whats the command
 lol m8 u never messed up this is just linux for ya if u gor 6 months  to figure out how stuff dosent work read on if not back to windows

---

### Post by D@ffy on 2005-08-24
[QUOTE=Nais]i followed these instructions and still have had no luck.

My sound is from my onboard chip, a ca0106. Does it make a difference that it's onboard? 
The board is an MSI K8N Neo4 Platinum, Running Ubuntu AMD64[/QUOTE]
Same problem here, anyone who has a suggestion? (same motherboard, and ALSA won't work, no matter what I try, OSS neither)

---

### Post by TiMBuS on 2005-08-25
[QUOTE=Jackfrost]mat@ubuntumat:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
mat@ubuntumat:~$ apt-get install build-essential fakeroot linux-headers-$(uname -r) alsa-source kernel-package
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mat@ubuntumat:~$  sudo apt-get install build-essential fakeroot linux-headers-$(uname -r) alsa-source kernel-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package alsa-source
mat@ubuntumat:~$
 so i take it that step 1 is not gonna work for me wat to do?[/QUOTE]

ok, 1. its:   sudo apt-get install build-essential fakeroot linux-headers-$(uname -r) alsa-source kernel-package

2. do you have repositories added? goto [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
and do what it says, THEN sudo apt-get all that.

PS. Yes, love the advice you give out because you're too damn impatient to learn linux.

---

### Post by projektdotnet on 2005-08-27
[QUOTE=BTJustice]The directions in the original post worked for me, but my sound is both choppy and scratchy.  What might be causing that and how can I fix it?  I use Kubuntu.[/QUOTE]
Same problem. At least I have sound AT ALL I was having trouble just fixing that part of it in Kubuntu.

Edit: P.S. I forgot to say thanks for the howto on getting it working at all its a great head start

---

### Post by projektdotnet on 2005-08-28
ok I know i'm not the only one who has had problems with choppy/skipping shound in this post so for those with that problemlower the sound buffer to as low as possible and then it should fix the problem (while playing around with the control center settings thats what fixed mine) I had also disabled realtime priority but it wasnt any differnet on quality.

---

### Post by Steve1961 on 2005-08-30
Great how to.  After never managing to get sound working with an on-board sis ac97 chip I bought a cheap oem SBLive 24bit and everything's now working great.  Many thanks.

---

### Post by Magadass on 2005-09-09
[QUOTE=fmanji]Okay, figured it out, went to 'init 1' and ran the commends from there, my SOUndblaster Live! 24" finally works!!![/QUOTE]

Can you explain what you mean by "went to init 1", I am trying to get better at linux and you lost me on that statement...Its so painful to feel like a noob in the linux world, especially since in the Windows world I am considered a guru...Ugh the pain, the piercing shar pain.... <<--  ](*,) 


Thanks guys!! :D

---

### Post by grp21 on 2005-09-10
hello all, 
it does not work for me here :(
i have a pci card : Creative Sound Blaster Live! 24 bits
i follow the guide step by step, everything seems to be ok.
i added snd-ca0106 in /etc/modules
i rebooted, error message during "loading modules" : 

[blockquote]
ALSA /usr/src/modules/alsa-driver/alsa-kernel/pci/ac97/ac97_codec.c:1907: AC'97 0 does not respond - RESET
ALSA /usr/src/modules/alsa-driver/alsa-kernel/pci/ac97/ac97_codec.c:1916: AC'97 0 access is not valid [0x0], removing mixer.
CA0106: probe of 0000:00:09.0 failed with error -5
[/blockquote]

ac97 seems to be my onboard sound card so i tryed to solve this problem performing the install another time, and adding the module during "dpkg-reconfigure alsa-source" :  via82xx (PCI: AC97 on motherboards with VIA VT 8233|8233A|8233C|8235 or VT 8.....
i added snd-ac97-codec  in /etc/modules
i rebooted, still the same error and still no sound :(

the modules seem to be loaded

[blockquote]
grp21@alanismauricette:~$  sudo lsmod | grep snd
snd_ca0106             26532  0
snd_ac97_codec         67320  1 snd_ca0106
snd_pcm_oss            55712  0
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                91016  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              24580  1 snd_pcm
snd                    59780  6 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc         10116  2 snd_ca0106,snd_pcm
[/blockquote]

the card seemed to be connected
when i launch System>Administration>device manager , gnome detect it :  SB AUDIGY LS


i need help  :-|

---

### Post by redboar on 2005-09-20
[QUOTE=projektdotnet]ok I know i'm not the only one who has had problems with choppy/skipping shound in this post so for those with that problemlower the sound buffer to as low as possible and then it should fix the problem (while playing around with the control center settings thats what fixed mine) I had also disabled realtime priority but it wasnt any differnet on quality.[/QUOTE]

What sound buffer?  Which control center?!?

---

### Post by rossjman1 on 2005-10-05
```
jeff@ubuntu:/usr/src/modules/alsa-driver$ sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)
You don't have the compiler that your kernel was built with installed
make: *** [configure-stamp] Error 1

```
Ahh, I don't know what to do. Please help.

---

### Post by Boelraty on 2005-10-05
I have a Sound Blaster Live 5.1 and a internal card AC97, for the moment, i have the sound on AC97 and i want use the other card

so i follow your instruction ut at step 5, you said to find a deb (alsa-module ...) but i dont know how to find this file, and where ! I have no *.dev in the directory :(
Maybe it is because of Breezy, this help is for Hoary, my source.list is like that :

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Hoary Extras (because Breezy Extras are not curently available)
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Officials Backports
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

## Backports
## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted
## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted
## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted


Thanks for your help

---

### Post by Boelraty on 2005-10-07
nobody can help me ?

---

### Post by rossjman1 on 2005-10-08
For anyone that had the same problem I had ("You don't have the compiler that your kernel was built with installed"), this can be fixed with a simple sudo apt-get install gcc-3.4

But now I've got another problem. Everything installed fine, but the sound is so low I cant hear it unless I put my ear against the speaker. Everything is maxed out in alsamixer. When I go into "Multimedea Systems Selector" it wont let me use anything other than ESD. Is there a volume controler for ESD that I don't know about? It's not my speakers, either, because Volume Meter doesn't show anything when I play music.

---

### Post by Linux_Amateur on 2005-10-15
[QUOTE=rossjman1]```
jeff@ubuntu:/usr/src/modules/alsa-driver$ sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)
You don't have the compiler that your kernel was built with installed
make: *** [configure-stamp] Error 1

```
Ahh, I don't know what to do. Please help.[/QUOTE]

Hello, i'm not a expert in Linux, but i have a SB Live 24 too.
When i saw that error. i've installed the "build-essential" and that installed the Kernel sources and the compiler and all necessary files.  Then i ran the command than you put here "sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)" and that worked for me.

Good Luck
(sorry my english, i'm from Chile)

---

### Post by rossjman1 on 2005-10-20
Bump. Does anyone know how to fix my other problem. I got the drivers to install and load, but sound volume is so low I can't hear anything, and the volume is all the way up in alsamixer.

---

### Post by Captn on 2005-10-20
[QUOTE=crimsun]You need to use the plug:surround51 virtual device. For instance, in beep-media-player, in the preferences for the ALSA output plugin, place "plug:surround51" in the device selection.[/QUOTE]

I'm a newbie, can you explain a little more on this? I'm having the same issue. Thanks in advance.:)

---

### Post by jaykup on 2005-11-21
I just installed Ubuntu, and tried getting the sb card to work, but i got this error..

```
jake@DIGITAL:/usr/src$ cd modules/alsa-driver && sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)
You don't have the compiler that your kernel was built with installed
make: *** [configure-stamp] Error 1

```

what do I need?

---

### Post by wicka on 2005-11-27
Jaykup: sudo apt-get install gcc-3.4

I am having the same problems with the choppy sound and what not, and since I am using GNOME (as I assume many others are) I have no access to the Control Center, and thus, any way to change the sound buffer (that I know of). Please, if I cannot get this problem fixed I am going back to Windows and this will probably be the last time I mess around with Linux.

---

### Post by justinc4 on 2006-02-15
Thank you so much for the orginal guide, I remember trying to do this back with the hedgehog and just giving up.  I have the dreaded MSI Neo Plat nForce4 board with a soundblaster live24 bit and the instructions worked perfectly.

The only thing to mention is: Mute all the SDI<anything>.  After the install works, you have to run alsamixer again and un-mute the analog outputs.  Works like a charm and all the stuttering is gone!

---

### Post by Snipe3D on 2006-03-10
Well, I got all the way through install, but no sound will play, and when I try to test in multimedia system selector, it says unable to construct pipeline....

edit: got it.

Reloaded alsa, went in to volume control, preferences, opened up ALL of the input options (analog front side back blah blah blah) - the normal analog output for the SBlive is mapped to analog front, which was all the way down.

---

### Post by Snipe3D on 2006-03-10
has anyone got a microphone working on an SB live?

---

### Post by raul_ on 2006-03-17
Hey...wassup =) hey everything was going fine till the 4th step where i get this message:
......
(etc etc)
....
checking for kernel version... The file /usr/src/linux-headers-2.6.10-6-386/KVERS=2.6.10-6-386-with-kernel=/lib/modules/2.6.10-6-386/build/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.10-6-386/build).
make: ** [configure-stamp] Erro 1


I'm not an expert but I don't think this is suppose to happen :rolleyes:  any ideas? 
Thanks in advance

[EDIT]: Hey update...don't know what happened...i restarted the computer and i didn't even need to finish the guide =) sound card up and running..thanks

---

### Post by semcapital on 2006-03-20
Hello.

First of all, thank you so much for this guide, it was great help. Following its instructions, I got my sound card to work perfectly. But, last weed I made a "dist-upgrade", and now my sound card doesn't work anymore. :cry:

I don't know what to do! When I do "modprobe snd-ca0106" the response is:
```
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-6-686-smp/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.10-6-686-smp/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-6-686-smp/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.10-6-686-smp/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ca0106 (/lib/modules/2.6.10-6-686-smp/updates/alsa/pci/ca0106/snd-ca0106.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_ca0106
```

My kernel is 2.6.10-6-686-smp. Please, help!

---

### Post by EKa on 2006-04-09
[QUOTE=Jesterace]Well I've been a dedicated slackware user for quite sometime and I have the dreaded value SB Live! 24Bit!. I was able to get it to work in slackware after I compiled alsa from cvs. ...
 

4th Step - Now it's time to make the Package

:)[/QUOTE]

Hi,

when trying to solve the problem common to most of us reading this thread i advanced to step 4 resulting

> You don't have the compiler that your kernel was built with installed
](*,) 

What can i do next? Any suggestions?

---

### Post by eddiesquared on 2006-05-03
Hi there. I am a total beginner with ubuntu/linux. how on earth do i get linux to send sound to all 5.1 of my speakers, rather then just the 2.1 is allowing me?? please help!

---

### Post by -Y- on 2006-12-11
Hello !
I'm trying to install my SB but I get this :
```
/usr/src/modules/alsa-driver/drivers/serialmidi.c:317: error: ‘struct tty_struct’ has no member named ‘atomic_write’
/usr/src/modules/alsa-driver/drivers/serialmidi.c:322: error: ‘struct tty_struct’ has no member named ‘atomic_write’
/usr/src/modules/alsa-driver/drivers/serialmidi.c:339: error: ‘struct tty_struct’ has no member named ‘atomic_write’
make[5]: *** [/usr/src/modules/alsa-driver/drivers/serialmidi.o] Erreur 1
make[4]: *** [/usr/src/modules/alsa-driver/drivers] Erreur 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Erreur 2
make[2]: *** [modules] Erreur 2
make[2]: quittant le répertoire « /usr/src/linux-headers-2.6.17-10-generic »
make[1]: *** [compile] Erreur 2
make[1]: quittant le répertoire « /usr/src/modules/alsa-driver »
make: *** [build-stamp] Erreur 2

```

Does someone knows what to do?
thx

---

### Post by The3rdhero on 2006-12-11
Just to add to this post, I've got a SB Live! 24bit external, when I run dapper, everything works great!

When I run edgy, the sound doesan't work anymore :(

Even with a dist-upgrade from dapper to edgy, the sound won't work.

Anyone got any ideas why it just decides to stop working with edgy?

Very confused because you'd think that since 6.06 or whatever dapper is and egdy is 6.10, you'd think that it'd work :(

---

### Post by ComplexNumber on 2006-12-31
> **The3rdhero said:**
> Just to add to this post, I've got a SB Live! 24bit external, when I run dapper, everything works great!

When I run edgy, the sound doesan't work anymore :(

Even with a dist-upgrade from dapper to edgy, the sound won't work.

Anyone got any ideas why it just decides to stop working with edgy?

Very confused because you'd think that since 6.06 or whatever dapper is and egdy is 6.10, you'd think that it'd work :(
today i messed up my fedora installation, so i thought i'd see if ubuntu could work correctly with sblive emu10k. fedora did (mostly) work with said sound card, but the bass and treble didn't work. ubuntu is exactly the same.  fantastic! :(

---

### Post by raffytaffy on 2007-07-11
raf@equinox2:/usr/src/modules/alsa-driver$ sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)
CC="gcc" ./configure --prefix=/usr --with-kernel=/usr/src/linux-headers-2.6.22-ck1/ --with-build=/usr/src/linux-headers-2.6.22-ck1/ --with-moddir=/lib/modules/2.6.22-ck1/updates/alsa --with-sequencer=yes --with-isapnp=yes --with-debug=detect --with-cards="ca0106"
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [configure-stamp] Error 77


i have build essential installed. problem persists.????

---

### Post by Terdog on 2007-09-08
I tried using this guide, and im stuck on

make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from include/linux/pci.h:55,
                 from /usr/src/modules/alsa-driver/acore/memalloc.inc:10,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/linux/pci_ids.h:2:68: error: /home/alsa/kernel/linux-2.6.17.8/include/linux/pci_ids.h: No such file or directory
make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [compile] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [build-stamp] Error 2
terry@terry-desktop:/usr/src/modules

---

