---
title: "Extend logical partition to include usb stick or usb hhd"
date: 2015-09-03
forum: Hardware
---

### Post by wendigo2 on 2015-09-03
Hi all,

This is my situation:

Chromebox running a dual boot with Chrome OS and Ubuntu. I only need Ubuntu which I originally gave 7gb of the total of 16gb. Running Kodi for streaming. Have a slow internet connection at ca. 3Mbit/s. I needed to enable zero cache from within Kodi to allow it to cache more (ie caching to the hdd instead of RAM). Problem is: when I let it run for a few hours to buffer a blu ray rip for example it runs out of hhd space and hits the wall, causing it to crash.

So:

I need to extend the single partition I have to include a 64gb usb stick or a 2tb HDD which I also have laying around somewhere. Can I do this without fully reinstalling Ubuntu and Kodi and ruining all my settings etc, or am I screwed? If anyone happens to know of a way to tell Kodi to cache in another location, that would be ideal of course, but I figure it wll need to be an OS thing. I am a linux noob btw.

Thanks, Jim

---

### Post by dino99 on 2015-09-03
i've no clue about kodi, but it might allow to set an external path as you need; even an OS can stand on a stick. So read the kodi wiki/howto, and glance to its settings/menu

---

### Post by wendigo2 on 2015-09-03
Ok I got this from another forum...like I say, I'm a noob, but it seems to me here he's created a new directory with the path on his usb stick to contain the temp folder of Kodi:

cd ~/.kodi/
sudo mkdir /media/USBDISK/kodi/temp
sudo cp -r temp/. /media/USBDISK/kodi/temp/
sudo chown -R pi:pi /media/USBDISK/kodi/.
sudo mv temp temp-backup
sudo ln -s /media/USBDISK/kodi/temp temp


Is this something like what you mean? It's a symbolic link I think. What If I reinstalled kodi on an external usb hdd? Would that just create all the folders on that drive and therefore automatically cache to the larger drive? How would I install Kodi on the external drive through Ubuntu? (I'm a Windows user...I know, shameful)

---

