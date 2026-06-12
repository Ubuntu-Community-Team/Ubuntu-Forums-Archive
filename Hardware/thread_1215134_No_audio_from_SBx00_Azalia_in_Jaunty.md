---
title: "No audio from SBx00 Azalia in Jaunty"
date: 2009-07-16
forum: Hardware
---

### Post by darkdeity311 on 2009-07-16
I'm starting my transition to Ubuntu on my HP Pavilion dv5-1250us, and liking it quite nicely. Pretty much everything worked out of the box, except for standby/hibernate and the audio. I'm not concerned about the standby/hibernate because its a laptop, and i don't expect perfection. The audio on the other hand, its almost a necesity for me. Messing with PulseAudio a little, I found the headphone jacks were muted, so I unmuted that and they work. The main speakers on the other hand, don't. The sound card that is built in is an ATI SBx00 Azalia, which looks to be problematic with many other folks. No one seems to have a definitive answer on it though. If i boot Ubuntu 8.04 from CD, or PXEboot the laptop from an 8.04 LTSP server, audio works. I also installed Fedora 11 on the laptop, and audio works. 

So, what i've tried so far:
Umuted all options i can find in volume control.
         [SIZE=5]"[/SIZE]sudo gedit /etc/modprobe.d[INDENT]sudo gedit /etc/modprobe.d/alsa-base
 I added at the end of file this line:
options snd-hda-intel model=laptop
 next
sudo gedit /boot/grub/menu.lst
 I added this options
iommu=off noirqdebug[SIZE=5]"[/SIZE]
[/INDENT]Updated ALSA and PulseAudio.
Installed PulseAudio Device Chooser, and changed each device's settings around to different websites' suggestions.




As of now, it looks like ALSA is what is getting my headphone jacks to work, but I dont know how to get the main speakers to work. 


I dont know what terminal outputs you would need, but heres a lspci | grep Audio output


00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]



I appologize if this was lengthy or if there is another post similar, if so, let me know.


Thank you!

[INDENT]

[/INDENT]

---

### Post by darkdeity311 on 2009-07-17
After I posted this, I changed my search criteria to be more specific with my laptop, and I found this:
[http://ubuntuforums.org/showthread.php?t=1073090&highlight=SBx00](http://ubuntuforums.org/showthread.php?t=1073090&highlight=SBx00)
Any one who is have the same trouble as I am, this should fix it!

---

