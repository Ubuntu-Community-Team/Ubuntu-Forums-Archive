---
title: "How I got microphone + headset + speaker muting working: Sony SZ650 and Ubuntu 7.10"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by arjunrc on 2007-12-20
**Notes on how to get things working on SONY SZ650 with Ubuntu 7.10 (Gutsy)**
[COLOR="Red"]
Note: some of these steps may be redundant - but I did it anyway, while trying all options to get my system working.[/COLOR]

**The facts for me: **There are many threads on how this may work, but not one thread worked for me in its entirety

**Problem :** Microphone may not work. Speakers may work, but if you plugin headphones, the audio still goes to the speaker.

**Resolution: **You most likely have alsa 1.0.14 installed. You need to upgrade to alsa 1.0.15.  There are many posts about this, but really, none of them seemed to fix everything. A combination of multiple posts worked for me.

**Step 1:**
Go to Synaptics, and uninstall existing alsa 1.0.14 drivers: alsa-base (don't remove alsa-utils as it will remove gdm and other useful apps). You must do this before you install  alsa 1.0.15 otherwise for me, plugging in the headphones did not mute the speaker. Infact, I tried to install alsa 1.0.15 over 1.0.14 without first removing it - that resulted in gnome-volume-manager not showing the internal mic option

**Step 2: **
Download alsa 1.0.15 drivers:

mkdir alsa && cd alsa

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)

wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)

wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)

**Step 3:**
Install them:


tar xjf alsa-driver-1.0.15.tar.bz2
tar xjf alsa-lib-1.0.15.tar.bz2
tar xjf alsa-utils-1.0.15.tar.bz2

cd alsa-driver-1.0.15

./configure --with-cards=hda-intel
 
make 
sudo make install

cd ..
cd alsa-lib-1.0.15

./configure
make 
sudo make install

cd ..
cd alsa-utils-1.0.15

./configure
make 
sudo make install


**Step 4: Modify installation**
Add this line to the end of /etc/modprobe.d/alsa-base
options snd-hda-intel model=vaio


Add the following lines to /etc/modules
snd-hwdep
snd-hda-intel

**Step 5: Detect sound card (as root)**
cd /etc/init.d
./alsasound stop
./alsa-utils stop

Now, run alsaconf

Let it detect you soundcard and say 'Yes' when it asks you whether it should modify the required files.

**Step 6: Reboot**

**Step 7: check for FATAL ERROR**
Go back to /etc/init.d and run (with root priv)
./alsasound restart
./alsa-utils restart

If you see an error like &#8220;FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-12-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)&#8221; along with other possible errors:

Then do the following:

See if you have the following two files:
/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko

If so, do this (with root priv)
rm /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
ln -s /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

Restart

**Step 8: Enable internal microphone**
Double click on volume icon on top bar
Go to 'switches'
Enable internal microphone

You should now be able to: 
use the microphone
when you plug in your headphones audio should be routed there and the speakers muted
[B]
How do you test it ? [/B]
Well you can use gnome-sound-recorder, but I just use Skype 2.0 beta for linux. I go to options->sound devices, and click on 'make a test sound' to verify my speakers. I then put in my headphones and do it again to ensure that the speakers are muted. I think click on 'test call' to ensure the microphone works. Skype 2.0 beta also has video calling, so I get to test my camera as well, all in one application together.

Why do I use skype ? Well, really, I mostly need sound only for skype :-) I generally like a quiet desktop otherwise. YMMV.

regds
arjun

---

### Post by frunns on 2007-12-20
Awesome! Thx for the guide. Been working on this all evening (and a few other days...). Now if I just could get gdm back... I use Linux Mint and for some reason it uninstalled gdm when I uninstalled alsa-utils...

---

### Post by arjunrc on 2007-12-20
hope it helps

---

### Post by chiacchio on 2008-01-07
Unfortunately if many other devices (webcam) are similar and use the same drivers,for my Sony Vaio SZ61MN the internal mic doesn't still work. Do you have any type of suggestion?

Thank you

---

### Post by ka1i on 2008-03-10
Thanks :D
I had been in trouble for a few days now and this solved my problem.
Worked on Ubuntu 7.10 on a Sony Vaio ar41l .
I had to install gettext to compile alsa utils and libncurses5-dev to compile something else (alsa-lib iirc).Also had some troubles with permissions and trying to compile alsa-utils before alsa-lib by mistake but everything eventually worked out.
Now to test the mic :S

Anyway,thanks again!

---

### Post by dracomordag on 2008-07-02
perfectly clear instructions, worked perfectly... thanks a lot man.

---

