---
title: "WLAN on Amilo L1310G in Ubuntu 10.04"
date: 2010-07-14
forum: Hardware
---

### Post by dmvanloon on 2010-07-14
Untill recently I've been using Ubuntu 8.04 Hardy Heron on my Fujitsu Siemens Amilo L1310G because anything beyond that release failed to work with my wireless adapter, which is an Atheros AR2413 802.11bg NIC. Despite endless googling and trying out supposed fixes, nothing ever seemed to work, untill I tried the very thing that worked on 8.04. Be it with a minor change.

If the fsaa1655g-fix in [this old article]("https://wiki.ubuntu.com/LaptopTestingTeam/Old/FujitsuAmiloL1310G") worked for you in Ubuntu 8.04 Hardy Heron, the following should work for you in Ubuntu 10.04 Lucid Lynx.



1. Create a new folder: ~/Downloads/fsaa1655g

2. Download the [tarball]("http://www.marvec.org/amilo/fsaa1655g-kernel-2.6.26.tar.bz2") and untar in the said folder

3. Navigate to said folder via terminal:
*cd ~/Downloads/fsaa1655g*

4. Now install the modules via terminal:
*make && sudo make install*

5. Open (what I think is) your former "options"-file:
*sudo gedit /etc/modprobe.d/alsa-base.conf*

6. Scroll down untill you find the following line: "# Prevent abnormal drivers from grabbing index 0". You should find some lines that start with "options". Now add the following:
[B]options fsaa1655g radio=1
options ath_pci rfkill=0[/B]
... and close the window.

7. Now we'll add the module so it will load at startup, again using a terminal:
*sudo gedit /etc/modules*

8. At the end of the file, add the following:
**fsaa1655g**
... and close the window.



Restart your machine and you should be able to use your laptop perfectly.

---

### Post by sokolic on 2010-08-07
Thanks, worked like a charm! Am finally able to roam around the house with my laptop.

---

### Post by Giovanni52 on 2010-12-21
Works perfect in 10.10 as well. A VERY BIG THANK YOU!! // Johan.

---

### Post by Chasalin on 2011-08-13
The Atheros seems to work out of the box on 11.04: it detects networks, although the LED doesn't light up.
It doesn't connect however...

So I tried this solution.

Status: works on 11.04

and the LED lights up :)

THANKS!

---

### Post by blackpear1477 on 2012-10-21
The Atheros seems to work on 12.10.
It also detects networks but the LED doesn't light up & 
doesn't connect...
However,I tried this solution and it works.

Status: works on 12.10.
Plus the LED lights up. 

I made the post here for those who stil have an Amilo L1310G.
I am glad that Ubuntu works.

thanx for all the works on this great OS.

---

### Post by wildmanne39 on 2012-10-21
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

