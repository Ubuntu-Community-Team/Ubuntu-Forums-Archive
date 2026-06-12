---
title: "Toshiba A60 AC'97 Sound Problem"
date: 2005-05-26
forum: Hardware &amp; Laptops
---

### Post by sebgate20 on 2005-05-26
Hi All

I've got a Toshiba Equium A60-155 Laptop (2.8GHz Celeron D, 256mb RAM, 40gb HDD) which has been running Ubuntu Hoary since Array-4 without many problems. However, the problems is that Sound does not work past the Ubuntu Splash screen. As soon as the GDM appears, a drum sound is made and then the startup sound is played but after that, it doesn't work.

It has an ATI-XP AC'97 Sound Chip. I got sound to work with SUSE 9.3 but not Fedora Core 3 or 4 Test 3. I saw something about this a while ago but I can't remember what it is. I'm willing to try anything! I would really like to play DVDs on this laptop and they ain't much fun without sound.

Thanks

Seb

---

### Post by tread on 2005-05-26
If you can hear a sound, that means the drivers are good. Rhythmbox uses esd (as far as I know) so you need to make sure esd is running ..

Try a simple test .. start a console and type in esd. You should hear a sound there .. 
Then start rhythmbox and try to play some songs ..

---

### Post by ::DoGG:: on 2005-05-26
You are using alsa or oss ?

---

### Post by der_kaiser on 2005-05-26
I also have a Toshiba A60, and I had the same problem with the sound.
You have to follow the instructions on this page : [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

And after add these lines to these files :

/etc/hotplug/blacklist : 
snd-atiixp-modem
snd-atiixp

/etc/modules : 
snd-atiixp

You also have to type "chmod 777 /dev/dsp"

Good luck!

---

