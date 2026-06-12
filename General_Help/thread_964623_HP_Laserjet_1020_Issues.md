---
title: "HP Laserjet 1020 Issues"
date: 2008-10-31
forum: General Help
---

### Post by SuperZero on 2008-10-31
On 8.04, after running hp-setup, the printer worked like a charm.

After doing a fresh install of Intrepid, printer fails to work even after running hp-setup. Recognized, print queue is there, but never actually prints. Bizarre.

Ran sudo hp-check and quite a few errors came up...

One of my gripes with Intrepid so far, along with intermittent disconnects on an ethernet connection and dysfunctional webcam support...

Advice?

---

### Post by mdurham on 2008-10-31
are you using a 64 bit cpu? It works for me on 32 bit Intrepid but not 64 Intrepid.

---

### Post by spiderbatdad on 2008-10-31
webcam support is being worked on. Some temp work-arounds exist, but the fixes don't work for everyone. [https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918) 
Try launchpad: [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/246475](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/246475)
and maybe search other reports as well...if the problems persists, consider reporting it.

---

### Post by mdurham on 2008-10-31
> **spiderbatdad said:**
> webcam support is being worked on. Some temp work-arounds exist, but the fixes don't work for everyone. Try launchpad: [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/246475](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/246475)
and maybe search other reports as well...if the problems persists, consider reporting it.

spiderbatdad, This is about a printer "HP Laserjet 1020 Issues" not a webcam.

SuperZero, I correct what I said in my prev post, it now doesn't work in either 32 or 64. It was working on 32 a few days ago. Ah well, that's progress for you!
Cheers, Mike

---

### Post by SuperZero on 2008-10-31
Progress is such a fickle mistress.

Ah well, thanks anyway. Six more months until 9.04!

---

### Post by mistseeker on 2008-10-31
Same problem here, after an upgrade to 8.10 on an Acer Aspire One.
I have faith in open source though, I'm sure it will be fixed soon.

---

### Post by mdurham on 2008-10-31
I followed spiderbatdad's link to the bug report and followed the instructions there and what do you know? My 1020 now prints again.

link: [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/246475]("https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/246475")
> To fix it:
1) Install hplip-gui: sudo apt-get install hplip-gui
2) Remove/Delete your current printer setup in System > Administration > Printing
3) Set up the printer again: sudo hp-setup
(It's mostly next > next > next - Be sure to have internet connection available)
4) Make sure the username is in lpadmin and scanner groups:
sudo adduser $USER lpadmin
sudo adduser $USER scanner
5) After you've done all this, switch off the printer, reboot your machine and switch on the printer once more.
It should be working now
Thanks spiderbatdad

---

### Post by SuperZero on 2008-10-31
That worked for me! Without having to restart or anything. I think installing hplip-gui did the trick, as it made me download other dependencies I think I may have been lacking initially. Thank you very much, I consider this solved.

---

### Post by sahmed001 on 2008-11-13
When I run HP-setup it works. Prints the test page. Prints pages. 
Then the next time I restart, it refuses to print again. I have to go through the damn setup every time I want to print. 

Worked fine in Hardy. Even had it shared with Samba.

---

### Post by mdurham on 2008-11-13
> **sahmed001 said:**
> When I run HP-setup it works. Prints the test page. Prints pages. 
Then the next time I restart, it refuses to print again. I have to go through the damn setup every time I want to print. 

Worked fine in Hardy. Even had it shared with Samba.

Look at System->Administration->Printing right-click on the printer icon and make sure that it's enabled. If I boot without the printer turned on, it's always disabled on my system.
Cheers, Mike

---

### Post by sahmed001 on 2008-11-13
> **mdurham said:**
> Look at System->Administration->Printing right-click on the printer icon and make sure that it's enabled. If I boot without the printer turned on, it's always disabled on my system.
Cheers, Mike


O.K. I feel like a moron, but thats what community is all about right :) Anyway, I actually booted with the printer turned off this time, it was still disabled. Any way to make it enabled on boot up.

---

### Post by mdurham on 2008-11-13
> **sahmed001 said:**
> Anyway, I actually booted with the printer turned off this time, it was still disabled. Any way to make it enabled on boot up.

I 'think' you meant "turned ON" didn't you? Anyway, I too wish it would stay enabled, I've no idea why it doesn't. If you find out let me know.
Cheers, Mike

---

### Post by cabo on 2008-11-13
put this code on a text editor:
|||||||||||||||||||||||||||||||||||||||||||||||||||||
clear
echo
echo Instalador HP-1000 HP-1005 HP-1018 HP-1020
echo

sudo apt-get install build-essential
echo Descargando datos............
echo
wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
tar zxf foo2zjs.tar.gz
cd foo2zjs
make
clear
echo Introduce una opcion:
echo 1--HP-1000
echo 2--HP-1005
echo 3--HP-1018
echo 4--HP-1020
read var
if [ $var -eq 1 ]
then ./getweb 1000
fi
if [ $var -eq 2 ]
then ./getweb 1005
fi
if [ $var -eq 3 ]
then ./getweb 1018
fi
if [ $var -eq 4 ]
then ./getweb 1020
fi
if [ $var -eq 0 ]
then exit
fi
echo Descargando datos............
sudo make install
sudo make install-hotplug
sudo make cups

sudo /etc/init.d/cupsys restart

clear

echo Abre el gestor de impresoras, configurala y disfruta.....
exit
||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||| 
, then save it like a .js, then open a terminal and go to the place were the .js is, and put this:
./(TheNameOfTheFile).js

---

### Post by mdurham on 2008-11-13
Thanks cabo, I had completely forgotten about the hot-plug stuff. 
Cheers, Mike

---

### Post by morphodone on 2008-11-16
> **mdurham said:**
> I followed spiderbatdad's link to the bug report and followed the instructions there and what do you know? My 1020 now prints again.

link: [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/246475]("https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/246475")

Thanks spiderbatdad

Thanks for this.

I think I will be buying Brother printers from now on.  My ubuntu box picked up the Brother printer I had installed in my iMac.  

And why do I have another laser printer?  Because the HP printer wouldn't work with the iMac.  I'm lucky I got the HP to work with Ubuntu at all.  I guess HP wants me to use Windows.  So no more HP printers for me!

---

### Post by TKoorn on 2008-11-26
My Ubuntu won't boot if the printer is on. It hangs on a bunch of USB errors it keeps on saying error -110 and Unable to enumerate USB devices for HUB 6 ore something like that. As soon as I switch of the 1018 it boots normally.

---

### Post by BewareOfDog on 2009-01-05
That worked for me too. Finally able to print!

---

