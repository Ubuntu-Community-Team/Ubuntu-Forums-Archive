---
title: "Compaq presario CQ35"
date: 2009-11-12
forum: Hardware
---

### Post by ravindasenarath on 2009-11-12
i have a Compaq presario CQ35 laptop and i have ubuntu 9.10 installed in it. there are no sounds. the player displays sound playing but no sounds come out. i upgrade alsa to the latest version but it was not solved. any one can suggest some solution for this.

ravinda

---

### Post by acrobaticman on 2009-12-19
First u need to Edit /etc/modprobe.d/alsa-base.conf
type this line in to the terminal
   [LEFT]>>     sudo gedit /etc/modprobe.d/alsa-base.conf

[/LEFT]
then add these 2 lines to the end of the file

>>     options snd-hda-intel model=hp-m4 enable=1 index=0
>>     options snd-hda-intel enable_msi=1


restart and smile brother ^^


Hope it will help you

---

### Post by ducmtv on 2010-01-15
thanks! it's very good ^^

---

### Post by ali.i.s on 2010-02-14
> **acrobaticman said:**
> First u need to Edit /etc/modprobe.d/alsa-base.conf
type this line in to the terminal
   [LEFT]>>     sudo gedit /etc/modprobe.d/alsa-base.conf

[/LEFT]
then add these 2 lines to the end of the file

>>     options snd-hda-intel model=hp-m4 enable=1 index=0
>>     options snd-hda-intel enable_msi=1


restart and smile brother ^^


Hope it will help you

Dear [acrobaticman]("http://ubuntuforums.org/member.php?u=887931"),

I tried the first command line and I got this;
(gedit:4242): Gtk-WARNING **: Theme directory 64x64apps of theme kdeclassic has no size field
 I went on and added the 2 lines and restarted as you instructed but it didn't work not to mention I have ubuntu 9.04 set on a Persario CQ35-243tx   thanks in advance for any suggestion.

---

### Post by crsroque on 2010-08-17
Hi,

What will i do for my "WIFI" to work on presario cq35?

Hoping to hear from anyone's reply soon.

Thanks and Best Regards,
Ruther

---

