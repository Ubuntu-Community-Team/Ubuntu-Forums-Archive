---
title: "Help with partition on dual boot"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by DougieFresh4U on 2009-02-18
I _**had**_ a dual boot with Windows 7 and Intrepid. I have a 320 GB hard drive and I had it set 50/50 when I set up dual boot. All was ok until I wanted to up Intrepid to Jaunty (I have Jaunty running on my other machine which is Intel and this machine is AMD) Well Upgrade failed miserable. (I went the "change soure list method", which has NEVER failed me in 3 years of upgrading) Machine through all kinds of fits and would not boot. Just dumped me into a shell with login at the top. some where during the upgrade network manager seemed to have been taken out and did not work so I lost connection to finish upgrade
Now that I have gone through my little 'rant'. When I put in my Intrepid cd and I get to the partitioner part it does not show my Windows 7. It shows like 5% 'orange' and 95% gray Ubuntu Intrepid. I am not sure how to proceed from there as I don't want to erase Windows 7, nightmare installing that as wireless driver was not included and had to install driver via USB flash.
Can some one please give me a clue as to what I am looking for in the partition part of install?
Sorry for the long ranting post!

---

### Post by taurus on 2009-02-18
Post a screenshot of gparted from the LiveCD.

---

### Post by DougieFresh4U on 2009-02-18
Good eve, taurus
here is the screen shot, but when I was trying install the partition didn't look like that and I wish there was a way to show the partition from trying to install

---

### Post by DougieFresh4U on 2009-02-19
ok, from the posted screen shot how do I save my windows 7 install and get rid of ubuntu and use that space to installjaunty on. I kind of want to keep it 50/50, half windows and half for jaunty. I know that I don't need that much space but I am trying to keep it simple and I have Intrepid on my other machine
Please, help is needed real bad.

---

### Post by DougieFresh4U on 2009-02-19
I seemed to have played the guessing game and got it right, I mean I was overwhelmed with replies, I didn't know which to choose!!
 I just went with the "Manual' in partitions and deleted sda6-ext3 (something like that) and left the swap alone, used the 'free' space from deleted partition, chose '/' for mount (or was it'\') but any ways continued on with install and 15 minutes later, up and running!! 
I ended up with hard drive split in half, first half stayed Windows 7 and other half Ubuntu (320GB Hard Drive) So plenty of space for each, and install of Jaunty Alpha 4 went smooth and no 'bitchin' from machine.
All have a nice day.

---

