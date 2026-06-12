---
title: "ubuntu newbie needs help with laptop audio jack"
date: 2009-04-14
forum: Hardware
---

### Post by sgtstukov on 2009-04-14
hi, I recently installed ubuntu on my gateway m153xl laptop, and the audio out (headphone) jack will not output audio in ubuntu. it works if i start the computer with the plug in the jack, but stops if i remove the plug, and wont resume when it is plugged back in. if i dont start it with the plug in the headphone jack, i get no audio at all, only from the laptop's speakers. 
can anyone help me? thanks!

---

### Post by BazookaAce on 2009-04-14
I had this problem myself in Ubuntu 8.10, but i upgraded to 9.04 Beta last week, and now the problem is solved. And man, it feels good!

---

### Post by sgtstukov on 2009-04-14
i installed the 9.04 beta but still have this problem. agh its driving me crazy, can anyone help?

---

### Post by BazookaAce on 2009-04-15
I don't know if this will work in 8/9.04 but you can try? 

[http://ubuntuforums.org/showthread.php?t=940709](http://ubuntuforums.org/showthread.php?t=940709)

And here's a thread that might help you:

[http://ubuntuforums.org/showthread.php?t=966241](http://ubuntuforums.org/showthread.php?t=966241)

---

### Post by sgtstukov on 2009-04-15
the links in the first thread you mentioned are broken, and the second thread did not solve my problem. anyone have any other solutions to a similar problem? thanks!

---

### Post by BazookaAce on 2009-04-15
Broken? Hmm, i can access it! But since you can't access that site, here it is:

```
 Headphone Not Working in Ubuntu Gutsy
I have a headphone that do not work lately, but when I searched for Ubuntu Tweaks, Tips and Howto, I found this codes in this Community, much thanks goes to hyperandy and his thread.

The codes runs this way:


wget ftp://ftp.alsa-project.org/pub/drive...1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/a...1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils...1.0.16.tar.bz2

Extracting them and removing tarballs:
Code:

tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

Making the directory for compiling the source:
Code:

sudo mkdir -p /usr/src/alsa
sudo mv alsa-* /usr/src/alsa

Compiling and installing alsa-driver
Code:

cd /usr/src/alsa/alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

Compiling and installing alsa-libs
Code:

cd /usr/src/alsa/alsa-lib*
sudo ./configure
sudo make
sudo make install

Compiling and installing alsa-utils
Code:

cd /usr/src/alsa/alsa-utils*
sudo ./configure
sudo make
sudo make install

*** I dont need to do the codes below, since it functions anyway, plus I got some error when I do them, but I am posting it here, you might be needing them.

After doing the codes above, do the following instructions:

Reboot the machine and run more these comands:
Code:

sudo cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
sudo depmod -a

Reboot once more. And the next time will have sound working, no extra tweaks needed, like adding some line to /etc/modprobe.d/alsa-base. The steps above must solve the problem with sound and mic. The mic will work after enabling all boxes in the Gnome mixer applet. Change the input source to "front mic" or "mic" depending on which microphone you are gonna use. That's it.

Once again, thanks to hyperandy, Long Live Ubuntu Users!
```

---

### Post by sgtstukov on 2009-04-15
each time i run the first 3 "wget" lines, i get a message saying "no such file 'a/drive/utils...1.0.16.tar.bz2'" any ideas?

---

### Post by BazookaAce on 2009-04-15
Nah, don't think it's working then, since that guide is for Gutsy. So i don't really have any other ideas at the moment. But you can report this bug at launchpad.

---

### Post by sgtstukov on 2009-04-16
after looking through google it seems like a lot of people have had this or a very similar problem... it seems to be something to do with the alsa sound drivers but i don't know what to do to fix it... anyone have experience with this?

---

