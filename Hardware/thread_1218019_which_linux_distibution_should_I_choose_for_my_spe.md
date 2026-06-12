---
title: "which linux distibution should I choose for my spec?"
date: 2009-07-20
forum: Hardware
---

### Post by acw on 2009-07-20
I am currently running WinXP Pro with most recent updates. It generally runs ok, though some graphics can be a bit slow, e.g. running more than one web page with flash banner ads or occasional games. I have been thinking of setting up a dual boot system for years (maybe even ditch Microsoft eventually), just never got aroung to it! 
 
I have been running a self build for about 8 or 9 years - basic spec is:
Asus CUV4X-E m'board with PIII 1GHz
64mb AGP 2x/4x graphics card
1.5GHz RAM PC133
some basic cheap soundcard
 
I now have a new 160GB HDD, which I intended to basically divide into two, reloading WinXP on one partition (I am the household geek open to switching completely, but need MS for other users) and a linux system on the other. My initial thoughts were 100GB for MS, 60GB for linux (based on assumption that windows is generally hungrier). That drive will be primarily OS, programmes and other software. I have other drives that I intend to use for personal files, etc. I have also read that linux sets up a swap partition (a bit like extra RAM???). Does this have any implications for my partitioning?
 
I have just tried a couple of 'linux chooser' tests and they both suggested SuSE. Next best suggestions were ubuntu, kubuntu, mandriva and linux mint but they were scored lower because it thought they might run a bit slow with my spec. The test questions were fairly basic and I suspect it thinks that because I said my system was 'more than a few years old' and because it asked if I had a 64-bit processor (I didn't know but looked it up and wiki said that PIII is 32-bit).
 
So three basic questions: 
1. will ubuntu run slow on my system or will it be fine?
2. (possibly a silly question but...) does anyone recommend an alternative - SuSE or another?
3. any suggestions about partition sizes?
 
Look forward to hearing from you :grin:

---

### Post by DEagleson on 2009-07-20
If your unsure if Ubuntu will run comfy on your system you could give Xubuntu a go.

I got a old AMD Athlon XP based computer with 1.5 GB DDR ram and a Nvidia Geforce FX 5600 AGP card.
It runs Xubuntu 9.04 quite nicely.

---

### Post by willmsbrt1 on 2009-07-20
I would say ubuntu 8.04 which is a long term support , it will run fine in 20 g or less , updates are stable and not alot of downloading ( updates ) to get it up and running , if you want a quicker system 9.04 and firefox is quite fast , what do you intend to use the partition for would be a better question , surfing , games ??? 

I dont have alot of use with kubuntu or edubuntu but 8.04 lts would be my choise as a stable platform to start with and possibly might make a few converts on the way

---

### Post by acw on 2009-07-20
Thanks, that is really helpful. 
 
It is mainly my graphics that I think could let it down. I have been looking at the possibility of replacing my card but not sure if I can still get the right type of AGP card for my board.
 
I was just flicking through the free ubuntu pocket guide and that suggested downloading the 32-bit version anyway, as the 64-bit could have some glitches (although it looks as though 8.10 was the latest available at the time it was written so they may have been ironed out since).
 
I keep coming back to the fact that XP runs acceptably on my system, and questioning whether ubuntu really would be (too) slow on my system. Just how different is Xubuntu from Ubuntu? If I find that Xubuntu works well, would I have to do a complete reinstallation if I then wanted to try Ubuntu?

---

### Post by acw on 2009-07-20
Hi Willmsbrt1,
 
I usually have 2 HDDs running on my system, I try to keep one for system and one for personal stuff wherever possible (and last year I was glad I had got into that habit when I turned power off a split second before XP had shut down - lost my entire OS and a load of email stuff, but all the personal files on the separate drive were fine -phew!).
 
Currently I have a 250GB drive that is being thoroughly underused, with my OS etc. in a 50GB partition, but the rest of it I never got around to sorting out. My 40GB drive is now packed to bursting with music, photos, etc.
 
My intention is to put two partitions on my new 160GB drive - one for XP, one for linux. My thinking was that I would then slice up the 250GB for perhaps music, photos and separate drives for (2) different users. Possibly. It's a work in progress! My question about partitions was really about suggestions for what to allocate for each OS.

---

### Post by AndyCee on 2009-07-20
Ubuntu should run fine, but if you don't mind the different apps available, try Xubuntu.

Xubuntu has a lightweight desktop environment, XFCE (instead of Gnome). The applications that come with it use less memory, but are often less powerful.

If you really want, install Ubuntu and if it's a bit slow, you could install "Xubuntu-desktop", which would install Xubuntu with Ubuntu. Log in choosing "XFCE" in the options button.

I ran full Ubuntu 7.10 on a PIII 1.7 GHz machine, and it was fine. I just wouldn't try to run heavy graphics stuff like compiz. And it should be fine if XP will run on it.

EDIT: 20Gig should be more than enough, if you store your big files on the windows partition. My Ubuntu partition is 20Gig( of which Ubuntu uses 4.9), all my personal files are on a seperate partition.

Definitely stick with 32 bit for now. Linux doesn't handle 32/64 bit programs the same way Windows does.

---

### Post by acw on 2009-07-20
Thanks, AndyCee, that's sounds like a plan! I was going to dangle my new HDD in for a while, to load up the OSes as I want them before full movement of all my files, so my old system will be available to me for as long as I want it (just got to keep swapping IDE cables!).
 
So, I'm tempted to try the Ubuntu and give it a whirl, as you suggest. My understanding of what you were saying is that it is easy enough to go for the best but work backwards if there are problems, rather than having to repeatedly install different OSes until I find one that works(?)

---

### Post by DEagleson on 2009-07-20
And remember that a Intel Pentium 3 does'ent even support x64.

---

### Post by AndyCee on 2009-07-21
> **acw said:**
> Thanks, AndyCee, that's sounds like a plan! I was going to dangle my new HDD in for a while, to load up the OSes as I want them before full movement of all my files, so my old system will be available to me for as long as I want it (just got to keep swapping IDE cables!).
 
So, I'm tempted to try the Ubuntu and give it a whirl, as you suggest. My understanding of what you were saying is that it is easy enough to go for the best but work backwards if there are problems, rather than having to repeatedly install different OSes until I find one that works(?)

I wouldn't say "go backwards", as both would be installed together. If you try Ubuntu first, then install the Xubuntu-desktop package, you'll still have a full Ubuntu install taking up room on your HD. I don't know of a simple way to cleanly remove the full Ubuntu install without simply re-installing.

Having said that, it's a 20-minute process to install either Ubuntu or Xubuntu. And if you have a USB disk, you can even use USB installer to avoid having to burn a CD.

---

### Post by acw on 2009-07-21
> **AndyCee said:**
> I wouldn't say "go backwards", as both would be installed together. If you try Ubuntu first, then install the Xubuntu-desktop package, you'll still have a full Ubuntu install taking up room on your HD. I don't know of a simple way to cleanly remove the full Ubuntu install without simply re-installing.
 
Having said that, it's a 20-minute process to install either Ubuntu or Xubuntu. And if you have a USB disk, you can even use USB installer to avoid having to burn a CD.
 
Yeah, I guess I just meant I could aim high and it would be easy enough to change to a lesser desktop if necessary, rather than trying the low one first, then reloading the better one if all seems well. With the available HDD space, it shouldn't be a problem having stuff I don't need on there.
 
Thanks

---

