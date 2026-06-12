---
title: "headphones stopped working"
date: 2011-03-16
forum: Hardware
---

### Post by subverted on 2011-03-16
Hi, I installed Ubuntu Maverick on my Toshiba Satellite. Originally it worked perfectly, but I wanted to remove GDM and start in TTY console mode and enter X11 via "startx". This broke my system, though it always worked on Debian. I am generally a stable Debian user on Desktop, but Ubuntu works better with WIFI and ethernet work better in Ubuntu on a laptop. 

Anyway, originally the headphones worked and I watched youtube with them. Then I broke the system by removing "GDM" from /etc/X11/default-display-manager (dont try this in Ubuntu! It works in Debian though.). Anyway. so my system quit working, and I installed Slackware. I found Slackware could not deal with headphones. The sound came out of both headphones and normal speakers. There were other issues with Slackware on Toshiba laptop, so I reinstalled Ubuntu. behold, now the headphones no longer output any sound, whereas previously with the same Maverick release it worked fine. 

I have tried many things and it is a pure mystery. I am considering upgrading Alsa driver but damn that is a big deal sort of and since the headphones worked before with the same distro, I think Slackware must have done something to me BIOS and turned off the headphones, but normal speakers still work. 

(BTW, my BIOS are a crappy kind called InsydeH20, which have no audio controls in them!)

Thanks for any help on this strange mystery! LSPCI in the terminal shows this:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

I think ICH9 family is a rather new type.

Advanced Linux Sound Architecture Driver Version 1.0.23.

Upgrade alsa to .24? That might have no effect whatsoever, but then have to install build-essential and all that, and that only problem is no sound from headphones. Otherwise Ubuntu runs perfectly on the Toshiba Satellite C650 Series, brand new.

---

### Post by subverted on 2011-03-17
Okay I fixed it. Found some new information. Apparently the chipset is more important than sound card info. So from the gnome-alsamixer so alsamixer which tells the chipset "Conexant CX20585" for me.  This led me to the right fix here: [http://doc.ubuntu-fr.org/audio_intel_hda#acer](http://doc.ubuntu-fr.org/audio_intel_hda#acer) as described here: [http://ubuntuforums.org/showthread.php?t=1624557&highlight=headphones+work](http://ubuntuforums.org/showthread.php?t=1624557&highlight=headphones+work). I tried this before but was using the card information rather than chipset. This crap about Intel Corporation 82801I (ICH9 Family) isnt useful. 

This worked: "options snd-hda-intel model=thinkpad", but I dont have a Thinkpad! But Thinkpad uses conexant chipset. So I have gathered this is a chipset issue.

---

