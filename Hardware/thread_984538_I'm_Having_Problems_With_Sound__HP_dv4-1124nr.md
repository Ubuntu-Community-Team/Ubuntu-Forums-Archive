---
title: "I'm Having Problems With Sound?  HP dv4-1124nr"
date: 2008-11-16
forum: Hardware
---

### Post by LinuxLuver29 on 2008-11-16
Hey all!
I just got my laptop today and the first thing I have done was get rid of Vista and install Ubuntu.

It's working great but the first noticeable thing was that the startup sounds and all the other sounds are stuttering/echoing.

Can anyone please help?
Thank you so much!

---

### Post by LinuxLuver29 on 2008-11-16
Can anybody help?

---

### Post by Jorge_C on 2008-11-16
This should solve your dv4 sound problems:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
and add this to the end of the file:
```
options snd-hda-intel enable_msi=1
```
Hope this works for you

---

### Post by russ2001 on 2008-12-07
this worked for my dv-1147cl.
thanks

---

### Post by Jim Olivi on 2009-01-06
I had a lot of trouble with an HP Pavilion dv4.  This fix worked right away!  It did require a reboot.

Thanks

---

### Post by popkid on 2009-01-09
also working for me on a dv4-1000ea thanks!

---

### Post by ameseisch on 2009-01-24
this also worked for my dv4 1114nr  -- thanks!

---

### Post by concerto on 2009-01-28
This DID NOT work for me.  I still need help!

I have a HP Pavilion DV4-1155SE

---

### Post by concerto on 2009-01-28
Actually I need help from you guys with HP DV4 computers.

When you type   "gksudo gedit /etc/modprobe.d/alsa-base"

Can someone print that out here so I can see the out put?

Please and thank you for all your help everyone.

---

### Post by rp1226 on 2009-01-31
I have a dv4 1155se and I haven't gotten the sound working.  Here is my output.

> 
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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
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
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel enable_msi=1


As you can see I have add the last line that you had requested to see if it work and that is a no go for me.  Please let me know if there is any way to make this work.

---

### Post by darcy.nogueira on 2009-02-27
This also works for HP dv4 1150.

---

### Post by jayhaze on 2009-03-03
Finally!!! I'vce been looking for this! GREAT!!!! Now my only other issue with my HP DV4 and ubuntu is slow internet speeds. I've already disable ipv6  (is on by default) that deffinitly increased my speed... downloading a large segmented .rar file with a gui usenet newsreader from astraweb news-server: on vista with newsleecher average speed 700.00 kbps; In Ubuntu with pan before disabling ipv6 average 95.00 kbps, after disabling ipv6 average 140.00 kb/ps
 
How can I get the same performance from wifi in Ubuntu Linux as I get in Vista? Please help with any ideas. I apoligize if this is the wrong thread.

system: Hp pavilion dv4 1120us intel core 2 duo dual core 64bit 3gigs ram, broadcom wifi

I realize this thread was started for the sound problem, but i have been having such a hard time searching the depths of the net for info regarding the HP DV4 specifically and it seems like this may be where that is... does anyone know another resource for help with the HP DV4 and various linux distributions? I'm sure it's obvious I'm a newb, But I'm really interested. and motivated to learn... so, thanks for any info.

---

### Post by markbuntu on 2009-03-03
Thanks everybody. I am adding these to the database

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

If you have some more, please post there to let me know.
Once again, thanks

mark

---

### Post by NaplesBill on 2009-03-04
Well, I just replied to another thread but thought I'd add this here since a few of you have the DV4-1155SE like I do:

I have an HP DV4-1155SE. I was able to get the sound working with the following alsa-base config:

> 
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1

I also had to set the default mixer track device by selecting PCM. I had to do the same thing for the sound icon on the taskbar.

---

### Post by maicol515 on 2009-03-06
Hey.

thank you very much. this worked fine for me. 
i have a dv4 1129la.

it required a reboot. but im listening to Depeche Mode right now.

thanks

---

### Post by dep01 on 2009-03-08
> **Jorge_C said:**
> This should solve your dv4 sound problems:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
and add this to the end of the file:
```
options snd-hda-intel enable_msi=1
```
Hope this works for you


Ah, i have a hp pavilion 1275mx and am still having the same problem.  i can hear audio through my headphones but not my internal speakers.

I tried this thread too, but didn't work for me as I got an error during the package config:

[http://ubuntuforums.org/showthread.php?p=6860840&posted=1#post6860840](http://ubuntuforums.org/showthread.php?p=6860840&posted=1#post6860840)

UPDATE: the following reply fixed my issue. thanks all!

---

### Post by dep01 on 2009-03-08
> **NaplesBill said:**
> Well, I just replied to another thread but thought I'd add this here since a few of you have the DV4-1155SE like I do:

I have an HP DV4-1155SE. I was able to get the sound working with the following alsa-base config:

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 

I also had to set the default mixer track device by selecting PCM. I had to do the same thing for the sound icon on the taskbar.

This worked for me on my 1275mx! thanks!

---

### Post by Landscapeman on 2009-03-11
Thanks, Works Perfectly

---

### Post by xMoDx on 2009-03-20
> **Jorge_C said:**
> This should solve your dv4 sound problems:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
and add this to the end of the file:
```
options snd-hda-intel enable_msi=1
```
Hope this works for you

this does not work with my Compaq Presario CQ40-340TU =( please help

---

### Post by gw7714 on 2009-03-20
I know I'm being a little but of a traitor here, but if you just can't seem to get things working, and need a working operating system, I just checked and I think that Windows 7 Beta is still able to be downloaded from Microsoft.

I tried it, and thought that it was Vista- but fixed in many ways (if that's possible), the fact that it is a bets didn't seem to make it that klunky or malfunctional

This is a just in case/last resort!

---

### Post by anthropop on 2009-03-20
I have an HP dv4-1222nr and none of the fixes on this thread worked.  I started a thread for the HP dv4-1222nr, but someone thought I should have just posted to this thread.  Anyway here is the HP dv4-1222nr thread:
[http://ubuntuforums.org/showthread.php?p=6931326](http://ubuntuforums.org/showthread.php?p=6931326)

- Windoze comes free with this laptop if we wanted that. No need to wait for another version of an antique OS.

> **gw7714 said:**
> I know I'm being a little but of a traitor here, but if you just can't seem to get things working, and need a working operating system, I just checked and I think that Windows 7 Beta is still able to be downloaded from Microsoft.

I tried it, and thought that it was Vista- but fixed in many ways (if that's possible), the fact that it is a bets didn't seem to make it that klunky or malfunctional

This is a just in case/last resort!

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

### Post by bosox on 2009-04-04
I'm contemplating purchasing this notebook at Staples tommorow. Are you guys (with the DV4 1222nr) experiencing any issues other than sound? It looks like from the other thread some DV4 (not 1222nr) user is experiencing low throughput with wifi. 

Any feedback is appreciated. Thanks!

>> Wrong Thread, Mod please delete. Thanks!

---

### Post by omeron on 2009-04-20
Thanks a lot. 
Solved mine as well
HP DV4-1030ej:popcorn:

---

### Post by robstat on 2009-04-20
Thanks very much sorted mine as well DV5-1111ea

---

### Post by thunderboltz on 2009-04-26
Thank you! This worked with HP dv4-1242tx on Debian as well!

---

### Post by joseinbaraj on 2009-04-27
> **Jorge_C said:**
> This should solve your dv4 sound problems:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
and add this to the end of the file:
```
options snd-hda-intel enable_msi=1
```
Hope this works for you


I get a blank file when i use "gksudo gedit /etc/modprobe.d/alsa-base"

can someone tell me how to proceed...

---

### Post by joseinbaraj on 2009-04-27
I get a blank file when i used "gksudo gedit /etc/modprobe.d/alsa-base"

can someone tell me how to proceed... 

Thanks in advance ...

---

### Post by benorner on 2009-04-27
the following worked (for the most part) on my Asus F6A-2:

options snd-hda-intel model=6stack
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1 

sound is still low on music or movie playback and no drums at start, but event sounds are loud and clear. I'll keep working on it.

---

### Post by Fughley on 2009-05-03
I just got my hands on a HP Dv6-1030 and am having the same problems with the sound, actually it is headphones and the speakers. 
ARRGGG everything else is so smooth with 9.04 I hate to give it up. 
I have tried the alsa base fix but to no avail. 
any word on Alsa comming up with a stable driver? 
Cheers

---

### Post by Jaypur on 2009-05-12
> **Jorge_C said:**
> This should solve your dv4 sound problems:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
and add this to the end of the file:
```
options snd-hda-intel enable_msi=1
```
Hope this works for you



worked here, thank you a lot....


hp pavilion dv4-1180br


thanks!!!!

---

### Post by RebateFX on 2009-05-14
> **Fughley said:**
> I just got my hands on a HP Dv6-1030 and am having the same problems with the sound, actually it is headphones and the speakers. 
ARRGGG everything else is so smooth with 9.04 I hate to give it up. 
I have tried the alsa base fix but to no avail. 
any word on Alsa comming up with a stable driver? 
Cheers

I got my sound working from this thread [http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

Model HP Pavillion DV6 1045

Still no sound from the headphones jack though lol

---

### Post by ncjones on 2009-06-05
This worked for my Pavilion dv4-1212TX (purchased in China).

---

### Post by Sardonism on 2009-06-12
> **joseinbaraj said:**
> I get a blank file when i used "gksudo gedit /etc/modprobe.d/alsa-base"

can someone tell me how to proceed... 

Thanks in advance ...

Go ahead and try "options snd-hda-intel enable_msi=1" anyways.  If something screws up then you can easily just erase the changes you made since it's only a sound configuration file.

---

### Post by satish0muktha on 2009-07-05
> **concerto said:**
> Actually I need help from you guys with HP DV4 computers.

When you type   "gksudo gedit /etc/modprobe.d/alsa-base"

Can someone print that out here so I can see the out put?

Please and thank you for all your help everyone.


Its "gksudo gedit /etc/modprobe.d/alsa-base.conf" for 9.04

---

### Post by satish0muktha on 2009-07-05
> **Sardonism said:**
> Go ahead and try "options snd-hda-intel enable_msi=1" anyways.  If something screws up then you can easily just erase the changes you made since it's only a sound configuration file.

Its "gksudo gedit /etc/modprobe.d/alsa-base.conf" for 9.04

---

### Post by ivanvajar on 2009-07-05
Folks!
> gksudo gedit /etc/modprobe.d/alsa-base.conf
not> gksudo gedit /etc/modprobe.d/alsa-base

---

### Post by Sardonism on 2009-07-05
> **satish0muktha said:**
> Its "gksudo gedit /etc/modprobe.d/alsa-base.conf" for 9.04

You didn't need to tell me that...

I'm pretty sure I know what I'm talking about.

---

### Post by jonbonjovi on 2009-07-06
Hi! I have an HP pavilion dv5-1112el and when I reboot/hibernate/suspend I hear a very noisy cracking sound from the speakers/headphones...anyone has the same problem? Solutions?

---

### Post by satish0muktha on 2009-07-06
> **Sardonism said:**
> You didn't need to tell me that...

I'm pretty sure I know what I'm talking about.

Alright dude..Just chill

---

### Post by kateshine on 2009-07-30
the above fix worked beautifully on my dv4 1444
thanks for the help:)

---

### Post by novistahere on 2009-08-23
Thank you very much! My laptop is DV4T-1000. I have been working on the sound issue for several days. The echoing electric sound not only affect the speakers, it also make the movie playing liking using a scratch DVD(of course there is no sound, but the pictures are also affected.)

Google several website and follow other instructions to restore the sound driver, add new plugins, etc... Nothing changes.

This TWO-LINE code solve the sound problem perfectly. Thank you again.

---

### Post by c5vetter on 2009-09-15
am newb to Ubuntu 9.0.4 - had a number of initial problems with getting printers setup; wireless, etc. but was able to work through them - but NO SOUND anywhere, such as in YouTube, etc. and is still kicking my ****!

okay, found this thread through a lot of digging - have basically tried everything I can think of, followed numerous guides to reload ALSA, etc. - have HP Pavalion 8280us, which is older machine - doesn't appear my sound card is recognized, etc. - so where do I start!?

BTW - when I click on shutdown, do get a beep, so know soundcard DOES WORK!

---

### Post by alyaba on 2009-09-15
thanks everybody this fixed my problem if your on 9.04 make sure you type .conf at the end of the command like someone already said.

---

### Post by Makesh on 2009-09-17
thanks.. it worked for me too..

---

### Post by Speedbump0 on 2010-02-25
ok, im not having issues with my sound, but i am having issues with my Internet... i just installed Ubuntu on my External today.

---

### Post by GreenMint on 2010-04-06
> **concerto said:**
> Actually I need help from you guys with HP DV4 computers.

When you type   "gksudo gedit /etc/modprobe.d/alsa-base"

Can someone print that out here so I can see the out put?

Please and thank you for all your help everyone.


Hi concerto,

You need type **gksudo gedit /etc/modprobe.d/alsa-base.conf** not gksudo gedit /etc/modprobe.d/alsa-base. 

TQ.

gm

---

### Post by GreenMint on 2010-04-06
You need type:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```


and put this at the end of file:

```
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5
```

:)

---

