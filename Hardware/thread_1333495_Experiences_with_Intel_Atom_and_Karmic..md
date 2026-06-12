---
title: "Experiences with Intel Atom and Karmic."
date: 2009-11-21
forum: Hardware
---

### Post by Despot on 2009-11-21
I recently purchased a [Zotar IONITX-B-E Atom motherboard/CPU combo]("http://www.zotacusa.com/zotac-ionitx-b-e-atom-n230-1-6ghz-mini-itx-intel-motherboard.html") for a media center project, and wanted to share my experience.

Installing Karmic was a bit of a hassle. The installer started up fine, but when I got to the disk partitioner, the window was blank, and all the buttons were greyed out. This happened with both 32-bit and 64-bit versions of Karmic, and it didn't matter if I went directly to the installation routine or booted into the LiveCD environment and then started the installation. The disk (a Western Digital Caviar SE16 WD2500KS SATA drive) showed up in the /dev/ listing, dmesg, and in GPartEd when I booted into the LiveCD environment. The partitioner never worked though: no matter what I did it was always blank with all the buttons disabled. However, Jaunty's installer did not have these problems, so I was able to install Jaunty, then do a CD-ROM upgrade ([http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)).

After upgrading, I got a weird flickering login prompt when the computer started up. GDM never came up. Turns out the default Karmic install doesn't have a driver that supported the Geforce 9400M onboard video, so X would fail to load, and GDM would die. However, Upstart was configured to continuously respawn GDM, so GDM would keep respawning and dying, leading to the flickering problem.

To solve the problem, I needed to download the Nvidia 190.42 drivers as described here: [http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html"). Since GDM was on the fritz, I had to reboot into Recovery Mode and drop into a shell with network support.

When I experimented with the 32 bit version, I had trouble bringing up the network interface when I booted into Recovery Mode, so instead I edited the /etc/init/gdm.conf file and commented out the "respawn" statement. This allowed me to boot to a login prompt, login, and follow the instructions in the previously mentioned link.

When I experimented with the 64 bit version, I was prompted to insert the Karmic CD. I had mounted the ISO image instead of burning a CD, so I had to re-mount the ISO image on the mount point /cdrom/ for the driver installation to succeed.

After installing the drivers, I had to add following line to the Device stanza in /etc/X11/xorg.conf:

```
Driver "nvidia"
```

With these adjustments in place, GDM started correctly, and I was able to login normally. Now I just have to get surround sound working! :p

---

### Post by Despot on 2009-11-21
To get surround sound working, this is helpful:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

The board I was using had an ALC662 chipset. With a bit of Googling I found that I needed to edit this line in /etc/modprobe.d/alsa-base.conf:

```
options snd-hda-intel power_save=10 power_save_controller=N
```

The revised line looks like this:

```
options snd-hda-intel power_save=10 power_save_controller=N model=3stack-6ch
```

Unfortunately I cannot find the page where I picked up this info. [http://alsa.opensrc.org/index.php/Hda](http://alsa.opensrc.org/index.php/Hda) has some good information, as does [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main), and this older forum thread: [http://ubuntuforums.org/showthread.php?t=1320013](http://ubuntuforums.org/showthread.php?t=1320013)

Running the speaker-test mentioned in the Ubuntu Surround Sound guide was still not working, though: the channels were being downmixed to stereo. Issuing this command sets the ALSA driver to 6 channel mode:

```
amixer -q set "Channel Mode" "6ch"
```

This option is also available in the alsamixer utility.

The 6 channel speaker test worked correctly after this, and once I'd rebooted, the Surround Sound options were available in the System-Preferences-Sound dialog under the Hardware tab, and surround sound worked in VLC. Hooray!

(edit)
I have since experienced some problems with odd ringing sounds in the satellite speakers on my surround setup, seemingly related to the low ranges. These problems only seem to occur when the Surround Sound options are selected in the Sound dialog--setting the output type to stereo resolved the problem, but of course I no longer have surround sound. I believe this is a problem with the driver, though, not the motherboard.

---

### Post by wesg on 2009-11-21
Thanks for the updates. I was just dreaming of building an Atom/ION machine for the home theatre.

Be sure to post updates when the video is running!

---

### Post by Despot on 2009-11-22
Glad it helped :) Video works great: after I got GDM working, all the other stuff fell into place. Compiz works fine, DVDs play fine, etc.

---

