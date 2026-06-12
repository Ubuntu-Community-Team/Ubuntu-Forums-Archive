---
title: "Toshiba L30-134 sound problems"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by tenchi39 on 2006-12-03
Hi!

I've purchaced a Toshiba L30-134 laptop yesterday. It's for my mom (but I'd like to get one now too) and she would like to use skype with it. Sound plays ok through the internal speakers, but the headphones out and the microphone in jacks just do not work. I checked with gnome's sound mixer and also alsamixer:

Card: HDA ATI SB                                                                                          
Chip: Realtek ID 862                                                                                      

Master, Pcm and Capture are all 100%, none of them is muted. I also tried several headphones and microphones, so the problem is not there.

Some more data:

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)

Please help!

Thanx,

Tenchi

---

### Post by teitunge on 2006-12-03
I am sorry to say this, but I think you will have to buy a set of usb-headphones. I had the same problem earlier. You could also buy a usb-jack-converter.

---

### Post by manny0 on 2007-01-01
will a usb headphone work automaticly or will i run into troubles getting drivers and getting ubuntu to see this as well? this worries me. i have almost everything working on my toshiba L35 but sound via headphones just doesnt work for me.

---

### Post by maximk on 2007-04-25
In fiesty I had no sound at my L30-134 for about a week and at last solution was found.
First, I compiled and install fresh alsa-driver-1.0.14rc3.

Then, add following line to /etc/modprobe.d/options
options snd-hda-intel model=6stack-digout

Then reboot.

There will be many mixer settings, but actuall only "pcm", "front" (for speakers), "surround" (for phone jack) and "internal speaker" works. Fortunately, unused bars may be hidden.

May be ugly solution (actually, internal sound card does not have 6-channel sound and digital output), but for now it just works.

PS: I guess "model=6stack-digout" is supported by fiesty alsa, so it is reasonable to test it before upgrading to new version.

---

### Post by Stefan Björk on 2007-05-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108065](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108065) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				No, this ugly fix does not work with pre-compiled alsa support in Feisty. I have filed a bug report on this (#108065).

Stefan

---

### Post by Stefan Björk on 2007-05-10
Well, actually it does work. I needed to reboot the computer. A modprobe -r snd-hda-intel was just not sufficient. (However, sound seem not to work after hibernate/resume.)

---

### Post by peter07 on 2007-06-17
My toshiba l-30 works with snd-hda-intel model=6stack-digout. I had problems with headphone jack, but I found solution. It is simple, just run alsamixer, find "surround" channel, unmute (key 'M') it and increase volume until you clearly hear sound. 

Everything was good till last kernel update from ubuntu updates. Now headphones out don't work, and I don't have idea why :(

---

### Post by heristal on 2007-08-01
Hi Team,

The same problem was resolved in fedora 7 with the same computer using the file 

/etc/modprobe.d/options

The file does not exist, so just create it and add this line 

options snd-hda-intel model=6stack-digout

Thanks MAXIMK !!!
RDE

---

### Post by manny0 on 2007-08-02
sound works but its super low :( via headphone jack with headphones.

---

