---
title: "200gb USB 2.0 problems..."
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by sesty on 2006-02-18
Hey all,
I'm pretty much newb when it comes to linux so please excuse any dumb questions...

I'm having a problem with my External USB2 Hard Drive 200gb:

when i plug it in (i'm sure it isn't the USB1.1 port) there are no problems with mounting (all completes automatically -- thank you ubuntu!!) but when i come to access the music folder (14,400 files using 55.8gb), the performance drops considerably and the mouse becomes unresponsive and starts jumping all over the place. Trying to play an mp3 produces jerky music as well. 

Any ideas??


Oh also the sound output is REALLY REALLY quiet. I will ask that in another thread, but if anyone knows "off-hand" it would be appreciated (thought there was no sound at all at first. A friend of mine suggested an ALSA problem??)....

Many thanks,
Sesty

---

### Post by StefanoCole on 2006-02-20
I was just wondering if the file system could be the problem. Is it fat32? It is only a guess, but maybe if it is a lot fragmented it could give some problems.

Stefano

---

### Post by sesty on 2006-02-20
no it is NTFS, when I hotplug and it is auto mounted -- no problem
the jerky behaviour only arises when i go into the music directory which (contained in various folders) has 14,400 files... is it just too many files for ubuntu to handle??
(i doubt this very much as ubuntu seems to be the best thing since computers came to be) but there is not the same response as other folders (for example, thousands of digicam pics-- no jerky) its just the music...

i'd like to get this sorted before i try and work out why the sound is messing about or is it part of the same problem??

---

### Post by sesty on 2006-02-20
any ideas on this one?
is this thread in the right place?
do i need to install or modify something which will handle many many files or am i just gonna have to not listen to music when in ubuntu? cuz that would kick me back to XP and i really don't wanna use that cr@p for much longer...

---

### Post by schatz on 2006-02-26
Have you found a solution?
I'm facing similar problems with a 300GB USB disk. Ubuntu does not mount it correctly autoamtically. I changed the /etc/fstab, this has solved the mounting problem, however when I try to access the drive the answer times are very strange. Sometimes ls reponds immediatelly, sometimes it takes 10 to 20 seconds! Still waiting for a solution...

---

