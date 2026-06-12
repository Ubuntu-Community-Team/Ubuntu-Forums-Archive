---
title: "IBM ThinkPad T23 Audio issues"
date: 2010-07-22
forum: Hardware
---

### Post by dmillerw on 2010-07-22
So I've installed Xubuntu 10.04 on an old ThinkPad for my sister, most things work, except sound.

Xubuntu recognizes that there is a sound device, but doesn't actually output anything, I've tried both the built in speakers and plugging in headphones, anyone have experience with this?

> #  Intel 82801CAM (ICH3) I/O and Audio controller
# Intel AC'97 Audio with a CS4299 codec

That's what the computer has in the way of hardware for audio.

Also, kind of related to this, the volume controls do not work, any idea as to why?

---

### Post by linuxdady on 2010-08-31
1. Remove pulse audio:

      sudo apt-get autoremove pulseaudio

2. Add this line to /etc/modprobe.d/alsa-base.conf
      
      options snd-hda-intel model=thinkpad

3. Reboot


4. Set visible controls in mixer

5. Enjoy!


Everything works for me, including Skype.

---

### Post by adimopoulos on 2011-05-13
Hi

I'm having the exact same problem here. Old IBM T23 series with xubuntu 10.b04.  The solution above didnt help. if anyone has a better idea....

Thanks 

Aris

---

