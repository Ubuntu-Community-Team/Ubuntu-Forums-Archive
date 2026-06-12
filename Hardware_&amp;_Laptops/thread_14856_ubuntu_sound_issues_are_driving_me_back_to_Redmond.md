---
title: "ubuntu sound issues are driving me back to Redmond!"
date: 2005-02-10
forum: Hardware &amp; Laptops
---

### Post by sharkzf6 on 2005-02-10
My ubuntu/Linux journey has been one of much frustration with an occasional success thrown in from time to time. I thought getting the nVidia 66.29 drivers installed was a challenge until I figured out what the packages in synaptic were, then it was a snap. My real issue with ubuntu so far is with sound/multimedia.

I started out with an old SB live sound card, which, of course, works perfectly. After getting everything else working, I decided I was getting good at this and thought I'd try my hand at getting the Audigy LS working which is what I use in WinXP (it sounds awesome compared to the old SB live). To make a long story short, I've gone from thinking I didn't have Audigy LS/ALSA support (ALSA version 1.0.6), to thinking it should actually be in there (ALSA was upgraded to 1.0.8 during a synaptic session), to knowing it's actually in there (according to ALSA's web site the Audigy LS driver is built-in to versions 1.0.6a and higher), though it still didn't work!? I ultimately gave up on the Audigy and tried the integrated sound on my motherboard (ALC655 – aka AC97). Upon booting up after the switch, I had sound at the GDM login screen – hallelujah! Gnome booted up and all sounds were enabled – I thought I was in good shape until I tried to play a music CD. It loaded but wouldn't “play”. Then I tried Doom 3 which worked perfectly with the SB live. The Doom 3 server reported that the sound device was busy...no sounds during game play. After scouring the internet I came across a post where a guy pointed out he had a similar problem and switched the Multimedia System Selector from ASLA to ESD which gave him sound. I did the same and could play music CDs but still no sound in Doom 3. Also, I noticed that streaming sound from some web sites was intermittent, sometimes they would play, sometimes not, even the same site!? Basically I'm confused about all these different sound selections I have. ALSA, OSS, ESD...it's so damn confusing.

Can anyone shed some light on all this? I know ALSA is new, OSS is old, and ESD is suppose to be a piece of junk, although it's the only one that gives me music. HELP!

---

### Post by king20878 on 2005-02-10
I can't say anything regarding your problem specifically, but after weeks/months of struggles getting sound working on my Thinkpad with a notoriously difficult sound chip, I installed Polypaudio and immediately got fantastic sound in all applications (so far).  I also have multiple sounds at once, which has been a dream for me up till now.  It's a drop in replacement for ESD, so I would try installing it and setting your applications to output to ESD.  You may have to launch it from a prompt by typing "polypaudio -D" 

I've only been using it for a day now, so I'm hardly an expert, but it's one more avenue to try.

---

### Post by ubuntu_fan on 2005-02-10
[QUOTE=sharkzf6]My ubuntu/Linux journey has been one of much frustration with an occasional success thrown in from time to time. I thought getting the nVidia 66.29 drivers installed was a challenge until I figured out what the packages in synaptic were, then it was a snap. My real issue with ubuntu so far is with sound/multimedia.

I started out with an old SB live sound card, which, of course, works perfectly. After getting everything else working, I decided I was getting good at this and thought I'd try my hand at getting the Audigy LS working which is what I use in WinXP (it sounds awesome compared to the old SB live). To make a long story short, I've gone from thinking I didn't have Audigy LS/ALSA support (ALSA version 1.0.6), to thinking it should actually be in there (ALSA was upgraded to 1.0.8 during a synaptic session), to knowing it's actually in there (according to ALSA's web site the Audigy LS driver is built-in to versions 1.0.6a and higher), though it still didn't work!? I ultimately gave up on the Audigy and tried the integrated sound on my motherboard (ALC655 – aka AC97). Upon booting up after the switch, I had sound at the GDM login screen – hallelujah! Gnome booted up and all sounds were enabled – I thought I was in good shape until I tried to play a music CD. It loaded but wouldn't “play”. Then I tried Doom 3 which worked perfectly with the SB live. The Doom 3 server reported that the sound device was busy...no sounds during game play. After scouring the internet I came across a post where a guy pointed out he had a similar problem and switched the Multimedia System Selector from ASLA to ESD which gave him sound. I did the same and could play music CDs but still no sound in Doom 3. Also, I noticed that streaming sound from some web sites was intermittent, sometimes they would play, sometimes not, even the same site!? Basically I'm confused about all these different sound selections I have. ALSA, OSS, ESD...it's so damn confusing.

Can anyone shed some light on all this? I know ALSA is new, OSS is old, and ESD is suppose to be a piece of junk, although it's the only one that gives me music. HELP![/QUOTE]
 I had the same problem with getting ALSA to work with my Audigy.

The problem was one of the digital channels needs muting. I can't remember which one it was, but I'll Google it and see if I can't remember.

Don't depair! Hang in there!

a.

---

### Post by ubuntu_fan on 2005-02-10
[QUOTE=ubuntu_fan]I had the same problem with getting ALSA to work with my Audigy.

The problem was one of the digital channels needs muting. I can't remember which one it was, but I'll Google it and see if I can't remember.

Don't depair! Hang in there!

a.[/QUOTE]

I don't have my system handy, but I think it was the IEC958 output that I muted in the mixer.

This should work for the ALSA/Audigy combo.

HTH,

a.

---

### Post by sharkzf6 on 2005-02-10
[QUOTE=ubuntu_fan]I don't have my system handy, but I think it was the IEC958 output that I muted in the mixer.

This should work for the ALSA/Audigy combo.

HTH,

a.[/QUOTE]
I really appreciate your response. Thing is, I know that's not what's wrong. In all my research, the one thing I'm sure of is, the card (Audigy LS) is not being detected properly because it's not listed anywhere other than the Device Manager in Gnome. The other 2 cards will always have devices and config files in the proper places along with the listing in Device Manager. As it stands right now, I've got my on-board sound enabled and the Audigy removed. It works OK with ESD but still no game sounds. I believe the reason for this is, both games I have installed on this drive (Quake 2 and DooM 3) require the OSS sound to be selected. Problem with this is, that borks the system. Here's a simple run down of the various configurations I've tried and the end result:

**SB live** -  *ALSA, OSS, & ESD: everything works except media player. It won't play anything but OGG format. It says the gstreamer plugins may be missing, however, I know they are installed. I believe this is a Totem issue.*

**On-Board Realtek ALC655 (aka AC97)** - *ALSA: nothing works. OSS: system sounds work, music CDs play but the CD won't eject (not even manually), games do not work, media player only plays OGG format. System sounds must be disabled in order to use other media devices. ESD: system sounds work, music CDs play and eject properly, media player only plays OGG format. Can have system sounds enabled and still use other media devices like CD player. Games do not work.*

**Audigy LS** - *ALSA: nothing works. OSS: nothing works. ESD: nothing works.*

This is almost enough to drive me back to Winblows where the multimedia always works flawlessly no matter which sound device I use, though the Audigy is clearly the best when it comes to sound quality. I don't blame Linux/ubuntu. I realize the problem is all this hardware that's being made for PCs is geared towards Windows. It's the situation we all face with the intent of putting an end to. I will probably just find out what card is best for Linux and just buy one (example – Turtle Beach 24 bit). I'm not giving up yet, however, it's frustrating trying to get something to work in Linux that is so easy to configure and use in Windows. Thanks again.

---

### Post by sharkzf6 on 2005-02-10
[QUOTE=king20878]I can't say anything regarding your problem specifically, but after weeks/months of struggles getting sound working on my Thinkpad with a notoriously difficult sound chip, I installed Polypaudio and immediately got fantastic sound in all applications (so far).  I also have multiple sounds at once, which has been a dream for me up till now.  It's a drop in replacement for ESD, so I would try installing it and setting your applications to output to ESD.  You may have to launch it from a prompt by typing "polypaudio -D" 

I've only been using it for a day now, so I'm hardly an expert, but it's one more avenue to try.[/QUOTE]
Thanks for heads up...I'll give that a try...

---

### Post by sharkzf6 on 2005-02-11
[QUOTE=king20878]I can't say anything regarding your problem specifically, but after weeks/months of struggles getting sound working on my Thinkpad with a notoriously difficult sound chip, I installed Polypaudio and immediately got fantastic sound in all applications (so far).  I also have multiple sounds at once, which has been a dream for me up till now.  It's a drop in replacement for ESD, so I would try installing it and setting your applications to output to ESD.  You may have to launch it from a prompt by typing "polypaudio -D" 

I've only been using it for a day now, so I'm hardly an expert, but it's one more avenue to try.[/QUOTE]
Argh!!!!!! I downloaded polypaudio and got the following message when I tried running ./configure from the directory:

[b]checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.[/b]

Last time I tried using the *configure* command attempting to install a different program I got the same message. GCC is installed - I don't get it. Can you help?
Thanks.

---

### Post by king20878 on 2005-02-11
I apt-get'ed polypaudio from the repositories.  It's in universe.  Installed polypaudio-alsa, -clients, and -x11 as well.

---

### Post by sharkzf6 on 2005-02-11
[QUOTE=king20878]I apt-get'ed polypaudio from the repositories.  It's in universe.  Installed polypaudio-alsa, -clients, and -x11 as well.[/QUOTE]
yeah, I just realized I don't have the universal URL in my repository, guess I need to add it and install poly that way...thanks again.

---

### Post by fenix03 on 2005-02-11
I also had a difficult time to get my Creative Audigy 2 ZS to work with alsa but that was primarily because it's difficult to find any good documentation.

Try the link below and see if you can get it working.

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+LS.&chip=SB0310%2C+P17&module=audigyls](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+LS.&chip=SB0310%2C+P17&module=audigyls)

You don't need to compile and stuff just start from 'Setting up modprobe and kmod support'

Or try this first:

Install 'alsa-utils' and 'alsa-oss', then use alsamixer and unmute everything, raise every bar until you hear sound.

---

### Post by sharkzf6 on 2005-02-11
[QUOTE=fenix03]I also had a difficult time to get my Creative Audigy 2 ZS to work with alsa but that was primarily because it's difficult to find any good documentation.

Try the link below and see if you can get it working.

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+LS.&chip=SB0310%2C+P17&module=audigyls](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+LS.&chip=SB0310%2C+P17&module=audigyls)

You don't need to compile and stuff just start from 'Setting up modprobe and kmod support'

Or try this first:

Install 'alsa-utils' and 'alsa-oss', then use alsamixer and unmute everything, raise every bar until you hear sound.[/QUOTE]
Yeah, I have ALSA 1.0.8 which has the Audigy LS support built-in. You may have something there...I don't know, I read through that link before, I'll take another look. Sad thing is, even if I get the Audigy working, since it's the cheapo version I still won't have the multi-device support...I may just get a new card that's 24 bit and has hardware mixing. Thanks.

---

### Post by CookieNinja on 2005-03-11
[QUOTE=sharkzf6]Yeah, I have ALSA 1.0.8 which has the Audigy LS support built-in. You may have something there...I don't know, I read through that link before, I'll take another look. Sad thing is, even if I get the Audigy working, since it's the cheapo version I still won't have the multi-device support...I may just get a new card that's 24 bit and has hardware mixing. Thanks.[/QUOTE]
 Does the OS know about the soundcard? If you're not sure, do the following below.

In shell, type lsmod and make sure the kernel modules required have been loaded. If not, try to insert them manually with modprobe. <kernel-module>. If they cannot be added mannually read the following to make sure everything has been done correctly.

First of all .. Make sure ALSA is compiled with the same version of gcc that was used to compile the kernel.

Next look up the link below and make sure the compiling instructions up to, but not beyond, step 4 have all been followed when compiling ALSA:

[http://fedoraforum.org/forum/showthread.php?p=202275#post202275](http://fedoraforum.org/forum/showthread.php?p=202275#post202275)

Once this has been done, restart the computer (some might say other ways, but I am keeping it as simple as possible) and then check again to see if the modules have been loaded. If not, again try adding them manually and seeing if that works or not. If you've followed all the steps correctly then it *should* work just fine.

Load alsamixer via the shell, or a gui version of the sound controls, to check the volume controls, if the modules are all loaded but there's no sound.

If the modules have to be loaded manually every time, then something's not right, but at least they work.

Hope some or all of that helps :) I've just come through all this pain myself :( but I'm now confident enough to sort it all out. Thanks to that fedora guide I've got my audigy 2 value card working on fedora and ubuntu.

---

### Post by cmichaelboyd on 2005-09-14
I thought of this because you said you had onboard sound.  I don't have an audigy, but I had similar problems getting sound working.  I was able to get it working when I ran alsaconf *every* time I rebooted, which was such a pain.  Turned out, alsa was setting up my pci soundcard as sound-slot-0 and snd-card-0, which was confusing it when the system was rebooting because it was detecting my onboard sound and assuming that that was snd-card-0.  So i went into my bios and disabled onboard sound, rebooted, and it worked like magic.

Hope this helps!

---

