---
title: "Intel 82801G (ICH7 Family) HDA + Feisty = It just (won't) work."
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by Ted Nancy on 2007-06-02
There are literally dozens of posts on this subject, and I have literally tried every one of them *except* recompiling my kernel. I'm sorry, but sound is something that's so basic that it is really bothering me how *impossible* it seems to get working for anyone who isn't on the ALSA devel. list. It seems like it's broken in the kernel, or something. Anyone have any idea when a fix is coming? I wiped Vista off my new HP530 to go full on Ubuntu after great success with a Lenovo laptop. Now... bah... pull out the recovery disc. Sigh...

FYI:

ted@HP530:~$ uname -r
2.6.20-16-generic

ted@HP530:~$ modinfo soundcore
filename:       /lib/modules/2.6.20-16-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     45750F13477CBA5B6F36F46
depends:        
vermagic:       2.6.20-16-generic SMP mod_unload 586

ted@HP530:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Had standard Feisty installed ALSA. Compiling the newest RC2, 3, and 4 all returned errors. Now have nothing installed and must reinstall Feisty. Though I think I'll gparted a partition for Vista back on to this thing. I just want to do my work, not spend forever learning how to use linux and compile for sound.

---

### Post by Gast00n on 2007-06-02
Hi, 

Was looking to resolve similar problem with my brand-new FS XI1546, I just found it : 

Add to the bottom of /etc/modprobe.d/alsa-base:
options snd-intel-hda index=0 model=w810
(And reboot)

I had to try several times cos I didnt know the exact model name : 

Available "model name" in case of other HDA codec :
* AD1981
"hp"
"thinkpad"
"basic"
"6stack"

* AD1986A
"6stack"
"3stack"
"laptop"
"laptop-eapd"

* AD1988
"6stack"
"6stack-dig"
"3stack"
"3stack-dig"
"laptop"
"laptop-dig"

* CMI9880
"full"
"full_dig"
"allout"

* ALC260
"basic"
"hp"
"fujitsu"
"acer"
"test"

* ALC262
"basic"
"fujitsu"

* ALC861
"3stack"
"3stack-dig"
"6stack-dig"

* ALC880
"3stack"
"3stack-digout"
"5stack"
"5stack-digout"
"w810"
"z71v"
"6stack"
"6stack-digout"
"asus"
"uniwill"
"F1734"
"lg"
"lg-lw"
"test"

* ALC882
"3stack-dig"
"6stack-dig"

* STAC7661
"vaio"

---

### Post by cptcrunch on 2007-06-02
have you tried this yet?

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by cptcrunch on 2007-06-02
you can also try installing the latest development version of ALSA HG (Mercurial) version from

[ftp://ftp.suse.com/pub/projects/alsa/snapshot/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/)

and use the steps in this how to

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If that fails, it quite possible may be an ACPI issue. Fortunately I got lucky and managed to find a custom DSDT that worked for me.

Good luck.

---

### Post by Ted Nancy on 2007-06-02
@Gastoon: I take it then, you don't know of any command to determine the exact model, and avoid the trial and error method that you used? Anyone else?

@CpnCrunch: Yes, twice in fact. And I can't intall the latest drivers, at least not using those instructions or the ones on the AlSA page, since compile exits with errors. Something about a recursive error, repeats four or five times, then exits. Driver seems to work. Lib doesn't actualy say error, but looks funny. Utils just quits.

---

### Post by crimsun on 2007-06-03
> **Ted Nancy said:**
> And I can't intall the latest drivers, at least not using those instructions or the ones on the AlSA page, since compile exits with errors. Something about a recursive error, repeats four or five times, then exits. Driver seems to work. Lib doesn't actualy say error, but looks funny. Utils just quits.

You need the following packages installed first: build-essential, linux-headers-$(uname -r), autoconf, automake1.7, libtool, and mercurial.  Then execute the following commands in a Terminal/Konsole (copy and paste):

hg clone [http://hg.alsa-project.org/alsa-kernel](http://hg.alsa-project.org/alsa-kernel) alsa-kernel && hg clone [http://hg.alsa-project.org/alsa-driver](http://hg.alsa-project.org/alsa-driver) alsa-driver && cd alsa-driver && ./hgcompile --with-cards=hda-intel --with-oss=yes --with-sequencer=yes --with-kernel=/lib/modules/$(uname -r)/build --with-debug=full && make && sudo make install-modules

Afterward, make sure you remove any edits you've made to /etc/modprobe.d/* regarding snd-hda-intel, then reboot.

---

### Post by Ted Nancy on 2007-06-04
Thanks for that Crimsun. Hopefully it will help someone else out. I've decided to stick with Vista until I see that this issue is resolved. Like I said, I just want a functioning laptop to do my work on, and I just can't spare the hours invovled in reinstalling, testing this, then reverting again if it doesn't work. 

I'm downloading FC7 Live right now, because I haven't seen this issue on their forums. Hopefully, I'll be back!

---

### Post by jeffisawesome on 2007-06-05
I wouldn't bet on Fedora 7.  I've been struggling with the same sound card issue with F7.  Been going nuts over it in fact.  Came over here to see if you guys had found an answer.  You're better off with the debian based distro trust me.  Ubuntu for life baby.  (Boss won't see the light... wants to use Fedora because of Redhat...)

---

### Post by Ted Nancy on 2007-06-06
So I realized. I couldn't help it. Did a live of FC7, no joy. Reinstalled feisty clean. Nothing. Updates. Nothing. Check sound levels, mute, etc. All fine. Check for device. Recognized, proper drvier / modules loaded. Builtlatest alsa stable. Nothing. Tried adding options like model=hp, 3stack, etc. etc..

I then tried to file a bug report. The server was done. Linux hates me. Currently writing from Vista. Maybe after more people buy this wicked new HP laptop something will happen. Meanwhile, I'll file a bug report eventually, keep my eye on the forums from time to time, and continue to learn to like Vista.

---

### Post by janb on 2007-06-06
I'm having the same problem, with the same chip on a Acer Travelmate 4201WLMi.

The new full release of ALSA 1.0.14 came out 2 days ago. I wonder if Ubuntu is going to incorporate it, and if I should wait for their updates, or try and do the manual thing and just get frustrated like Ted.

I sent a mail to Crimsun for an answer, seeing that he is a developer specialising in this.
Hoping for an answer real soon.

I wouldn't want to go back to MicroFsoft neither.

---

### Post by janb on 2007-06-06
This is the answer from Crimsun:

> Feisty will not be upgrading to ALSA 1.0.14.  I've backported as many of
the non-invasive -{kernel,driver,lib} patches as possible.

Gutsy main is currently frozen for Tribe1, but we will be getting 1.0.14
soon.  I will revert the most current "improved resampling" patch, as
that has caused issues (reported against Feisty).


I suppose we just have to wait?

---

### Post by Espionage724 on 2007-06-06
I have a Acer TravelMate 2480 laptop with Intel HDA driver installed. My real driver is supposed to be Realtek HD Audio (doesn't matter to me though) anyway if your sound isnt working when you fresh install Ubuntu Feisty just go to ur mixer and turn all devices on and max the volume on them and it should work

---

### Post by kamwla on 2007-06-12
Guys what do you think about this?

I use Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller on Toshiba P100-188.

After successful installation of hda intel alsa drivers there is no sound
when i try to open system>preferences>sound I get his message

'The application "gnome-sound-properties" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.''

when i go to details i get

Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/gstreamer/0.10/default/audiosink' set in a read-only source at the front of your configuration path
Any ideas how to deal with it  I am completely hopeless :-(

---

### Post by janb on 2007-06-14
This is really weird.
I finally got my microphone working, and all was well under kernel 2.6.20-15.

Then my computer upgraded to kernel 2.6.20-16, and all of a sudden all sound is gone. As in Zip, Niks, Nada.
No speaker, no microphone, no headphone.

The speaker icon has a red flag, and when trying to adjust the settings, it says

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

HOWEVER, if I boot up with the old kernel, 2.6.20-15, it all works again.

Can someone explain that one to me? (and help me rectify this)

---

### Post by ofir_k on 2007-06-20
Hello,

I have Lenovo 3000 N100 with Intel 82801G HDA (ICH7...) ALC861VD sound card.

I also encountered the same problem as many of you.

I searched the internet a little bit, searched in alsa's website, launchpad and in Ubuntu Wiki, and finally I found the desired solution.

The solution can be found in here: [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)
Just scroll down to the notes section and under Sound you will find what you are looking for.

> The sound is now fixed, here's how to get it working, I have done this in Feisty as it is now the current release, it should work for Edgy. Make sure the on-board modem is enabled in the BIOS.

Note: If you would rather not recompile ALSA yourself, you can download the requisite kernel modules, built from the latest ALSA development sources from the Mercurial repos (as of 20070519), [WWW] [here]("http://codepolice.org/files/alsa-hg-hda-intel.tar.gz"). This is rather hackish, but should work with Feisty with the latest updates -- no guarantees, however. Install as follows, and then restart the computer:

```
cd /lib/modules/`uname -r`
sudo tar zxvf ~/alsa-hg-hda-intel.tar.gz (or path to downloaded file)
sudo depmod -a
```


Hope this will solve the problem.

Note: I tried it on 2.6.20-15-generic kernel and now I am going to try it on 2.6.20-16-generic. I will post here the results!

Good Luck! ;)

---

### Post by ofir_k on 2007-06-20
It also works on 2.6.20-16-generic ! :p

---

### Post by zachflanders on 2007-06-20
OK, i tried the above soultion suggested by ofir_k to try and get my microphone working with 2.6.20-16-lowlatency, and . . . it didn't work.

I had sound before, and i still do, but now it seems really grainy.

My microphone still isn't working.

When I run alsamixer in the terminal I get all kinds of items.

For Playback I get: master (with a bar), PCM (with a bar),  IEC958 (with MM), Ext Mic (with a bar), and INT Mic (with a bar).

Under Capture I get:  Line In (without a bar), capture (with a bar), Ext Mic (with a bar), Int Mic (with a bar), and IntMic (without a bar).

I can turn CAPTUR on and off (with the space bar) for capture, and i can turn capture on for Line In, and IntMic (the one without a bar) but only one at a time, and a least one is on all the time (when one is on, the other is off, i can't turn both off at the same time)

I am very confused

Please help if you can.

Screen shot of alsamixer:
[IMG]http://farm2.static.flickr.com/1056/576924117_1ec0f48a0a_o.png[/IMG]

---

### Post by ofir_k on 2007-06-21
I really don't know anything about capturing...

I tried it in my laptop and it also didn't work....

I think that the above 'patch' is only meant for playback...

---

### Post by johntkucz on 2007-06-21
I agree with nancy, sound is pretty fundamental.  I know ubuntu is a collaborative project, but this is outraeously ridiculous that so many people (self included) can't get sound.

---

### Post by KovaZg on 2007-06-21
I also have:

Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

 sudo lsmod | grep snd
snd_hda_intel          22552  3 
snd_hda_codec         213376  1 snd_hda_intel
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            35200  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54000  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  3 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
snd                    56324  13 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm


Thing is, I had Ubuntu 2 days ago, then I tried OSX, then back on Ubuntu. I managed to solve problem with sound 2 days ago, but now, I can't find solution.

Nothing helped. Tried 1.0.14rc4, and rc3 ... 

Added both lines:

options snd-hda-intel model=3stack 

and even:

options snd-intel-hda index=0 model=w810

Then removed those lines from etc/.../alsa-base

Tried to copy paste that big line that Cirsume wrote, but nothing, like installation passes ok, but nothing happend, still no sound.

Funny thing is that my player is playing songs, but there is no sound. I checked 10 times, nothing is muted, I can't test it in Sound properties, no sound there either ..

I feel so stupid as I can't remember what I did last time, to make my sound work.

I have Asus V1JP laptop.

Anybody ? I know it can work. PLEASE.

2 mins LATER:
I found that PCM was muted, or not muted, I don't know, I just pressed M and right arrow few times, then TAB then again, and I put song on play, so I did changes in play, and I heard it, and thats it, PCM was one I changed ... 

And then I remebered, that i found solution here on forum somewhere, when somebody mentioned, just PCM !!! If this helps, alsamixer, PCM (unmute). 

Cheers. Now to solve Wireless problem :)

---

### Post by cddeluca on 2007-06-22
> **Ted Nancy said:**
> So I realized. I couldn't help it. Did a live of FC7, no joy. Reinstalled feisty clean. Nothing. Updates. Nothing. Check sound levels, mute, etc. All fine. Check for device. Recognized, proper drvier / modules loaded. Builtlatest alsa stable. Nothing. Tried adding options like model=hp, 3stack, etc. etc... 

I've been through the same thing with Toshiba A135-S4527, 82801GBM (ICH7), ALC861VD on-board sound.

Done everything Google can find; every listed variation of snd-hda-intel in /modprobe.d/alsa-base; re-(move) (install) alsa utils; reverted to old kernel; mixer all unmuted and max volume everywhere. Module loads; card recognized; the whole nine yards and back - everything looks perfect according to about 10 wikis and 10,000 threads but no sound, no how.

<b>Slight</b> difference in my problem though - It worked before I installed Vista dual-boot. Previously all I had to do was add "options snd-hda-intel model=auto" to alsa-base and it worked. Since I wiped the disk, installed Vista on the first partition and re-installed FF 7.04 that fix no longer works.

I know NOTHING so any speculation on my part is silly, but I know MS has a deal with Phoenix (used by Toshiba) to "customize" their BIOS for Vista - I wonder if the Vista install changed something in the BIOS? It's not anything visible in the BIOS option menus; it's all the same as it was before the Vista install.

Another thing is that the processor and chipset (PENTIUM DUAL CORE T2080 - NOT CORE DUO and 945GMS) are some sort of OEM deal -they're not acknowledged anywhere on Intel's website.

I must have Vista because (1) it came with the machine and I ain't buying another copy of MS anything and (2) I need Winblows to run some commercial instrumentation configuration software that will never be ported to *nix.

ANY help or suggestion would be deeply appreciated.

charlie

---

### Post by cddeluca on 2007-06-22
So out of frustration (or masochism) I cycled through all the alsa-base "options snd-hda-intel   model=???" that I've tried for days but THIS TIME "3stack" WORKED!

Didn't work an hour ago, but works now.

I know that without a formal change log there's every likelihood that I tweaked something else concurrently and don't recognize it, but I don't remember any other configuration changes.

FWIW

---

### Post by ofir_k on 2007-06-25
> **johntkucz said:**
> I agree with nancy, sound is pretty fundamental.  I know ubuntu is a collaborative project, but this is outraeously ridiculous that so many people (self included) can't get sound.

Indeed!

If Ubuntu won't support 90% of the hardware out-of-the-box, users won't switch to it!

I don't know how drivers in Linux works nor in Windows, but if Windows drivers could be used in Linux without any command-line use, it will be perfect, since companies are already developing drivers for Windows, and for them just to test them on Linux, instead of write them from scratch, would be a huge incentive to support Linux and support it!

---

### Post by Ted Nancy on 2007-07-06
OMFG... it works. What did I do different? I removed Vista. Installed. Worked out of the box. There may be nothing at all wrong with Ubuntu, ALSA, none of it. Vista is doing something that messes it up.

I removed Vista. Reset Bios defaults, installed, voila. Sound goodness.

---

### Post by fredj on 2007-07-07
"If Ubuntu won't support 90% of the hardware out-of-the-box, users won't switch to it!

I don't know how drivers in Linux works nor in Windows, but if Windows drivers could be used in Linux without any command-line use, it will be perfect, since companies are already developing drivers for Windows, and for them just to test them on Linux, instead of write them from scratch, would be a huge incentive to support Linux and support it!"

I suspect that people who make this sort of post have never tried to install Vista or XP on a computer. They
have bought computers with the Windows pre installed. I know from experience that MS Windows doesn't just
work out of the box.

---

### Post by moore.bryan on 2007-07-27
[I]this is driving me CRAZY, so i hope someone can shed light on this for me...
lspci shows this:```
moore@ubuntu:/etc/modprobe.d$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controlle                                          r Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Grap                                          hics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Co                                          ntroller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 0                                          2)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller                                           AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752M Gigabit Ethernet PCI Express (r                                          ev 02)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
15:00.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
15:00.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/x                                          D)
15:00.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host C                                          ontroller

```but aplay -l shows this:
```
moore@ubuntu:/etc/modprobe.d$ aplay -l
]aplay: device_list:222: no soundcards found...

```WTF?  i had sound working LAST NIGHT and now this?  i try to reinstall alsa-drivers and everything just leaves with errors.
i'm running kernel-2.6.20-16-server with openbox; no gnome, no kde, no xfce.
PLEASE HELP!
[/I]-----
EDIT
-----
[i]nevermind... i finally got it to compile by specifying the kernel path on each step.  getting sound to work should NOT be this difficult.

---

### Post by gagiz on 2007-07-30
Hello,
I have toshiba satellite a135 with intel HDA ALC861-VD. Had simmilar problem - no sound :(... Fixed by adding the line to /etc/modprobe.d/alsa-base with model=3stack. Everything works perfect after reboot :). Just wanted to thank for the help.

---

### Post by NNxD on 2007-08-24
is there a solution on this problem yet? i have the same problem...

---

### Post by NNxD on 2007-08-24
Sorry, please disregard my last post.

I have installed Asla and also tried all the other steps, now, after rebooting it kinda worked. Its all on full blast! Very loud feedback, because the microphone is also on and there is incredible feedback. No way of turning anything down in sound control, nor using the buttons (on a Lenovo 3000 N100, Realtek ASC861VD). This is a lot worse then no sound at all, especially because its middle of the night and I woke up the whole house.  .. :mad:

---

### Post by PeterWalgreens on 2007-08-26
> **Ted Nancy said:**
> OMFG... it works. What did I do different? I removed Vista. Installed. Worked out of the box. There may be nothing at all wrong with Ubuntu, ALSA, none of it. Vista is doing something that messes it up.

I removed Vista. Reset Bios defaults, installed, voila. Sound goodness.

Wait, how do I do that?

---

### Post by PeterWalgreens on 2007-08-28
Does anyone else have a solution?

---

### Post by MikeSTL on 2007-09-10
Hi all,

Like a lot of you I was having video resolution and sound problems with my HP530. While running 7.04 I was able to set the resolution to the correct 1280x800, using 915resolution, but never got the sound to work. Not a squeak!

Throwing caution to the wind, I d/l Ubuntu 7.10. Video worked right off the bat, but still no sound. Remembering what others said about running Alsamixer to check volume levels, I installed Gnome Alsa Mixer from the Add/Remove menu.

I made sure the Master, PCM, and Digital volumes were all turned up, and checked the boxes marked IEC958 and IntMic at the bottom of the window.

In the Sound Preferences control panel, everything is set to "Autodetect". 

Sound now works! :)

I did not edit any conf files. Hope this helps somebody...I was really hating life...It has been a long time since an Ubuntu install did not recognize everything. I am just writing it off to the fact that this is a very new laptop. It is the dual core, 1 gig ram, 120 gig HD one that Tiger Direct is selling.

Mike

---

### Post by wnmnkh on 2007-09-13
Guess it still hasn't resolved in latest 7.10 (tribe 5.)

Did all things and it simply did not work. (Sony VAIO FZ)

---

