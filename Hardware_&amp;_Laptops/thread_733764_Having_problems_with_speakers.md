---
title: "Having problems with speakers"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by Quaxir on 2008-03-24
I'm using Asus F3JP laptop, and having Windows XP + Linux Ubuntu 8.04 as dualboot on my computer. After installing Ubuntu, I noticed even I plug in my headphones, speakers in computer, those built-in speakers can't be muted, or then my headphones will be muted aswell. So I would want to know how to mute laptop's built-in speakers without muting plugged in headphones :).

I'm pretty new with Linux and these things, so I don't actually have a clue what I could do to solve the problem.

---

### Post by erginemr on 2008-03-24
Ubuntu 8.04 Hardy is at Beta stage and there can still be bugs related to sound in Hardy.

What I suggest for you is to download Ubuntu Gutsy Gibbon (7.10) Live CD, boot your computer with it and check it there still is a problem with headphones in the Live CD. 

Unfortunately, I have seen many posts in the forums by laptop owners dealing with problems regarding headphones. So, even if you try Gutsy (but you should still try it) your chances are not much.

---

### Post by lswest on 2008-03-24
Yeah, i had a similar problem in Gutsy.  When i plugged my headphones in it wouldn't mute my integrated speakers, or play music through the headphones.  Supposedly it's really hard to get it working right using ALSA, but pulseaudio (the Hardy Beta uses it) works for me.  Chances are Gutsy won't be able to do what you want it to do, but if you wait 31-32 days (until Hardy gets released) there's a good chance it will work then.

---

### Post by Quaxir on 2008-03-24
Damn, I mean I got 7.10, Gutsy Gibbons atm. Not that new beta version. (maybe I typed 8.04 because my friend installed that beta version few days ago, so). But I have gutsy gibbons, and that problem was aswell in Feisty (or what was previous version before Gutsy Gibbons).

---

### Post by erginemr on 2008-03-24
If so, then please post the outcome of the following commands from the terminal:
```
aplay -l
```
```
cat /proc/asound/cards
```
```
lspci | grep -i audio
```
to help us identify your sound card.

---

### Post by Quaxir on 2008-03-25
logima@logima-laptop:~$ aplay -l
**** Luettelo PLAYBACK laitteista ****
kortti 0: Intel [HDA Intel], laite 0: ALC861VD Analog [ALC861VD Analog]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 0: Intel [HDA Intel], laite 6: Si3054 Modem [Si3054 Modem]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0

logima@logima-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 16

logima@logima-laptop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


And is it problem for you my language is set to Finnish (just some of those words are as Finnish). And, yesterday I even updated Linux to its new beta version, 8.10 Hardy, not sure was it really wise, but what's done it's done :/.

---

### Post by erginemr on 2008-03-25
> **Quaxir said:**
> ...
And is it problem for you my language is set to Finnish (just some of those words are as Finnish). And, yesterday I even updated Linux to its new beta version, 8.10 Hardy, not sure was it really wise, but what's done it's done :/.

I will try to help you regarding the sound issue, but regarding the language, what is your native tongue, or do your prefer having the system in English?

---

### Post by erginemr on 2008-03-25
Regarding the sound issue, I suggest to to refer to this howto:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

From there, find the lines:
```
ALC861/660
3stack 3-jack
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack with SPDIF I/O
3stack-660 3-jack (for ALC660)
uniwill-m31 Uniwill M31 laptop
toshiba Toshiba laptop support
asus Asus laptop support
[color=red]**asus-laptop ASUS F2/F3 laptops**[/color]
auto auto-config reading BIOS (default)
```

and edit the file /etc/modprobe.d/alsa-base by issuing the following command from the terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base
```

finally append the line:
```
options snd-hda-intel model=**asus-laptop**
```
save the file, exit and reboot to check if the headphones problem has been taken care of.

If not, replace "asus-laptop", with first "asus" and then with "auto".

That howto is full of success stories, I hope it will work for you too.

---

### Post by Quaxir on 2008-03-25
Should I already have

```
ALC861/660
3stack 3-jack
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack with SPDIF I/O
3stack-660 3-jack (for ALC660)
uniwill-m31 Uniwill M31 laptop
toshiba Toshiba laptop support
asus Asus laptop support
asus-laptop ASUS F2/F3 laptops
auto auto-config reading BIOS (default)
```

those lines allready in

```
/etc/modprobe.d/alsa-base
``` ?

And, my mother tongue is Finnish.

---

### Post by erginemr on 2008-03-25
No, you should just add the followng line:
options snd-hda-intel model=asus-laptop

---

### Post by erginemr on 2008-03-25
The language part is easy. 

All you need to do is pay a visit to "Main Menu -> System -> Administration -> Language Support" and then check the Finnish language from the list. Then, the system will download some 14 packages. When it is done, you should select Finnish from the "Default Language" combo box below.

Now reboot, and select Finnish language again at the gdm login screen. It may require a few reboots / logins for all language settings to settle, but you will end up in an Ubuntu system in your own language.

---

### Post by Quaxir on 2008-03-25
Thank you about that language set up, now it works. But I still got that speaker problem, even I added line: "options snd-hda-intel model=asus-laptop" and tested with "options snd-hda-intel model=asus-auto" aswell, but still hearing voice from both, headphones and built-in speakers :(.

---

### Post by erginemr on 2008-03-25
Then, I suggest you to update your ALSA driver to the latest version, 1.0.16. Please have a look at:
[http://ubuntuforums.org/showthread.php?t=616845&page=5](http://ubuntuforums.org/showthread.php?t=616845&page=5)

and use Temujin's scripts. Let us see if it helps (I hope).

---

### Post by erginemr on 2008-03-25
> **Quaxir said:**
> Thank you about that language set up, now it works. But I still got that speaker problem, even I added line: "options snd-hda-intel model=asus-laptop" and tested with "options snd-hda-intel model=asus-auto" aswell, but still hearing voice from both, headphones and built-in speakers :(.

It should be either:
**options snd-hda-intel model=asus**
or
**options snd-hda-intel model=auto**

Can you please try them as well, in the hope that one of them might work?

---

### Post by Quaxir on 2008-03-25
Even I included those lines, it didn't take effect :/.

Just if I've done something wrong, I link here some stuff..

```
/etc/modprobe.d/alsa-base
``` (place where edited file is)

and

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-hda-intel model=auto
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

Text what that file includes after I added that line, is line in right place, or should it be added to somewhere else. (I tested it with "options snd-hda-intel model=auto" and with "options snd-hda-intel model=asus", but not working.)

---

### Post by erginemr on 2008-03-25
No friend, you did it correctly. Unfortunately, this trick doesn't work in your case. 

In this case, I can only suggest you to upgrade your ALSA driver to 1.0.16 by using those two scripts (Hardy has 1.0.15).

---

### Post by erginemr on 2008-03-25
> **lswest said:**
> Yeah, i had a similar problem in Gutsy.  When i plugged my headphones in it wouldn't mute my integrated speakers, or play music through the headphones.  Supposedly it's really hard to get it working right using ALSA, but pulseaudio (the Hardy Beta uses it) works for me.  Chances are Gutsy won't be able to do what you want it to do, but if you wait 31-32 days (until Hardy gets released) there's a good chance it will work then.

I don't know what **pulseaudio **is good for, but I remember from the Hardy Heron Beta Live CD that there was an option to select the default sound system (one as regular ALSA, the other as pulseaudio) in;

* either by double clicking Gnome volume level icon and selecting preferences from the menu, 
* or by System -> Preferences -> Multimedia Systems Selector, 
* or still, by System -> Preferences -> Sound.

Now that you have upgraded to Hardy in an effort to fix this problem, this **pulseaudio **may be the answer for you.

---

### Post by Quaxir on 2008-03-25
Hmm, seems I allready got that pulseaudio. What should I do with that software :D?

---

### Post by erginemr on 2008-03-25
Here is a similar thread on the same sound chip:
[http://ubuntuforums.org/showthread.php?p=4222234](http://ubuntuforums.org/showthread.php?p=4222234)

Apparently, updating ALSA didn't solve the problem where sound comes both from headphones and speakers. 

A faint hope but still... Do you happen to have a headphones volume bar when you open **alsamixer** (text-mode ALSA volume monitor) from a terminal window?

---

### Post by erginemr on 2008-03-25
> **Quaxir said:**
> Hmm, seems I allready got that pulseaudio. What should I do with that software :D?

Ha ha... Not so fast. ;) You should try to select it as the default sound output device from the several locations I have already mentioned.

I am also calling **lswest** to duty, has s/he apparently knows better on pulseaudio than me...

[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

---

### Post by Quaxir on 2008-03-25
I've tried to put it as default sound output, but nothing happens. Should I reboot after doing that or something?

---

### Post by erginemr on 2008-03-25
> **Quaxir said:**
> I've tried to put it as default sound output, but nothing happens. Should I reboot after doing that or something?

Go ahead. But if it doesn't help, I advise you to update your ALSA driver...

---

### Post by Quaxir on 2008-03-25
> **erginemr said:**
> 
A faint hope but still... Do you happen to have a headphones volume bar when you open **alsamixer** (text-mode ALSA volume monitor) from a terminal window?

Yes, I have selection for that, but I can't activate or deactivate it :/

And about updating ALSA drivers, I allready have that, or at least I think so

```
logima@logima-laptop:~$ sudo apt-get upgrade alsa/alsa-driver-1.0.16
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatietoja... Valmis       
0 päivitetty, 0 uutta asennusta, 0 poistettavaa ja 0 päivittämätöntä.
logima@logima-laptop:~$ 

```

"0 päivitetty, 0 uutta asennusta, 0 poistettavaa ja 0 päivittämätöntä." means nothing has been changed with that command.

---

### Post by erginemr on 2008-03-25
> sudo apt-get upgrade alsa/alsa-driver-1.0.16

It doesn't work that way. You should follow this one instead:
[http://ubuntuforums.org/showpost.php?p=4450631&postcount=5](http://ubuntuforums.org/showpost.php?p=4450631&postcount=5)

---

### Post by Quaxir on 2008-03-27
I have updated my Alsamixer to 1.0.16 version, booted computer and having that

```
options snd-hda-intel model=auto
```

in my

```
/etc/modprobe.d/alsa-base
```

but still nothing happens to my voice, still hearing it from both :(

---

### Post by erginemr on 2008-03-27
I am sorry. I have also searched both Ubuntu Forums and the Linux related sites in general, and have concluded to my disappointent that there is no tried and tested solution to this problem. Some people have signed in bug reports for this problem, but none of them has come to any resolution so far. I hoped that an update may have solved the issue, well, alas...

Yet my previous comment below still applies:
*A faint hope but still... Do you happen to have a headphones volume bar when you open alsamixer (text-mode ALSA volume monitor) from a terminal window?*

You can check your alsa version with:
```
alsactl -v
```

:(

---

### Post by Quaxir on 2008-03-28
Yepyep, well you tried your best to help me, thank you about your help, this time problem could not soluted, maybe problem is just in my computer's hardware, not with software.

---

### Post by kayel_justice on 2008-03-30
This may help.
I found this thread somewhere I forgot where, but the guy said that if you have problems with your external speakers(sub woofer, monitors) and such, that you should follow these instructions if you installed ubuntu 7.10 correctly.

1) Go to the upper right hand corner or where your volume is for you and mute it. Right click (over icon) -> mute.

2) Right click(over icon) -> open volume control........... and turn pcm way up.

3) If you still can't hear anything.......Right click(over icon) -> open volume control, and click the tab "switches", check to see if headphones is checked.


That's it. Worked for me

---

### Post by cdtech on 2008-03-30
What is your Subsystem Id?
On the command line type:
```
cat /proc/asound/card0/codec#0
```

---

### Post by erginemr on 2008-03-31
**Quaxir**, I have found something which may interest you:

Following this link again:
[http://ubuntuforums.org/showthread.php?p=3796486](http://ubuntuforums.org/showthread.php?p=3796486)

The following two people, who have posted in that thread, could solve their headphones problem by inserting:
**options snd-hda-intel model=6stack-dig** to **/etc/modprobe.d/alsa-base**

and by manually enabling / disabling headpnones switch from Gnome volume applet:
[http://ubuntuforums.org/showpost.php?p=4474212&postcount=34](http://ubuntuforums.org/showpost.php?p=4474212&postcount=34)
[http://ubuntuforums.org/showpost.php?p=4184991&postcount=18](http://ubuntuforums.org/showpost.php?p=4184991&postcount=18)

For you to try...

---

### Post by erginemr on 2008-03-31
Another success story with the same trick:
[http://ubuntuforums.org/showpost.php?p=4623048&postcount=900](http://ubuntuforums.org/showpost.php?p=4623048&postcount=900)

---

### Post by Quaxir on 2008-04-01
Well, even I added that ```
options snd-hda-intel model=6stack-dig
``` line to ```
 /etc/modprobe.d/alsa-base
``` nothing happened. And, if I switch main volume from master to 0% and headphones to full, I can hear little sound, but not enough at all what I would need. I hardly can hear that voice --> not good :/.

---

