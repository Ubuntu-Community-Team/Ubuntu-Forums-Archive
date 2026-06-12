---
title: "fiesty doesnt mount DVDs but mounts CDs (I have all codecs)"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by seshomaru samma on 2007-07-29
So here is the problem:
I have a Lenovo laptop running feisty. It has a cd-rw/dvd rom that I rarely use. Yesterday I wanted to browse some files on a Fedora DVD and feisty wouldn't see it. 
Here are the symptoms:
 *It automounts CDs
 *I can play videos/media from a DVD if I open VLC and tells it to open a file
 *When I put a DVD it makes a sound (like the DVD is spinning ) 
 *I usually have a "CD-ROM1" icon on nautilus, but when I put in a DVD a new icon appears "CD-RW/DVD-ROM Drive" . When I click on it I get "Unable to mount media ,there is probably no media"
 * I did install all the codecs ,including  libdvdcss2
here is the relevant fstab entry :
```
/dev/[COLOR="Red"]scd0[/COLOR]       /media/cdrom0   udf,iso9660 user,noauto     0       0
```
I find it strange that it is scd0 i expected it to be cdrom or hdc or something ,but i'm not sure what to change it to....

---

