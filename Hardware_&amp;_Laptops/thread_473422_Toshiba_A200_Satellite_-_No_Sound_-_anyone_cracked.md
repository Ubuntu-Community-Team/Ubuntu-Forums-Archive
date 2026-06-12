---
title: "Toshiba A200 Satellite - No Sound - anyone cracked it yet?"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by matheuu on 2007-06-14
Intel HDA sound card 
Feisty 
no sound 
card detected.
sucks heaps

anyone figured out how to make it work?

---

### Post by Unreal223linux on 2007-06-14
I just managed to get sound working on my toshiba l35. I just typed up how I did it here:
[http://ubuntuforums.org/showthread.php?t=473425](http://ubuntuforums.org/showthread.php?t=473425)

I hope this works for you as well as it did for me! I'm so happy no more junky windows xp!

---

### Post by matheuu on 2007-06-16
nah.  sorry, not working for my toshiba a200.

do you have the same card?

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


cheers

---

### Post by thobbs on 2007-06-16
i am no expert at this, but a friend of mine managed to get the sound working on my Thinkpad after about 2 hours - i was using feisty then, something about installing and getting the correct modem drivers, this made the soundcard work correctly??? Sorry - not able to contact him at the moment and i have just installed Gutsy - obviously have no sound again :( and would like to know if anyone else had any ideas which might work?

---

### Post by matheuu on 2007-06-16
Hey Thobbs,
what kind of sound card have you got?

---

### Post by tsella on 2007-06-16
well, i got it working just fine by moving to gutsy -
```

sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

NOTE: the above is a bit of a large change, moving to a yet unreleased version of ubuntu. think 10 times before making the jump.

a friend of mine who has the same laptop mentioned he was able to get audio working by adding a line to alsa config. i have asked him for it, and will share when i get it.

---

### Post by sci-fi guy on 2007-06-16
> **tsella said:**
> well, i got it working just fine by moving to gutsy -
```

sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

NOTE: the above is a bit of a large change, moving to a yet unreleased version of ubuntu. think 10 times before making the jump.

a friend of mine who has the same laptop mentioned he was able to get audio working by adding a line to alsa config. i have asked him for it, and will share when i get it.

Gutsy didn't work for my A205's sound, but I updated from a disc with errors in 13 files.  I had been babysitting the torrent for 6 hours (on Vista) and was not interested in doing it over.  Went back to Fiesty when it did not work. Since the above lines will (I assume) update to Gutsy without a disc, any chance that it could help me?

---

### Post by tsella on 2007-06-16
> **sci-fi guy said:**
> Gutsy didn't work for my A205's sound.

what is the difference between the A200 and A205?

---

### Post by sci-fi guy on 2007-06-16
Dunno

---

### Post by voltagex on 2007-06-16
[http://ubuntuforums.org/showthread.php?t=473425](http://ubuntuforums.org/showthread.php?t=473425)

Some instructions on how to load the latest sound drivers (including Intel HDA by the look of it)

---

### Post by sci-fi guy on 2007-06-16
Tried that before (same issue as post #2 of that thread).

---

### Post by tsella on 2007-06-17
> **tsella said:**
> 
a friend of mine who has the same laptop mentioned he was able to get audio working by adding a line to alsa config. i have asked him for it, and will share when i get it.

according to my friend, who did not update to gutsy, yet got it to work, you need to add the following line to **/etc/modprobe.d/alsa-base**
```
options snd-hda-intel model=3stack
```

---

### Post by matheuu on 2007-06-17
Hey Tsella,

Cheers for helping. I haven't tryed upgrading to gutsy yet. Thinking about it.. Not sure it will work.
Adding that line to the end of the alsa-base doesn't seem to work for any of the A series Toshibas, A100, A105, A200 and A205's probably more.

Actually adding anything to the alsa-base doesn't seem to work.
Apparently there is no driver for the kind of chip used on these cards.

Let me know if you hear anything.  I am going to try your gutsy upgrade, will put my results up

---

### Post by matheuu on 2007-06-23
I am thinking that my alsamixer is rooted. 
This is what is looks like.... I am sure there should be more options...and I am not sure that the sound card has a realtek chip?

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.13 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ID 268                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00]                                            &#9474;
&#9474;                                                                              &#9474;
&#9474;           &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;             &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;            &#9474;
&#9474;                                             &#9474;MM&#9474;             &#9474;MM&#9474;            &#9474;
&#9474;                                             &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;            &#9474;
&#9474;         100<>100         100<>100                                            &#9474;
&#9474;        < Master >          PCM            Caller I         Off-hook          &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by sci-fi guy on 2007-06-24
Interesting.  On my system, the first two columns are not muted, just the second two. But I have no sound anyway. In alsamixer, did you hit the "M" key to unmute (look down at the bottom where it says "MM")?

---

### Post by matheuu on 2007-06-28
Actually, Mine is the same as yours. The alsamixer screen wont copy properly. There are actually four columns . The last two seem to be for a modem(they are both muted-tried un-muting them but still nothing) and the Master and PCM are 100%. 

On my desktop I have heaps of sound mixer options, like surround, left, right aux, headphone etc, etc.

I think this laptop should have a few more options than just Master and PCM(what ever that is)

---

### Post by brightsmile on 2007-06-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.beta.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.beta.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				matheuu, I have the same problem -- seems to be the bug filed here:
[https://bugs.beta.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.beta.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326)

Chris Cheney wrote he intents to fix it soon... let's cross our fingers! -- And maybe subscribe there so the devs will give it more attention?

---

### Post by bradmayne on 2007-07-02
options snd-hda-intel model=3stack

---

### Post by spupy on 2007-07-02
Just my two cents:
I got Toshiba A110, which i think has the same Intel HDA.
I have no sound on startup, so everytime i start the pc  i do this:
```
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
```
I put it in a script of course. It works for me but its annoying - need to do it at every boot :/

---

### Post by brightsmile on 2007-07-02
Check here:
[https://bugs.launchpad.net/bugs/116326](https://bugs.launchpad.net/bugs/116326)

Pls comment there, so the devs will know.

---

### Post by brightsmile on 2007-07-02
There's a new patch to fix this, which seems to be working, so pls check the link in my previous post.

---

### Post by matheuu on 2007-07-10
Hey Brightsmile,

Did you get yours to work?

---

### Post by brightsmile on 2007-07-10
I really don't have time for now to try the current version of Chris Cheney's patch...

...but this patch is still being actively worked on.. so I'll probably wait till it's complete.

But if you do go ahead with it, let us know the results in that launchpad thread.
Thanks.

---

### Post by bvmou on 2007-07-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

**UPDATE 2**:  There is a top-to-bottom solution to this problem posted here: [http://ubuntuforums.org/showthread.php?t=568463#1]("http://ubuntuforums.org/showthread.php?t=568463#1"). 

**UPDATE: **  THE NEW VERSION OF ALSA WORKS WITH NO PATCH AND CORRECTS THE HEADPHONE MUTE ISSUE.  Get 1.0.15rc1 at [www.alsa-project.org](www.alsa-project.org)[www.alsa-project.org]("www.alsa-project.org") ; I also left a few words at the end of the thread on this happy news, big thanks to ALSA project.

				
				I got an A205 working which has the ALC268 Codec.  It is not perfect (headphones work but do not automatically mute speakers, etc., but this is a big improvement after a week without sound.)

The procedure:

Dowload ALSA latest version from alsa-project.org.  This consists of drivers, libraries, utils, tools, and firmware.

Get the patches discussed and linked in this launchpad discussion: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326)
(They will be called realtek10.tar.gz and realtek11.tar.gz)

Extract the ALSA source to a convenient location, such as /home/user/alsa

Go to the directory (it will be called this wherever you extract it to) ~/alsa-driver-1.0.14/alsa-kernel/pci/hda

There you will find two files with names identical to the ones in the patches.  Replace the old patch_realtek.c with the new one.  Same with the hda_proc.c  You can do this by simply dragging the new version into the correct folder, and you will be asked if you want to replace the file, which you do.

Once you have patched the ALSA driver, you compile as normal.  Go to the alsa-lib folder, and type:

sudo ./configure
sudo make
sudo make install

After this is done, do the same for all the other folders you downloaded from ALSA-project.org, such as alsa-utils..., alsa-driver..., etc. (Tools is a bit beyond me, to be honest, and this may be why I have ironing out to do.)

Like I said this left me with a slightly quirky setup and may not be ideal, but I know the feeling of having uncooperative hardware so give this a shot and let us know how it goes.  Be sure to add the packages noted below by Julian if you do not have them installed already.

---

### Post by gfd on 2007-07-13
> **bvmou said:**
> I got an A205 working which has the ALC268 Codec. 

I got an **A200** working following your instructions bvmou!

As you said, the headphones don't mute the speakers but hey... I have sound!!

You did however, say that they don't do it "automatically". 
Did you figure out some way to do it manually?

I tried messing about with the alsamixer but without success.

thanks a million!

---

### Post by santoxyz on 2007-07-13
can be my post about fujitsu v3515 helps:

[http://ubuntuforums.org/showthread.php?t=500274](http://ubuntuforums.org/showthread.php?t=500274)


good luck!

---

### Post by bvmou on 2007-07-14
It is possible to mute the built-in speakers and use only the headphones by one method, but the catch is that any use of the onboard sound controls seems to supplant the changes I make in the terminal-based alsamixer gui.  To see if this works for you, enter alsamixer in terminal and lower the "Front" level to zero while leaving the "Headphon" setting as-is.  That should work but if at any time you use the sound control hardware on the front of the laptop your hand-set values will be replaced by the values given by the volume wheel.  For me its a kludge but is working well enough to use on planes or near sleeping people.

Glad to hear the fix is mostly working :)

---

### Post by julian.coccia on 2007-07-21
Thank you for the info bvmou. I simply wanted to add something for new users. In order to be able to compile this, you must install gettext and ja-trans, otherwise compilation fails. Also, most recently installed systems won't even have build-essential installed. In few words, it's safe to say a user must run this before compiling the alsa driver:

**sudo apt-get install build-essential gettext ja-trans**

Last, if you try to compile alsa-utils first (as you explained) without having compiled and installed alsa-lib first, compilation would fail. I have compiled everything in this order: alsa-driver, alsa-lib, alsa-util and alsa-firmware.

Cheers,
Julian

---

### Post by julian.coccia on 2007-07-21
BTW, I forgot to mention that **IT WORKED** for me following bvmou's suggesions. I'm running 7.04 on a Toshiba Satellite A200-1C0

Also, alsa-tools are not needed to fix the problem. I have only installed alsa-driver, alsa-lib, alsa-util and alsa-firmware (in that particular order)

---

### Post by CalvinK on 2007-07-25
without moving to gutsy there are some threads here to obtain a sound working :
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto).
[http://doc.ubuntu-fr.org/installation/son](http://doc.ubuntu-fr.org/installation/son) (in French)
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
I added 3mask at the end of the file detailed in these threads. The sound works but  the speakers dont shut when I plug the earphone.

with Toshiba A200 the common problems are : 
[LIST]
[*]sound card not recognized
[*]Chicony Webcam not recognized by easycam2 nor by camorama
[*]bug in the bios but you can forget it . Presently there is no alternate solution for this and you only have that disturbing message at boot However, hibernation doesn't work.
[/LIST]
Good luck !
calvinK:lolflag:

---

### Post by rast4man on 2007-07-25
Thank you for all of the information, collaboratively. I managed to get my sound working on my Feisty 7.04 Toshiba A205-S4607. The main link which worked was [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) I am grateful for all of the information. Now to tackle the Chicony Webcam. :)

---

### Post by CalvinK on 2007-07-29
I am interested by this problem of webcam which doesn't seem to be easy. I dont know where to obtain the driver for Linux (not at Chicony Ltd) but it works with Ekiga. Unfortunately I cannot tune the image or the sound without an error message. It seems to work with Gutsy. I tried to upgrade my kernel but it doesn't work. Thanks for any clue.:confused:

---

### Post by gokay on 2007-07-30
Yeah i know that i am newbie but i did everything and it is still not working. So what now? :(

---

### Post by bvmou on 2007-08-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

**UPDATE 2:**  There is a top-to-bottom solution to this problem posted here: [http://ubuntuforums.org/showthread.php?t=568463#1]("http://ubuntuforums.org/showthread.php?t=568463#1"). 

				Just a heads-up if anyone has trouble with the HdaIntelSoundHowto Tutorial that worked for Rast4Man: the unpatched ALSA Intel HDA driver will not work for the ALC268 codec, if you get sound after upgrading to the most current version of ALSA you have supported hardware.  If the output of:

```
cat /proc/asound/*
```

gives you a line about ALC268 Analog, you have a codec that is not yet merged into the main ALSA package, that is the problem that gave rise to this thread but for which a patch exists.  The general Intel instructions that worked for Rast4Man will not work with this subset of hardware.  You can fix it by applying the patch that was tracked down by some Launchpad contributors here: 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326)

There are some pointers about how to apply the patch on page three of this thread.

RE the webcam, has anyone had success with the uvcvideo?

---

### Post by dehuszar on 2007-08-11
For me, using a Satellite U305-S5097, the webcam works out of the box with Ekiga.  I think it's only supported by v4l2 apps.  If there are drivers for use with v4l1 apps, I don't know about em.

---

### Post by matheuu on 2007-09-09
Hey anyone out there?
Does this look normal?

Tried the patch etc put up by Brian (with the mods) still nothing?


mat@mat-laptop:~$ cat /proc/asound/*
cat: /proc/asound/card0: Is a directory
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0b40000 irq 21
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 22: [ 0- 6]: digital audio playback
 24: [ 0- 0]: digital audio capture
 30: [ 0- 6]: digital audio capture
 33:        : timer
cat: /proc/asound/Intel: Is a directory
 0 snd_hda_intel
cat: /proc/asound/oss: Is a directory
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-00: HDA Generic : HDA Generic : playback 1 : capture 1
cat: /proc/asound/seq: Is a directory
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
  Client application 5394 : running
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-6-0: PCM playback 0-6-0 : SLAVE
P0-6-1: PCM capture 0-6-1 : SLAVE
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Sep  1 2007 for kernel 2.6.20-16-generic (SMP).

Cheers
Mat

---

### Post by bvmou on 2007-09-12
Comrades, especially Mattheu!,

**UPDATE 2:**  There is a top-to-bottom solution to this problem posted here: [http://ubuntuforums.org/showthread.php?t=568463#1]("http://ubuntuforums.org/showthread.php?t=568463#1"). 

I just built release candidate 1 of alsa-*.1.0.15, and everything works, including automatic mute of speakers when headphones inserted!  There are several mentions of our codec in the release notes.

To build, the instructions are the same as on page three of this thread, also be sure to follow julian.coccia's build order and pointers.  The only change of course is that you will be building alsa-driver-1.0.15rc1, alsa-lib-1.0.15rc1, etc.

Mattheu, feel free to post here or by PM with questions, I can't wait to see your sig changed.

---

### Post by HannahK on 2007-09-19
Hi matheuu,

Finally the sound is working on my Toshiba a200!  If you or anyone else with this laptop are still having trouble this is what I did (running feisty):

Followed bvmou's & julian's instructions from page 3 of this thread using the stable alsa release. 

I then changed "model=3stack" to "model=toshiba" in /etc/modprobe.d/alsa-base, rebooted and voila!!

My mic does not work and headphones do not mute the speakers but I'm not too bothered right now!!

HannahK

---

### Post by rzrgenesys187 on 2007-09-19
This worked **perfectly** for my toshiba satellite p105-s6177

[http://ubuntuforums.org/showthread.php?t=349491&highlight=p105-s6177](http://ubuntuforums.org/showthread.php?t=349491&highlight=p105-s6177)

---

### Post by CalvinK on 2007-09-30
> **HannahK said:**
> Hi matheuu,

Finally the sound is working on my Toshiba a200!  If you or anyone else with this laptop are still having trouble this is what I did (running feisty):

Followed bvmou's & julian's instructions from page 3 of this thread using the stable alsa release. 

I then changed "model=3stack" to "model=toshiba" in /etc/modprobe.d/alsa-base, rebooted and voila!!

My mic does not work and headphones do not mute the speakers but I'm not too bothered right now!!

HannahK


Finally, my headphone mute the speakers with the following trick : I was searching the realtek ALC861-VD which is the sound card of the Toshiba A200. Fortunately, when compiling the latest version of alsa-driver-1.0.15rc2 with the ad hoc lib and utils, I discovered than the patch was already applied. So it's very simple, just do it and add a new line at the end of /etc/modprobe.d/alsa-base :
*options snd-hda-intel position_fix=1 model=lenovo*
It should correct the problem.
Caution !! You should repeat the procedure (compilation of alsa-driver, lib and utils after the last update which destroyed my config.

PS : For those who own the Satellite A200 model, I have also straigthen out the problem of the webcam using the sn9cxxx driver which is available as a debian package and corrected the problem of gnome sleeping procedure by adding* -force* to the scripts which use s2ram, namely 
*sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux*
and in lines that say
[I]elif [ -x "/sbin/s2ram" ] ; then
/sbin/s2ram -f <--------Add the -f to force suspend
RET=$?[/I]
 and correcting the uswsusp.conf file for the memory-_size.  I will post something if I manage to correct the faulty hibernation but s2disk doesn't work and I am reluctant at the idea of recompiling the kernel to integrate suspend2.

---

### Post by squirage on 2007-10-05
Hi, this thread is a life saver.

I just wanted to thank everyone here for posting their fixes, especially mathheu for intitiating it, bvmou for writing the new alsa code and julian.coccia for the procedural tips.

I was going to post how I did it here but I'll start another thread for that so as not to clutter this one up.

One thing I will say is that I think that 

```
cat /proc/asound/card0/codec#* | grep Codec
```

is a better way to find your sound card/chip because you don't have to search through any other code. Perhaps it is not so good if you have a lot of sound cards.

I don't know about my mic, but my headphones do not work, nor do my speakers mute when something is plugged in the jack.

I will try CalvinK's suggestion:
> Finally, my headphone mute the speakers with the following trick : I was searching the realtek ALC861-VD which is the sound card of the Toshiba A200. Fortunately, when compiling the latest version of alsa-driver-1.0.15rc2 with the ad hoc lib and utils, I discovered than the patch was already applied. So it's very simple, just do it and add a new line at the end of /etc/modprobe.d/alsa-base :
options snd-hda-intel position_fix=1 model=lenovo
It should correct the problem.

My A135-S4477 also shows the ALC861-VD chip.

Thanks again to all who have contributed. It's nice to know that non programmers can follow the things outlined here and achieve results.

---

### Post by squirage on 2007-10-05
Hi,

I just wanted to confirm that CalvinK's fix definitely works.

```
options snd-hda-intel position_fix=1 model=lenovo
```

Added to the end of /etc/modprobe.d/alsa-base

Thanks again, I'm rockin' now.:guitar:

---

### Post by LaGTaLiTy on 2007-10-05
i have the same sound card as matheuu's (Intel Corp 82801G (ICH7 Family) High Definition Audio Controller (rev 02) and also have no sound whatsoever...

edit: i don't have a Toshiba like most people with the problem, i have a Lenovo IBM Thinkpad T60

---

### Post by LaGTaLiTy on 2007-10-08
that's weird... i don't know what i did but today the sound is working all of a sudden.
:)  i hope it stays.

---

### Post by Kennoo on 2007-10-10
> **CalvinK said:**
> Finally, my headphone mute the speakers with the following trick : I was searching the realtek ALC861-VD which is the sound card of the Toshiba A200. Fortunately, when compiling the latest version of alsa-driver-1.0.15rc2 with the ad hoc lib and utils, I discovered than the patch was already applied. So it's very simple, just do it and add a new line at the end of /etc/modprobe.d/alsa-base :
*options snd-hda-intel position_fix=1 model=lenovo*
It should correct the problem.
Caution !! You should repeat the procedure (compilation of alsa-driver, lib and utils after the last update which destroyed my config.
...


I don't know what to say beside: "Thank you, thank you, and thank you a million." I'm a Debian user owning an A200. I've been using this laptop without sound even since I bought it about 4 or 5 months ago.

Just wanna recap what I did to get the sound working:

- installing alsa 1.0.15rc1
- appending <code>options snd-hda-intel position_fix=1 model=lenovo</code> to /etc/modeprob.d/alsa-base

Thanks again CalvinK and everyone.

---

### Post by bvmou on 2007-10-12
If anyone comes to this thread looking for the solution you should know that Squirage has posted the definitive guide to solving this problem here: [http://ubuntuforums.org/showthread.php?t=568463#1]("http://ubuntuforums.org/showthread.php?t=568463#1").  Whatever happened to the clapping smiley face?

Mattheu, we want a new sig soon!  Also, Squirage, since this thread has a lot of searches already (and relevant terms), post your solution or a synthesis of it and the subsequent postings so that it remains visible.  Unfortunately I don't think the relevant release of ALSA made it into Gutsy in time (please correct me) for those of us who got this otherwise excellent laptop.

---

### Post by joenjeru on 2007-11-10
Greetings,

I have a Toshiba Satellite A200-1CR. 

My speakers would still play music when my headphones were connected. I used the following options on my Fedora Core 7 /etc/modprobe.conf

options snd-hda-intel model=lenovo

Has worked as should since.

Hope this helps.

Regards,

Joe
Linux User: #361092 
Living Linux in Nairobi

---

### Post by john3333 on 2007-11-26
Hey, thanks Joenjeru.
I tried all the suggested fixes to get the Feisty headphone jack to work on my Satellite A200-AH9 and none worked except yours, although it did cut down a bit on the features of the volume control. Now it does mute the main speakers when I plug in my headphones.
Funny that adding various options lines to /etc/modprobe.d/alsa-base did not work for me. 
But replacing the text in /etc/modprobe.conf with snd-hda-intel model=lenovo did the trick.
One other thing I found: To test if changes took effect, I had to completely reboot -- not just use the Ctrl-Alt-Backspace fast restart, as this did not make any changes I made take effect. 
Thanks again Joenjeru.

---

