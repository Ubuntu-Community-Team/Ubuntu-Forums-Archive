---
title: "[SOLVED] High Definition Audio"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by brunoskrebs on 2007-08-18
Hello,

I'm a little bit new to ubuntu. I've installed it two days ago. Everything is runing perfectly besides my audio. I have a Toshiba a135 s4656, and the driver that I was using for the windows xp was High Definition Audio. I saw in the device manager that is written High Definition Audio Controller, but when I tried to listen to a music it didnt work. Then I open the device manager again and made a test, it tested the Audio, the video, the wireless and other stuff, and the only one that not worked was the audio.

Does anyone can help me:

Thanks. Bye

Bruno Krebs

---

### Post by steveneddy on 2007-08-18
Tell more about the hardware.

Brand of PC. Type of sound card. 

Are the speakers hooked up?

Are they turned on?...or turned up?

---

### Post by bombina on 2007-08-26
> **brunoskrebs said:**
> Hello,

I'm a little bit new to ubuntu. I've installed it two days ago. Everything is runing perfectly besides my audio. I have a Toshiba a135 s4656, and the driver that I was using for the windows xp was High Definition Audio. I saw in the device manager that is written High Definition Audio Controller, but when I tried to listen to a music it didnt work. Then I open the device manager again and made a test, it tested the Audio, the video, the wireless and other stuff, and the only one that not worked was the audio.

Does anyone can help me:

Thanks. Bye

Bruno Krebs

Hi Bruno

it might well be that I got the same laptop as you do. 
No sound with feisty.
On a fresh feisty install i got

bombina@laptop:~$ head -n 3 /proc/asound/card0/codec#0
Codec: Realtek ALC861-VD
Address: 0
Vendor Id: 0x10ec0862

The first thing I tried:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

The result was that the command above said something along the lines "no soundcard found"

Then I tried
[http://www.linlap.com/forum/viewtopic.php?p=494](http://www.linlap.com/forum/viewtopic.php?p=494)

Look at what g4t0x wrote:

sudo apt-get install build-essential ncurses-dev
sudo apt-get install linux-headers-`uname -r`
cd ~
mkdir alsa-src
cd alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14rc3.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14rc2.tar.bz2)
[These drivers are different from above from the HdaIntelSoundHowto link...]

sudo /etc/init.d/alsasound stop

tar xvf alsa-driver-1.0.14rc3.tar.bz2
tar xvf alsa-lib-1.0.14rc3.tar.bz2
tar xvf alsa-utils-1.0.14rc2.tar.bz2

cd ~/alsa-src
tar xvf realtek6.tar.gz
[I am unsure if you reallly need to do this. The patch is already in that directory...You will have to download it first.  wget [http://lenovo.dropshock.com/files/realtek6.tar.gz]](http://lenovo.dropshock.com/files/realtek6.tar.gz])

cp patch_realtek.c ~/alsa-driver-1.0.14rc3/alsa-kernel/pci/hda/
[There is something wrong in this copy command. You will have to adjust this for your needs]

cd alsa-driver-1.0.14rc3
./configure --with-cards=hda-intel
make
sudo make install

cd ../alsa-lib-1.0.14rc3
./configure
make
sudo make install

cd ../alsa-utils-1.0.14rc2
./configure
make
sudo make install
[At this point I restarted the computer and I had sound. So I skipped the rest]

Bear with me though I am no expert. My philosophy is: I can always reinstall if seriously break something...

P

---

