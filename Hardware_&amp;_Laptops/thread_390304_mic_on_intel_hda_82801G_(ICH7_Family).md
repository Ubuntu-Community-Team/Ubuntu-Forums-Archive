---
title: "mic on intel hda 82801G (ICH7 Family)"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by eagletek on 2007-03-21
Hello everybody!

I have a notebook Fujitsu-Siemens Amilo si 1520.  
The audio device (lspci) is the following:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

My problem is the microphone. It does not work but sometimes I am able to make it work.
I noticed that opening the gnome volume control or alsamixer there is no bar for setting the mic or line in volume but in the capture tab there is just a general capture volume that does not make the mic plugged into the line in work.

Once I noticed that (I don't know how) in this tab there was also line in and mic bar so that I could make the microphone work, but after it dissapeared! and it is strange because I did not install anything different.

I started to look at the file /var/lib/alsa/asound.state but there was no
any reference to the mic and line in I saw the time it is was working. I found in internet another asound.state file with the bars I was looking, I tried to restore it
and it was working again!! 

After the reboot the mic was not working anymore and i noticed that the file asound.state was reverted to the original one.. do you know how??
I checked also with  sysv-rc-conf and noticed that alsautils are not loaded at boot time.. so how can be modified the file??
But what I don't understand is why the same command with the same file asound.state after some reboots is not working anymore! It looks very strange!! 

Right now I am not able to make it work in any way!! 

Do you have any Idea??

Thanks a lot,
byez, 
eagletek

---

### Post by mikewhatever on 2007-03-22
[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

---

### Post by treesurf on 2007-03-23
Eagletek,  I am running the latest ALSA with Intel ICH7 Sigmatel Stac 92xx and am having the same problem as you.  If you find a solution please be sure to post it.  Thanks.

---

### Post by eagletek on 2007-03-23
Hi treesurf,

looking the link in the previous post, I just

add the following line to the file /etc/modprobe.d/alsa-base:

options snd-hda-intel model=3stack

and after reboot it was working! 

byez,

eagletek

---

### Post by Ender Black on 2007-03-23
I have the exact same sound card as the OP on a HP Pavillion dv9000 and following the link and compiling the new alsa program worked like a charm!  Thanks a bunch!

---

