---
title: "Installation issues"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by thome.penguin on 2009-01-10
Maybe I should have posted this in the Noob section, but I figure since I've tried trouble shooting enough on my own, that I'm a little past that point.  

My wife's PC crashed when Service pack 3 came out.  It's a cheap 4 yr old eMachines she bought for her fr year of college, so there was no point in throwing money at it to reinstall xp (she lost her disk over time).  We just want a second computer for email and stuff when she uses mine for homework and what not.  I downloaded fedora for it, but somewhere along the way didn't burn the disk right with the boot.ini file or whatever.  So I broke down and bought (I know I know)ubuntu 8.04 off of Amazon.  I figured it would save me time and frustration knowing someone else did it right, considering the Fedora download took about 4 hrs.  So I tried to install it, but it would never go into the set up screen.  I later figured out, that SP3 took out the hard drive along the way.  So I got a used 40G from my brother who's a gamer.  So then I thought I was in business after the reformat.

Well then we determined that ubuntu didn't support the Fat32 or whatever, when the install didn't work.  I reformated again in the other format, and I still had problems. It will run off of the disk just fine, I just can't get it to install to the hard drive and boot and run off of that.  

I believe it somewhat starts to do so, because as the installations fail and I try to do it again, when I get to screen 4 of 7 it asks how I want to partition the disk, and the little bar graph seems to indicate that a portion is being used by ubuntu 8.04.  This is getting lengthy, I will post more text and photos soon.

---

### Post by susanw on 2009-01-10
I wonder if you can use GParted - available when running off the Hardy LiveCD, to find out how your disk is being used to get more off an idea of what your hard disk looks like - partitions:sizes, operating systems installed, swap partitions, ubuntu partition.

You'll probably then need more help than I can give but it's a start.

---

### Post by thome.penguin on 2009-01-10
I see have have to link to photos hosted elsewhere, so it may take some time for me because the site I was going to host them on currently is under construction.  I don't know if facebook will let me do this or not, but...

[IMG]http://photos-h.ak.fbcdn.net/photos-ak-snc1/v1950/139/93/17005133/n17005133_37742063_3687.jpg[/IMG]

---

### Post by namdung on 2009-01-10
Ubuntu or any other Linux distro doesn't use FAT32 or NTFS which is MS Windows specific. By default, Ubuntu uses *ext3*, hence there is no issue of disk fragmentation in Ubuntu.

If ur LiveCD is running fine than Ubuntu supports the hardware. If u want format the entire HDD, then select *Use entire hard disk* during partition step. This option will format the HDD to ext3 and also create a swap partition automatically.

Pls mention any specific issue. Screenshots and details will help.
[http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml)

The current version of Ubuntu Hardy Heron LTS is 8.04.1 and the next release 8.04.2 is on 22nd Jan.

PS: People actually buy Ubuntu DVD from Amazon!!!

---

### Post by thome.penguin on 2009-01-10
As the installation goes along, I think it sort of stalls out (I'm currently doing an installation, it's been about a month since I tried this when I got fed up), and gives me this screen:
[IMG]http://photos-a.ak.fbcdn.net/photos-ak-snc1/v1950/139/93/17005133/n17005133_37742064_4017.jpg[/IMG]

So the picture is from the last time around, I will double check and see if the same happens this time around.  I know it's hard to read, but try taking a picture of the screen on a 4-5yr old monitor.  I think it says: *The ext3 file system creation or partition #1 of SC1.01 [0.1.0](ada) failed* or something very close.

---

### Post by thome.penguin on 2009-01-10
Thanks, namdung...

That makes sense then, because that seems to be what that error box is telling me in my post above.  I thought at one point I did use the guided install, but that could have been long ago.  I guess I will cancel my current install and see what happens.

---

