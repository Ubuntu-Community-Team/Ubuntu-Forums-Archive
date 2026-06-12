---
title: "Blu Ray Drive not showing up in Ubuntu 11.04"
date: 2011-06-04
forum: Hardware
---

### Post by Rocky1980 on 2011-06-04
Hi all,

I have just build myself a new machine :p but I am having a real issue with my new Bluray Drive. MY new machine is the following spec 

ASUS P8H61-M Rev 3.0 MB
4 Gig DDR3 RAM 
1TG SATA HD
Intel i5 3.3ghz CPU
LG B10 Blu-Ray Rewriter


My issues started when I first put the machine together and none off my ubuntu live CD's would work they would get so far them throw up some error. I ended up installing Xp then making a LIVE USB and using that to install 11.04. The blu ray drive worked fine in windows but does not show up at all in ubuntu. Any ideas please ???


Regards 

Rocky

---

### Post by dFlyer on 2011-06-04
You might want to check this link to see if it will help. I know for a long time Blu Ray wouldn't work with linux. Not sure if that has changes but did find this link with a google search.

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---

### Post by Rocky1980 on 2011-06-04
Thanks for the link, but that inly really talks about play a blu ray my drive does not show up in ubuntu at all

---

### Post by gordintoronto on 2011-06-04
Did you mean to say you have this blu-ray drive: LG BH10LS30?

You say, "my drive does not show up in ubuntu at all." Where do you expect it to show up?

Can you run Accessories/terminal, then enter these two commands:
sudo lshw > myconfig.txt
gedit myconfig.txt

Now search for dvd, and if it's not found, search for SATA and look at what follows it.

If you put a CD in the drive, does it appear on your desktop?

Are you using Unity or Gnome?

---

