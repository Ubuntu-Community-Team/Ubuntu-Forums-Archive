---
title: "Thinkpad 770z Sound problem.  Cirrus Logic CS423x?"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by LieToPurify3 on 2008-03-10
I've looked at every single page I could find that had anything to do with configuring the thinkpad 770z or any Cirrus Logic CS423x card with any distro of linux, and I've come up with nothing.  On a site that tells me the specs of my laptop, it says the 770z uses the Cirrus Logic CS423x sound card, but the output of lspci gives me "Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear Sound Fusion Audio Accelerator] (rev 01)"  Ive read on some pages that sometimes linux mistakes the CS423x for the 4610/11.  But how can I be sure this is the problem?  I've also tried everything from this guide which uses a similar chip "http://ubuntuforums.org/showthread.php?t=282624".  Any ideas or help is GREATLY appreciated.  I've had this laptop for months and have gotten nowhere with the sound.  However, this is my first time using linux, and I've learned a lot by struggling with it lol.  Its dual booting DSL 4.2.5 and Xubuntu 7.10 right now.

---

### Post by SixedUp on 2008-03-11
Too long since I saw one of these to be sure, but I think the sound system is the same (or very similar to) the Thinkpad 600/600e series of machines.  You'll find that it has both a CS4610 and (I think) a CS4239.  I think the CS4239 is hung off the ISA bus (this machine was designed around the time that PCI was replacing ISA), which may explain why lspci isnt showing it.

Getting sound to work on Thinkpad 600's is notoriously difficult, and I suspect you'll be facing the same problems with the 770. Unfortunately I've not succeeded in getting sound to work on my old 600, so I can't help you much, beyond pointing you at the (often conflicting and out of date) information out on the web for the 600's that might well be applicable to your machine too.

Good luck.

---

### Post by LieToPurify3 on 2008-03-11
Yeah, it seems that everyone has problems with it.  I was hoping that instead of pointing to those old "fixes" that dont work with ubuntu, we could write a new 'how-to' on how to get the card working.  I'm sure someone here can help me!

---

### Post by wparker on 2008-05-08
I just signed up for the forum today and started looking for 770z info first thing.  I know zilch about linux, so far, but I did run across this website with a "how to" for sound on a 770e: [http://linux-laptop.net/hosted/xubuntu-thinkpad770e.html](http://linux-laptop.net/hosted/xubuntu-thinkpad770e.html). Have not yet attempted to see if it will work, I'm too busy trying to get my Broadband wireless card working.  

If you have any other info on running xubuntu or ubuntu on a 770z please contact me.

---

### Post by rcmayfld on 2008-06-09
this should solve your problem

[http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_some_ThinkPads](http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_some_ThinkPads)

rick

---

