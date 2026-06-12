---
title: "[SOLVED] No sound, Znote 6024W (Realtek ALC268)"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by Knorr on 2007-09-15
Good evening!

I've recently purchased a Znote 6024W laptop from Zepto.

It contains the sound device ALC268, which I can't get to work properly in Ubuntu.

I've looked at the various threads on these forums and tried a lot of different things. None has helped me.

I'm running Gutsy kernel 2.6.22-11 and I've tried to compile the newest ALSA driver (driver: 1.0.15RC2, lib: 1.0.15RC2, util: 1.0.15RC1) and added the "options snd-hda-intel model=toshiba" line in /etc/modprobe.d/alsa-base. Tried with model=auto and model=acer too.

When I try to compile with one of the various patch_realtek.c files around the forum I get some errors during make. 
```
In file included from /home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/patch_realtek.c:2:
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc_resume’:
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:2000: advarsel: implicit declaration of function ‘snd_hda_resume_ctls’
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:2002: advarsel: implicit declaration of function ‘snd_hda_resume_spdif_out’
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:2004: advarsel: implicit declaration of function ‘snd_hda_resume_spdif_in’
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc882_mux_enum_put’:
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:4760: fejl: ‘struct hda_codec’ has no member named ‘in_resume’
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc883_mux_enum_put’:
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:5643: fejl: ‘struct hda_codec’ has no member named ‘in_resume’
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc262_fujitsu_master_sw_put’:
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:7166: fejl: ‘struct hda_codec’ has no member named ‘in_resume’
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:7167: fejl: ‘struct hda_codec’ has no member named ‘in_resume’
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc268_mux_enum_put’:
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:8004: fejl: ‘struct hda_codec’ has no member named ‘in_resume’
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc861vd_mux_enum_put’:
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:9617: fejl: ‘struct hda_codec’ has no member named ‘in_resume’
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c: In function ‘alc662_mux_enum_put’:
/home/jesper/Desktop/alsa-driver-1.0.15rc2/pci/hda/../../alsa-kernel/pci/hda/patch_realtek.c:10547: fejl: ‘struct hda_codec’ has no member named ‘in_resume’
```

If I try modprobe snd-hda-intel I get a "snd-hda-intel: Unknown symbol snd_hwdep_new" error in dmesg.

Help debugging this would please these new Ubuntu user a lot. :)

 - Knorr

---

### Post by ilkkal on 2007-10-06
What was the answer?

---

### Post by Knorr on 2007-10-07
1. Delete /lib/modules/`uname -r`/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
2. Re-compile alsadriver
3. gedit /etc/modprobe.d/alsa-base
4. add the line "options snd-hda-intel model=toshiba"
5. If the file /etc/modprobe.d/snd-hda-intel.modprobe exists then make sure the options snd-hda-intel line has model=toshiba

---

### Post by Jojan on 2007-10-20
I have the same computer, Zepto 6024W, and I don't get any sound. I'm also pretty new to Ubuntu so I don't know how to reompile the alsa driver. I have Ubuntu 7.10,

---

### Post by ilkkal on 2007-10-21
> **Knorr said:**
> 1. Delete /lib/modules/`uname -r`/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
2. Re-compile alsadriver
3. gedit /etc/modprobe.d/alsa-base
4. add the line "options snd-hda-intel model=toshiba"
5. If the file /etc/modprobe.d/snd-hda-intel.modprobe exists then make sure the options snd-hda-intel line has model=toshiba

Thank you so much! This really did the trick!

A bit of knowledge about compiling the alsa-driver (I hope this is correct, because I'm kinda new to this also):
Install the necessary for building the package:
```
 sudo aptitude install build-essential linux-headers-$(uname -r) libncurses5-dev libncursesw5-dev 
```

Then you should download the package:
```
 wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2 
```
and untar it and go to the directory:
```
tar xjf alsa-driver-1.0.15.tar.bz2;cd alsa-driver-1.0.15.tar.bz2
```

Now the actuall compiling part:
```
./configure
```
```
make
```
```
make install
```

Now they should be compiled. You can remove the directory and tar-ball.

---

### Post by Knorr on 2007-10-21
> **ilkkal said:**
> 
Now the actuall compiling part:
```
./configure
```

This will compile the driver with support for all drivers included.

You can with advantage use this instead
```

./configure --with-cards=hda-intel

```

---

### Post by kkjaergaard on 2007-10-22
I have the same computer with the same sound card. Do I need to compile the ALSA thing myself, or will the official ALSA Ubuntu packages work in the future?

How do I update ALSA if I compile it myself?

---

### Post by Knorr on 2007-10-22
> **kkjaergaard said:**
> I have the same computer with the same sound card. Do I need to compile the ALSA thing myself, or will the official ALSA Ubuntu packages work in the future?

How do I update ALSA if I compile it myself?

As far as I remember the ALSA included in Ubuntu is 1.0.14, which doesn't support ALC268 as well as the present 1.0.15, if it does at all.

You can update your ALSA driver by the steps mentioned here in this thread.

```

sudo rm /lib/modules/`uname -r`/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo aptitude install build-essential linux-headers-$(uname -r) libncurses5-dev libncursesw5-dev
cd /usr/src
mkdir alsa
cd alsa
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
tar -xf alsa-driver-1.0.15.tar.bz2
cd alsa-driver-1.0.15.tar.bz2
./configure --with-cards=hda-intel
make
sudo make install

```

You can use this for future updates as well. Just find the newest tarball from [www.alsa-project.org](www.alsa-project.org)

---

### Post by Jojan on 2007-10-23
This guide worked well for me. The only thing is that when I have my volume turned up to more than 3/4  some noice disturbance or distortion gets heard.

---

### Post by kkjaergaard on 2007-10-26
It doesn't work for me. I did as you wrote, but I get no sound on any device.

After "make install"-ing I was asked to unmute the channel, but it does not seem to be muted in alsamixer.

---

### Post by xc3RnbFO8P on 2007-10-30
> **Knorr said:**
> 1. Delete /lib/modules/`uname -r`/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
2. Re-compile alsadriver
3. gedit /etc/modprobe.d/alsa-base
4. add the line "options snd-hda-intel model=toshiba"
5. If the file /etc/modprobe.d/snd-hda-intel.modprobe exists then make sure the options snd-hda-intel line has model=toshiba

This worked for me, a got Zepto znote 3215 :)

alsa-driver-1.0.15rc3

---

### Post by Tavathlon on 2007-10-31
I have the driver compiled, and it works really nicely as long as I only use the internal speakers and rythmbox. However, I have some other problems:

- The sound is always muted on reboot (although that is actually pretty handy for me - it's just that it should not be like that, I suppose...
- The external volume control does not work for changing the volume of the internal speakers (which it did when I used the live cd).
- Whenever I paus a movie, the sound gets muted. Not in the normal muting way, it gets back if I adjust the volume.
- Whenever I plug in external speakers, the sound gets muted in the same way as when I paus movie player.
- No matter whether I reenable the sound after having plugged in external speakers, the speakers won't give any sound - the internal ones does still give sound, though. And it's nothing about the speakers, I know they work - I have double checked that.

So..  a bunch of bugs, ey? =P
Btw, I have a Znote 6625WD, but I think it's the same soundcard as in the 6024W.

Anyone who have any ideas on how I could fix this? Or perhaps, anyone who knows when alsa version 1.0.15 will be integrated in ubuntu?

---

### Post by swedub on 2007-11-04
> **Knorr said:**
> As far as I remember the ALSA included in Ubuntu is 1.0.14, which doesn't support ALC268 as well as the present 1.0.15, if it does at all.

You can update your ALSA driver by the steps mentioned here in this thread.

```

sudo rm /lib/modules/`uname -r`/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo aptitude install build-essential linux-headers-$(uname -r) libncurses5-dev libncursesw5-dev
cd /usr/src
mkdir alsa
cd alsa
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
tar -xf alsa-driver-1.0.15.tar.bz2
cd alsa-driver-1.0.15.tar.bz2
./configure --with-cards=hda-intel
make
sudo make install

```

You can use this for future updates as well. Just find the newest tarball from [www.alsa-project.org](www.alsa-project.org)

WOW! Thank you! This finally fixed my audio problem. Now my Toshiba Satellite A215-S7422 has sound! Next step, internal wi-fi. Then I can finally say good-bye to Windows.

---

### Post by dkov on 2007-11-05
I can't do the mkdir alsa step. I get Permission denied. What do I need to do? I've tried adding myself to various groups and logging in again.

---

### Post by Knorr on 2007-11-06
> **dkov said:**
> I can't do the mkdir alsa step. I get Permission denied. What do I need to do? I've tried adding myself to various groups and logging in again.

Just do a "sudo mkdir alsa"

---

### Post by dkov on 2007-11-06
Aha, thanks.

I'm almost there but I can't do the ./configure line. I get error: C compiler cannot create executables. I started the line sudo as well.

---

### Post by linuxonbute on 2007-11-06
> **Ringi said:**
> This worked for me, a got Zepto znote 3215 :)

alsa-driver-1.0.15rc3

I am thinking of buying the Znote 3215W

Did you have any other problems to overcome or was it just the sound?

tia
Norm

---

### Post by dkov on 2007-11-06
Any help with my compiler error? Here's the log file, renamed as .txt so it would upload:

---

### Post by fortinbras on 2007-11-12
> **ilkkal said:**
> Thank you so much! This really did the trick!

A bit of knowledge about compiling the alsa-driver (I hope this is correct, because I'm kinda new to this also):
Install the necessary for building the package:
```
 sudo aptitude install build-essential linux-headers-$(uname -r) libncurses5-dev libncursesw5-dev 
```

Then you should download the package:
```
 wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2 
```
and untar it and go to the directory:
```
tar xjf alsa-driver-1.0.15.tar.bz2;cd alsa-driver-1.0.15.tar.bz2
```

Now the actuall compiling part:
```
./configure
```
```
make
```
```
make install
```

Now they should be compiled. You can remove the directory and tar-ball.

Over the last few days I have tried this numerous times.  Finally, I decided to start fresh.  Therefore, I reformatted my partitions and began with a clean slate.  On the first attempt, after rebooting of course, I had sound.  Thank you all for your input on this matter.  As others have said and many are probably wishing... let there be Wifi!!!!  If anyone has a fix for the wifi please post it!  Thanks.

Oh, by the way, this thread fixed a no sound issue with the following hardware:

Toshiba A215-S7422
Ubuntu Gutsy

---

### Post by Anders Rasmussen on 2007-11-13
> **dkov said:**
> Aha, thanks.

I'm almost there but I can't do the ./configure line. I get error: C compiler cannot create executables. I started the line sudo as well.

I had the same problem, but got an advice on a danish ubuntu forum to install div. libs and tools for compiling:

sudo aptitude install build-essential

On my computer this required the ubuntu install cd, but by using synaptic and disable the need for the cd I could get it by the internet.

That worked for me so far as I could get the sudo ./configure command to work, and making the installation (remember to use sudo _all the time_)...
BUT the soud still dosent work, I think I have the same problem as kkjaergaard in this thread:
> It doesn't work for me. I did as you wrote, but I get no sound on any device.

After "make install"-ing I was asked to unmute the channel, but it does not seem to be muted in alsamixer.

Anyone got a clue? Kjærsgård have you discovered any solution?

Cheers
Anders

---

### Post by Jojan on 2007-11-13
**But hey!** I just found a CD I got when I bought the 6024W that I had forgotten about. It has Windows drivers for the audio (and some other stuff). Is there a way to install the audio drivers even if they're made for Vista, XP and 2000.

---

### Post by dkov on 2007-11-14
Thanks for the help with compiling, Anders. That worked just fine for me after getting build-essential.

Unfortunately, I still get no sound.

---

### Post by Anders Rasmussen on 2007-11-16
Well, then it seems we stuck the same place dkov. I guess next stop i Googleing until something comes up...

And Jojan, I don't think the xp-drivers will help in Linux, but I cant say for sure. My problem right now is, that I don know what the problem really is - I have installed a driver that people in this thread says work, and I can now un-mute my sound (which I couldn't before), but still don't get any sound.

So close and yet so far...
Anders

---

### Post by hortimech on 2007-11-16
I have an HP laptop with this sound chip and the only way I could get sound was to install the OSS sound driver, see this post, it might help.

[http://ubuntuforums.org/showpost.php...4&postcount=60](http://ubuntuforums.org/showpost.php...4&postcount=60)

---

### Post by dkov on 2007-11-16
Hortimech, the URL you posted is broken. Can you please repost it?

---

### Post by dkov on 2007-11-16
I found it, over here: [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

---

### Post by Anders Rasmussen on 2007-11-17
Hmm, I dont see the ALC 268 in the list of OSS supported devices here:
[http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html)


But, back to the ALSA.

I ran the "alsamixer" command in the Terminal and got to some sort of control screen. In the top it says: "AlsaMixer v1.0.14". That sorta imply, that I haven't updated the driver, which I don't really get...

Anyone got a clue how I can see if I really have updated v1.0.15 or the system just made me think that?

There
Anders

---

### Post by Anders Rasmussen on 2007-11-27
Shameless bump....

Anyone got a clue?

---

### Post by xc3RnbFO8P on 2007-11-30
> **linuxonbute said:**
> I am thinking of buying the Znote 3215W

Did you have any other problems to overcome or was it just the sound?

tia
Norm

Just the sound, I use usb wireless WCN 0103 Level One and Level One Router.
Sorry for the late respond.

---

### Post by lefredbleu on 2007-12-02
Just to let people know : compiling alsa new tarball as shown previously in this thread works well with Toshiba Tecra A7. 

You just have to remember to uninstall the package you created if you tried the module-assistant method with ubuntu alsa-sources (This method does not work for the tecra A7)

---

### Post by iamnew on 2007-12-08
Great! you made my day when i was about to give up on this laptop

---

### Post by martin.demare on 2007-12-19
I found this thread after I fixed the problem om my Znote 3415w. I was helped by the excellent instructions on this link:
[http://atlas.hasselbalch.com/znote6625wd/](http://atlas.hasselbalch.com/znote6625wd/)

I can't really tell if the same information is already in the thread or not. 
(When following the link, note that I had to restart the computer for the changes to take effect.)

---

### Post by kurotenshi on 2008-01-13
Worked for me but I still have sound on the speakers and headphones at the same time, low volume on the speakers and a lot of noise

Hardware: Toshiba A200-1SX

---

### Post by martinrandau on 2008-01-14
This fix seems to be redundant in Hardy since we're using pulseaudio, and there is no /lib/modules/`uname -r`/ubuntu/media/snd-hda-intel/snd-hda-intel.ko directory.

---

### Post by linuxonbute on 2008-01-22
> **kurotenshi said:**
> Worked for me but I still have sound on the speakers and headphones at the same time, low volume on the speakers and a lot of noise

Hardware: Toshiba A200-1SX
Right click on the speaker icon on the top taskbar.

Choose Open Volume Control
Click on Edit / Preferences
Select all the options to so they display in Alsamixer

Then back in the Volume Control you should be able to mute the speakers or headphones etc.
Best wishes.

---

### Post by Loupax on 2008-03-15
First post! Yay!
I got myself a new laptop, and deleted the Vista partition to install Gutsy 7.10 :P
I have the same soundchip (Realtek ALC268 ) AND the same soundboard, and still have the same problem... No sound anywhere, no error messages, even though I installed the latest ALSA driver just a couple of minutes ago (Version 1.0.16).
I get the "ALSA channels muted by default" message, but the ALSAmixer shows that they are not muted, and I cannot find some conf file where this setting is stored... Any ideas?
Does the brand of the Laptop matter or just the sound chip model?

---

### Post by Loupax on 2008-03-15
No need after all! I compiled the Realtek Linux driver as said [here]("http://atlas.hasselbalch.com/znote6625wd/") and everything worked just fine! 
Remember! Before you follow the instruction, kill any application using the sound card!

---

### Post by Jojan on 2008-05-01
Has anyone tried a freash install of Hardy Heron, and cheked if that could fix it?

I might to this later.

---

### Post by Ralph386 on 2008-06-13
Many thanks for the tip, you made my day!!!!!!!

I found small details using ubuntu 8.04 in a Toshiba satellite:
I downloaded the last version of alsa-driver (alsa-driver-1.0.16.tar.bz2) in my desktop, with a terminal I went to desktop and typed:

tar -xf alsa-driver-1.0.16.tar.bz2

after that a folder was created and then I wrote (without.bz2):

cd alsa-driver-1.0.16.tar
./configure --with-cards=hda-intel
make
sudo make install

After that I typed

gedit /etc/modprobe.d/alsa-base
add the line "options snd-hda-intel model=toshiba"

I got a message that I didn't have enough permissions to do the change, so I modified alsa-base file permissions following the next link: [http://www.linuxcommand.org/lts0070.php](http://www.linuxcommand.org/lts0070.php)

I re-started the computer

and in System/Preferences/Sound I select ALSA for all the events and HDA Intel (Alsa mixer)

Have a great day!!!> 

---

