---
title: "Acer Aspire 6920G Sound Card Solution for the #bug issue with Intel ICH 8 (Realtek 88"
date: 2008-12-17
forum: Hardware
---

### Post by nikkpap on 2008-12-17
Acer Aspire 6920G Sound Card Solution for the #bug issue with Intel ICH 8 (Realtek 889) & Ubuntu 8.10 Intrepid Ibex

UPGRADE YOUR ALSA** 1.0.18a +

In the fist line i will try to explain what the commands do, and in the second line how to execute the command... Let's start...
*S.O.S Don't use in terminal the "" only the commands WithOUT the ""

1) Upgrade the ALSA (Advanced Linux Sound Architecture)) Drivers to the latest

a) Login as root by

" sudo -s "

b) To start the installation download this script at your home folder:
 
" [http://www.box.net/shared/454ic17as0](http://www.box.net/shared/454ic17as0) "


c) This script will download the ALSA 1.0.18a drivers from the ALSA-PROJECT website and install them automatically. 
	After that your pc reboots, so don't do anything else...

" sudo chmod +x alsa_setup "
" sudo ./alsa_setup.sh "

d) After the reboot you have to download at Home directory the following file
	[ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz](ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz) 
	** if the site goes down google it with hda-verb-0.3xx

e) Login as root by

"sudo -s "

f) Brings up a text editor in SuperUser mode (which is necessary to edit system files)

" gksudo gedit /etc/modprobe.d/alsa-base "

g) Look for cluster of lines beginning with "options." If you have the line
" options snd-hda-intel model=default "

Change it to " options snd-hda-intel model=acer-aspire "

Save the file

h) Go at Home directory, right click and extract the file hda-verb-0.3.tar.gz

i) Now cd (change directory) to the hda-verb-0.3

" cd hda-verb "

j) compile the file with 
" make "

k) Copy it at /usr/local/bin type

" sudo cp hda-verb /usr/local/bin "

l) Edit /etc/rc.local by typing

" gksudo gedit /etc/rc.local "

m) This will bring up your text editor again, this script is empty by default, for our purposes we must add this line before the 
"exit line"

" /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2 "

You're finally done, reboot your machine and you should have sound card working.
it works with 2.6.27-10-generic kernel and 2.24.1 Gnome

thanks to all people who helped me to make this easy for us.
so i want to thank personaly:  
- plunder (Administrator) 
from the this [http://www.codecaucus.com/forum/viewtopic.php?id=13](http://www.codecaucus.com/forum/viewtopic.php?id=13)  forum witch is very good.

- CJay554 for this [http://ubuntuforums.org/showthread.php?t=921637](http://ubuntuforums.org/showthread.php?t=921637)
and for this [http://ubuntuforums.org/showthread.php?t=921637&highlight=acer+6920+sound&page=3#26](http://ubuntuforums.org/showthread.php?t=921637&highlight=acer+6920+sound&page=3#26)

thank you guys you are the best keep going for a free world without limits...

<< Software is like Sex it's better when it's  FREE >> open your minds up nikkpap.

Follow the rest to upgrade to Alsa 1.020 with BASS just do all the command on the terminal one by one... nikkpap again for all of you.

sudo apt-get -y install build-essential ncurses-dev gettext xmlto

sudo apt-get -y install linux-headers-`uname -r`

cd ~

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)

wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2)

wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2)

sudo mkdir -p /usr/src/alsa

cd /usr/src/alsa

sudo cp ~/alsa* .

sudo tar xjf alsa-driver*

sudo tar xjf alsa-lib*

sudo tar xjf alsa-utils*

cd alsa-driver*

sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)

sudo make

sudo make install

cd ../alsa-lib*

sudo ./configure

sudo make

sudo make install

cd ../alsa-utils*

sudo ./configure

sudo make

sudo make install

rm -f ~/alsa-driver*

rm -f ~/alsa-lib*

rm -f ~/alsa-utils*

sudo reboot

wget [ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz](ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz)

tar -xvmf hda-verb-0.3.tar.gz

cd hda-verb-0.3

make

sudo cp hda-verb /usr/local/bin

gksudo gedit /etc/rc.local

add this before the line with the word &#8220;exit&#8221;

/usr/local/bin/hda-verb /dev/snd/hwC0D0 0×15 SET_EAPD_BTLENABLE 2

sudo reboot

---

### Post by nikkpap on 2008-12-18
):p):p):p):p

---

### Post by lusephur on 2008-12-23
cheers, works like a charm.

---

### Post by mc6415 on 2009-01-01
Hi, thanks the guide worked and I have sound at long long last, but I still have a problem in that whenever I use it with headphones, I get sound out the speakers on the laptop and out of my headphones at the same time, is there anyway to stop this?

---

### Post by nikkpap on 2009-01-09
i dont know anything for that but i have a problem too..
i cant have sound from the hdmi plug to my lcd tv i dont know what to do...

---

### Post by CJay554 on 2009-01-11
@mc6415  Hey, are you using the aspire 6920? Jack sensing seems to work for most of us, maybe you didn't upgrade the right way, did u have OSS4 installed before you did the ALSA installation? 

A work-around is to right click on your volume applet (or u can make a shortcut to the volume control from applications > sound & video > volume control on your panel, then in there just mute/unmute whichever you are using (speaker/headphones) etc.

Nikk, the HDMI is a totally different driver, you might want to research such as my laptop did not come with the HDMI controller, find what model it is and google or post another thread describing your problem.

CHeeRs:popcorn:

---

### Post by CraigBray on 2009-02-02
I just did that whole tutorial and it didn't work, is there anything else i can do? Should i format and try it again?
Or could it be my version i'm running right now?

---

### Post by CraigBray on 2009-02-14
In addition to my prior post, i can't seem to get it to work....it's really getting to be a drag.

---

### Post by CJay554 on 2009-02-14
Craigbay:
Which laptop do you have? (6920/8920)
Which Distro do you have? (7.10/8.10/etc)
Have you tried other methods of installing other drivers/programs in order to try and get sound to work?

---

### Post by atarifreak on 2009-02-14
with this hda-verb i got real cool sound (bass), but its clipping now :-(

---

### Post by CraigBray on 2009-02-14
> **CJay554 said:**
> Craigbay:
Which laptop do you have? (6920/8920)
Which Distro do you have? (7.10/8.10/etc)
Have you tried other methods of installing other drivers/programs in order to try and get sound to work?

I was using 8.10 Intrepid. Now I'm gonna try again on 8.04 Hardy. I use an Acer 6920g Gemstone Blue. It has an intel centrino duo 2.0ghz t5750, 4gb ram, optiarc blu-ray player/dual layer dvd write, and a GeForce 9500m GS.
No i haven't tried many other methods, i used the package manager. I also manually installed everything found here in smaller chunks, and i changed the model to default, auto and acer-aspire. I've also removed all options and placed just the intel specific audio stuff i found on another thread. I've done it before i ran all ubuntu updates and also after.

---

### Post by CraigBray on 2009-02-16
News on it is the Makefile doesn't work on 8.04... anyone know if i can change it to do so?

---

### Post by CJay554 on 2009-02-17
do 

sudo apt-get install build-essential 

to get makefile working.

Anyway, do this as well:

lspci

and show us what you get

---

### Post by CraigBray on 2009-02-17
There it is:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0405 (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
08:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

I did the full tutorial now, and it's not working, is there anything more to do? Settings i need to change perhaps?

---

### Post by CJay554 on 2009-02-26
Hmm, interesting.. I have this:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

notice the (rev 03)

you seem to have rev 04

unless someone else has your revision and reports it to work then i dont think you have the same hardware as us

---

### Post by CraigBray on 2009-02-27
Well...that sucks :( Now i have to restore NTLDR, somehow.. lol. Acer sucks for providing discs.

---

### Post by CraigBray on 2009-03-28
I seem to have found a sensible fix. You need to bail on Alsa, and instal OSS4. Here is the guide.[https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")

---

### Post by jterrygr on 2009-07-22
*I seem to have found a sensible fix. You need to bail on Alsa, and instal OSS4. Here is the guide.[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)*

Thanks CraigBray! Newb user here. Was having multiple sound problems in Ubuntu 9.04. The above link did the trick. Appreciate it!

---

### Post by matmat07 on 2009-08-05
any hint for the hdmi sound output?

---

