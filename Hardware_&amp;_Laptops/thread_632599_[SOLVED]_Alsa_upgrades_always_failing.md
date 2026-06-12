---
title: "[SOLVED] Alsa upgrades always failing"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by dysphasi on 2007-12-05
Ok...basically I'm using a Sony Vaio VGN-C2S with an hda-intel soundcard.

My problem is that whilst sound works on gutsy, if I plug my headphones in, the sound continues to play on laptop speakers as well as in the headphones unless I mute the laptop speakers via alsamixer from the terminal.

I found out that by using the following alsa packages:

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc3.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.15rc1.tar.bz2)

everything worked. I wrote down the instructions for myself clearly, and even reformatted and reinstalled, following my instructions to install the drivers...all worked fine...

....UNTIL NOW

Just today I reformatted in order to wipe my windows partition (---yes I hope to be a full convert!) Followed the instructions to upgrade my alsa again and this time when I restart I get no sound whatsoever. 

My speaker icon on the gnome panel is also muted, when I double click on the icon I get: 
"No volume control GStreamer plugins and/or devices found"

Essentially it appears no audio device is found, aplay -l lists "no soundcards found..."

I really don't know what's wrong, I used the exact same ubuntu disk to install gutsy, used the same instructions as before to upgrade alsa and now have no sound device whatsoever according to the messages I've been getting!

Please could someone help me out here, I'm at a complete loss.

---

### Post by dysphasi on 2007-12-05
For completeness sake below is the method I used once the relevant archives were unpacked:

1. sudo /etc/init.d/alsa-utils stop

2. sudo apt-get remove --purge alsa-base alsa-tools

3. sudo apt-get install linux-headers-$(uname -r) build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext po-debconf debhelper quilt alsa-base libc6-dev

4. Install driver:

cd alsa-driver-1.0.15rc3/
sudo make clean
./configure --with-oss=yes --with-cards=hda-intel 
sudo make
sudo make install

5. Install alsa-lib:

cd ../alsa-lib-1.0.15rc3
sudo make clean
./configure
sudo make
sudo make install

6. Install alsa-utils:

cd ../alsa-utils-1.0.15rc1
sudo make clean
./configure
sudo make 
sudo make install

7. Install alsa-firmware:

cd ../alsa-firmware-1.0.15rc1
sudo make clean
./configure
sudo make 
sudo make install

8. Double-click Volume control (the speaker next to the clock), then Edit-Preferences and check all the boxes. Close Preferences.

9. Go to Switches and check headphones/LineIn

10. Go to Recording tab and ensure both mic and speakers are not muted.

11. Go to Playback tab and ensure nothing (except IntMic if present) is muted.

12. Back in the terminal type: sudo /etc/init.d/alsa-utils start and restart the computer

nb... I know not all those make cleans are required from the outset...bit of a cut and paste job and I gather they can't do any harm.

---

### Post by Yellow Pasque on 2007-12-05
I'd suggest trying again with the release version of 1.0.15
Take out the rc_ in your wget filenames and try again.

---

### Post by dysphasi on 2007-12-05
Did so, no joy. 

Even ran someone else's script for the same card which essentially seems to run the exact same commands as I've been entering.

BUT I at last found the solution, just needed to use Gutsy Backports by running the following from the terminal:
```
 sudo aptitude install linux-backports-modules-generic 
``` 
et voila, all works :D

I discovered this tip at the following site:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

:guitar:

---

