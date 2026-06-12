---
title: "Video Drivers finding issues"
date: 2010-01-04
forum: Hardware
---

### Post by Aevum on 2010-01-04
Greetings people, I know you might have seen thousands of these help-request threads for drivers but oh well, I'm gonna explain my issue real quick:

I just yesterday bought a new Netbook: Packard Bell Dot m and I decided to install Ubuntu Karmic Coala as I used to have on the old PC, I downloaded again the file yesterday, installed and made all the possible updates in the Update Manager. Ubuntu doesn't seem to find my Graphic Card I guess, I didn't find any information on the box about which graphic card I was using but I found on the net it was a GMA 500 most probably, though I can't find any useful method to get my video card working and that's getting me kind of annoyed.

I would be really thankful to anyone who could post here a working method for me to try, please, explain step after step if you do that because I'm not that much expert at all.
Thanks for reading

-Max

---

### Post by Aevum on 2010-01-04
I think I got something more.. I saw some Poulsbo drivers in the Synaptic package managers so I decided to try, I found the poulso-driver-3d and I tried to install it but it said I needed to install the 2d version first, so as soon as I tried to install the Poulsbo-Driver-2d I got a similar errpr saying that that 2d driver was depending from another file called "xserver-xorg-video-psb" which actually isn't present in the package manager thingy, I looked it up over the internet and I found some .gz files which I downloaded trying to open them with the archive manager but.. After I clicked on the link of a file like this "[xserver-xorg-video-psb_0.2.1.orig.tar.gz]("https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-video-psb_0.2.1.orig.tar.gz")" I did "Open with: Archive Manager (Default) and what I got is:

/tmp/xserver-xorg-video-psb_0.2.1.orig.tar-3.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences

Help please :S

[IMG]http://i46.tinypic.com/2ldk3nt.png[/IMG]
Folder of the file I need to install


UPDATE! I managed to unpack that .gz file and now I need to install it, kind of hard to me.. would use some infos, it's about installing the install.sh thing isn't it?
I just hope this will turn out as the right one at least

I called the folder aa in order to get it easier

cd home/max/scrivania/aa
bash: cd: home/max/musica: No such file or directory

what's wrong?

---

