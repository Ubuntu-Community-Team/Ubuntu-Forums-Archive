---
title: "problem installing vlc"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by sameerb1 on 2009-03-02
I have been trying to install any software in my ubuntu for past 3 days leaving my work on the work desk.

i dont have internet connection on my laptop (with ubuntu) so i cant use apt-get. 

I want to watch xvid's on my ubuntu. i tried to install mplayer and vlc, mplayer gives me no permission error while vlc gives me cannot find lglu error. i have libglu.so.1 in my library. 

can someone help me please? i already configured mesa on my ubuntu. please let me know how can i watch avi(xvid) files on my ubuntu???

p.s. i already installed xvid on ubuntu but dunno how it will patch with the default ubuntu movie player? i have ubuntu 8.10

---

### Post by Partyboi2 on 2009-03-03
To install vlc on ubuntu without Internet you will need to satisfy the dependencies which are the ones listed [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/intrepid/vlc") with a red dot next to them.
Another easier way to install packages without a Internet connection is to use something like [[COLOR=Blue]keryx[/COLOR]]("http://keryx.betaserver.org/").

---

### Post by sameerb1 on 2009-03-03
okay...i will download all the red dots...but when i click one red dot it takes me to another folder with other red dots...so do i need to download all those red dots until i reach to a folder deep inside? or do i just download the external red dots? i hope you understand my question...

if i get internet connection (which i will at home in 15 days)...will i still need to download all those red dots?

if i download keryx and install vlc with that, will i still need to download the red dots?

---

### Post by EXCiD3 on 2009-03-03
> **sameerb1 said:**
> if i get internet connection (which i will at home in 15 days)...will i still need to download all those red dots?

if i download keryx and install vlc with that, will i still need to download the red dots?

If you get an internet connection and install VLC, everything will be taken care of for you. Same thing goes with Keryx. If you create a project using Keryx, go to another computer and select VLC to download it will take care of all those "red dots" which are packages that VLC depends on. Keryx will download everything you need and then you can go and install them when you get back home. :)

---

