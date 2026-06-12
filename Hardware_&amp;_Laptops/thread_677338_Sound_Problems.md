---
title: "Sound Problems"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by shoeshrimp on 2008-01-24
Hey Guys, I'm sure you hear this all the time, but I'm having problems with my sound on a new Ubuntu install on a Toshiba Satellite A30. It uses a Realtec AC'97 sound card, and just has no sound. I've tried a few of the fixes online, but none of them seem to work (like unchecking one of the modem drivers...)

Hope you might have some idea as to what the problem might be!

Thanks in advance,

Tom

---

### Post by HariVenkata Lakshmi Kumar on 2008-01-24
HI Buddy,
not sure if it helps you.. but try it out...

reinstall ALSA driver
run:
[B]sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
[/B]in terminal

and
**sudo gedit /etc/modprobe.d/alsa-base**

add the following line in opened config file

**options snd-hda-intel model=vaio position_fix=0**


now reboot.

---

### Post by shoeshrimp on 2008-01-24
Thanks for your message,

unfortunately that does not seem to work. I get a noise on login, but other than that it's all silent, and sound juicer crashes after playing 2 secs of an audio cd...

It's very strange

---

### Post by Casual Fan on 2008-01-24
My sole purpose on this forum: Spread this thread.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Go through the steps; it may help.

---

### Post by shoeshrimp on 2008-01-24
as does totem when trying to play an mpeg file.. i have all the codecs...

any ideas?

thanks in advance,

tom

---

### Post by Yellow Pasque on 2008-01-24
Try the latest version of ALSA.
Run the two scripts found in this post. (reboot in between as instructed). I would suggest altering the first script to download "1.0.16rc1" instead of "1.0.15"
[http://ubuntuforums.org/showpost.php?p=3603812&postcount=13](http://ubuntuforums.org/showpost.php?p=3603812&postcount=13)

---

### Post by shoeshrimp on 2008-01-26
Whenever I try to run any music software it crashes when I try to play a track. Could this be a sound drivers problem?

---

### Post by shoeshrimp on 2008-01-26
Hey, I've tried running those two shell scripts, but encounter problems on the 2nd one...


tom@tom-laptop:~/Desktop$ sudo sh alsa_2.sh
cp: cannot stat `/lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver*/modules/*': No such file or directory


what do I do!?

Thanks

---

### Post by shoeshrimp on 2008-01-27
> **Casual Fan said:**
> My sole purpose on this forum: Spread this thread.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Go through the steps; it may help.

Heya, I went through the comprehensive sound thing, found my drivers and reinstalled them, but I get:

tom@tom-laptop:~$ sudo modprobe snd-
FATAL: Module snd_ not found.
tom@tom-laptop:~$ 

afterwards, and now when I click on volume control I get:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.



oh no! What has happened!?

Thanks in advance,

Tom

---

