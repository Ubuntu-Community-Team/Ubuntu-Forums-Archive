---
title: "AVI won't play properly"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by david1212 on 2009-04-03
AVI won't play properly.

I installed and updated kubuntu 8.04.1 as listed below.

I try to play a avi file and it doesn't play correctly.
Sound is OK. Video is a series of orange strips. 
The machine is so slow to respond that I give up and use ctrl-alt-backspace
to quit X windows.


How installed:

-download and put kubuntu on a usb stick.
-cleanly install kubuntu on a freshly formated partition.
then:
clip from history:
    4  sudo apt-get install  smb4k komba2  kubuntu-restricted-extras  rar dvdrip transcode  kedit
    5  sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
    6  sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
    7  sudo apt-get install dvdrip transcode firefox xvid4conf pyneighborhood  mythbuntu-desktop
  114  sudo apt-get install w32codecs libdvdcss2


I have done this sort of thing to Ubuntu 8.10 and it worked. The reason I am doing this
to 8.04 is that it has a longer support period. This machine is for someone who may come
back to me two years later asking for one thing or another -- so long term supported
repositories are needed.

David

---

### Post by coffeecat on 2009-04-03
Since you've got the medibuntu repository enabled, install vlc and see if that copes better with your avi file(s) than whatever kubuntu uses as the default media player.

I've given up with Totem (which is what comes with Ubuntu/gnome) and always use vlc. While you're about it, get mplayer/kmplayer as well (it won't cost you anything :wink: ) and give that a try.

---

