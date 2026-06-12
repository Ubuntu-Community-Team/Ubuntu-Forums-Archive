---
title: "toshiba satellite p205-s6337"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by Pitbull11188 on 2007-07-08
Does anyone have any experience installing ubuntu or any distro on this laptop? If so could you please tell me which and how it worked?

I intend to find out if the store has a floor model available and if so I'm going test a livecd out on it, Thanks.

---

### Post by Pitbull11188 on 2007-07-14
I just purchased the p205-s6337 from circuit city about an hour ago. Here are the Facts:

-7.04 would not install from the livecd/install due to a recurring partitioning error

-7.04 did install from the alternate cd in text mode

-The webcam doesn't work (duh)

-The thumbprint reader doesn't work (duh)

-The wifi doesn't work, but I hear it can with some configuration

-Sound doesn't work out of the box but can be easily fixed 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

-The default resolution is 1280x800 but I hear it can be upped
[http://ubuntuforums.org/showthread.php?t=441482&highlight=p205](http://ubuntuforums.org/showthread.php?t=441482&highlight=p205)

-The browser key opens firefox


That's just an initial list and I will try to get all the special keys and features working, but I'm not holding my breath on the webcam or thumbprint reader.

I promise to update as soon as I get more done.

---

### Post by Pitbull11188 on 2007-07-15
The definitive way to make sound work on the p205-s6337.

enter this command 'sudo apt-get remove alsa'

Follow this guide to the letter: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and then do this: enter this command 'gksudo gedit /etc/modprobe.d/alsa-base' and then add this line to the end 'options snd-hda-intel position_fix=1 model=3stack'

Sound will then work upon rebooting.

---

### Post by vivalagina on 2007-07-15
Thank you so much! I've been trying to get sound to work all afternoon, and ended up accidentally killing my GUI for a while, but reinstalling the gdm and using that guide made everything work again.

---

### Post by Fliipn on 2007-07-17
> **vivalagina said:**
> Thank you so much! I've been trying to get sound to work all afternoon, and ended up accidentally killing my GUI for a while, but reinstalling the gdm and using that guide made everything work again.

didn't seem to work for my u205-S5022.. I do have the updated version of alsa installed 1.014.rc4 and still no sound.

---

### Post by Pitbull11188 on 2007-08-23
To fix the problem with the hd auto dumping at every shutdown:

'nano S00hdd-shutdown-workaround'

Put this in the file:

#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown

Then:

'cd etc/rc0.d'
'sudo chmod +x S00hdd-shutdown-workaround'

Upon reboot or shutdown hd no longer auto dumps thus preventing damage and wearing.

---

### Post by Pitbull11188 on 2007-08-30
I finally tested the SD card reader and it works flawlessly out of the box.

Gutsy is supposed to fix my wireless card.

Overall I'm very happy with this laptop and would suggest it to anyone on this forum.

---

### Post by Pitbull11188 on 2007-09-01
[http://ubuntuforums.org/showthread.php?t=511974&highlight=how+to+upgrade+kernel](http://ubuntuforums.org/showthread.php?t=511974&highlight=how+to+upgrade+kernel)

That gets wireless to work albeit not perfectly. It's impoosible to switch to wireless and then back to wired. Annoying, but not a showstopper.

---

### Post by Pitbull11188 on 2007-09-01
[http://ubuntuforums.org/showthread.php?t=511974&highlight=how+to+upgrade+kernel](http://ubuntuforums.org/showthread.php?t=511974&highlight=how+to+upgrade+kernel)

That gets wireless to work albeit not perfectly. It's impoosible to switch to wireless and then back to wired. Annoying, but not a showstopper.

echo 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted' | sudo tee -a /etc/apt/sources.list


sudo apt-get update


sudo apt-get -y install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic


gksudo gedit /etc/apt/sources.list
      add:              #deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted


sudo apt-get update


sudo reboot

---

