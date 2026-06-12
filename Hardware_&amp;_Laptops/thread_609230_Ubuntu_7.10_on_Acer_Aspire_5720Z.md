---
title: "Ubuntu 7.10 on Acer Aspire 5720Z"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by Pallando on 2007-11-10
I just picked up this very slick laptop a couple days ago after some issues with shipping (CDW is awful). After some searching and trying different methods to get it to work, I can happily confirm that everything works except for the cardreader and bluetooth. To get wireless and sound working, I had to use the instructions [here]("http://ubuntuforums.org/showthread.php?t=512828") and [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto") respectively, but they worked perfectly.

As to the cardreader and the bluetooth: I've searched and searched for drivers or fixes for the reader but cannot find any, and I don't have any bluetooth devices to test (sorry!). I've had no problems with monitor resolution out of the box.

I hope this can help anyone else with this laptop or other similar Aspires, and if someone has a solution for my card reader (device manager seems to say it's an amalgamation of Rico R5C592, R5C822, R5C832, R5C843, and a model-number-less xD-Picture Card Controller) that would be a great help. :)

---

### Post by Fred_S on 2007-11-16
I tried this myself (fixing sound) but i just ended up to get errors and i had to reinstall, anyways do you have Intel soundcard? 

* Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev3)
* Subsystem: Acer Incorporated [ALI] Unknown device 011e.

My wireless seems to work well from the start so i guessed that we might have different have different Hardware. I've tried so much to get this to work, browsing through guides and such but it still wont work.

---

### Post by firedragonsf on 2007-12-11
> **firedragonsf said:**
> fix for my graphics prob:
At first boot have an internet connection that helps.

1. Go to System ==> Administration ==> Restricted Drivers Managment
2. Check the enabled box and if you have internet it should fix it self.
3. If not reinstall ubuntu :P

fix for my sound prob:
Sound drivers fix for acer aspire 5720z 
		source: [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

1.Copy the first block of text to a text file and save as alsa_1.sh, and then the second block to alsa_2.sh 

2.Then "cd" to it in a terminal 
	code: "cd /home/henrik/Desktop"
  if your file is on desktop

3. then type "sudo sh alsa_1.sh"

4.Now reboot

5.Type "sudo sh alsa_2.sh"

6.Open up terminal and write this:
	"sudo gedit /etc/modprobe.d/alsa-base"

7.It will open up a script, scroll to the bottom, make a new line and write this:
	"options snd-hda-intel model=acer"


Text for alsa_1.sh

```
#!/bin/sh
#
#install necessary stuff
apt-get install build-essential ncurses-dev gettext
apt-get install linux-headers-`uname -r`

echo "downloading alsa packages..."
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2

echo "extracting alsa packages..."
tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

echo "setting up alsa for compilation"
mkdir -p /usr/src/alsa
mv alsa-* /usr/src/alsa

#alsa-driver
cd /usr/src/alsa/alsa-driver*
./configure --with-cards=hda-intel
make
make install

#alsa-lib
cd /usr/src/alsa/alsa-lib*
./configure
make
make install

#alsa-utils
cd /usr/src/alsa/alsa-utils*
./configure
make
make install

echo "now reboot your machine, and run alsa_2"
#end of alsa_1
```





Text for alsa_2.sh

```
#!/bin/sh
#for after reboot
cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
depmod -a
#end of alsa_2
```





This worked om my acer aspire 5720z

.

---

### Post by isparkes on 2008-01-29
There's a more sinister problem with this laptop and Ubuntu. I'm suffering from it at the moment, and can't find a solution to it.

The problem is with the power management, and the unit just shutting down randomly. You can be working, and all of a sudden, it just turns off. No warning, no message, just a hard shut down.

I have found this interesting thread, which goes some way to explaining what is going on. On Windoze, there is a utility that manages the fan speed and power management. On Ubuntu, there is no such utility.

[http://ubuntuforums.org/showthread.php?t=604158&highlight=acer+power+management](http://ubuntuforums.org/showthread.php?t=604158&highlight=acer+power+management)

The symptoms are:
 - the unit performs a shut down when under load (this shut down is in fact a thermal hardware protection, because the fan management is not correct)
 - the problem is worse after waking up from a suspend or hibernate
 - The fan runs all the time, or does not run at all

All in all, I'm disappointed that Acer looks like it is doing things that should be managed in hardware (fan control) in software (the Windoze app).

Anyone got any thoughts about this?

---

### Post by isparkes on 2008-01-31
Just an update on this. I am now avoiding hibernating and suspending, and I'm not getting the problem any more.

Because the Ubuntu boot is not that much longer than a "wake up" (I have 2GB of RAM, so it takes a while), I'll live with it.

Apparently, there is a whole thread of this on the Debian Kernel forum. I'm sure it will get worked out soon, as it is a known issue. I'd like to try to help solve the problem, but the kernel is out of my competence zone... %-)

---

### Post by wraithe on 2008-02-01
Just installing linux onto one of these laptops, its had a major problem in the past from shutting down, my friend who owns it was unhappy, especially as they couldnt run BOINC...
I have pulled the cover off, and behind the fan is a little radiator, its very small, and as the whole setup is crammed in, it gets a little dust on there, and it overheats...
After just blowing it out, its fine again...
(This may not be your case, but its a start towards solving it)...

---

### Post by isparkes on 2008-02-17
Just an update on this - the shutdown problem is due to a "non-compatibility" of the Acer hardware. It happens only when using the unit after resuming from a suspended or hibernated state. Acer provides some kludgeware under Windows to reset the hardware every so often, but nothing is yet available in the kernel to do the same work (it is a known and reported error, though).

Workaround: Just shutdown and restart the unit instead of hibernating or suspending it. I know that this is not a great answer, but with 2GB of RAM, there's not a great deal of difference in the time taken to boot.

---

### Post by Bookman on 2008-04-08
> **isparkes said:**
> There's a more sinister problem with this laptop and Ubuntu. I'm suffering from it at the moment, and can't find a solution to it.

The problem is with the power management, and the unit just shutting down randomly. You can be working, and all of a sudden, it just turns off. No warning, no message, just a hard shut down.

I have found this interesting thread, which goes some way to explaining what is going on. On Windoze, there is a utility that manages the fan speed and power management. On Ubuntu, there is no such utility.

[http://ubuntuforums.org/showthread.php?t=604158&highlight=acer+power+management](http://ubuntuforums.org/showthread.php?t=604158&highlight=acer+power+management)

The symptoms are:
 - the unit performs a shut down when under load (this shut down is in fact a thermal hardware protection, because the fan management is not correct)
 - the problem is worse after waking up from a suspend or hibernate
 - The fan runs all the time, or does not run at all

All in all, I'm disappointed that Acer looks like it is doing things that should be managed in hardware (fan control) in software (the Windoze app).

Anyone got any thoughts about this?

A solution for the power shutdown that worked on my Aspire 5715z is here, all credit to David Edwards for suppling the solution
[http://ubuntuforums.org/showthread.php?p=4675762]("http://ubuntuforums.org/showthread.php?p=4675762")

---

