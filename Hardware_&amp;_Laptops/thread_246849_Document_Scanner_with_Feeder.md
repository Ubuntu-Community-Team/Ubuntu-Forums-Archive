---
title: "Document Scanner with Feeder"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by Roman27 on 2006-08-29
Greetings!

I'm looking to try to go paperless at home and am looking for a good scanner that has an automatic document feeder (ADF) that is reliable and will last a while.  I have a whole file cabinet of stuff that I would like to scan in and store digitally.

I would like the scanner to have "Complete" support according to the sane-project.org website, or at least "Good" support.

Does anyone have any recommendations or personal experience with this?

---

### Post by mrojas73 on 2006-12-25
I am looking for the same thing.  Right now I have a desktop computer running windows with a Microtek 5950 scanner which I use for scanning all my bills and stuff.  I am ready to rebuild the system, but it will never see windows again since I am going ubuntu 100%.  Right now I am searching ebay for ADF scanner, so far the ones I have found are not compatible with linux or are way too expensive.

If you find one, please post here!

Thank you.

---

### Post by mujalan on 2007-05-01
I notice that your post was dated 8/29/06 so this response may be academic at this point.  I am going paperless at my office also.  I have just installed an HP Laserjet 3050 on Ubuntu 7.04.  It is a multi-function machine with an ADF scanner.  It works well with SANE or Kooka except that it puts each page into a different file.  I haven't learned a way yet to get it to put a group of pages into one file.  That is something I need.

I also have a Fujitsu ScanSnap which works wonderfully with windows and is supposed to work with Linux as well, but I haven't worked on that much at this point.

Best wishes.  I hope you have already found your solution.

Sonny

---

### Post by Roman27 on 2007-05-01
Thank you very much for posting.

Actually, I haven't found a solution yet.  I'll take a look at the HP LJ 3050.  I would like to have each scan job, no matter how many pages, go into the same PDF file.  But, it would be nice to at least have a working ADF scanner at this point.

Let me know if you like the Fujitsu better.  And thanks again for posting.

---

### Post by mujalan on 2007-05-02
Got it to work!!!!  Xsane will now scan with the adf on the HP 3050 and place several pages into a pdf file! I just had not clicked the right spot.  Speed is important in my business and my first efforts were abysmally slow.  Now it comes through at an acceptable speed for me at least.  Not as fast as the Fujitsu ScanSnap but enough for my needs.  I don't know if it would fulfil your needs, just that it is working for me.

Best wishes
Sonny

---

### Post by snobel on 2007-05-10
Hi there,

*looks around* wow, this forum is even bigger than it looked from the outside...

You have probably found it already but just in case I thought i'd mention [gscan2pdf]("http://ubuntuforums.org/showthread.php?t=62636&page=34"), a gui for scanning multiple pages to pdf or tiff. It works wonderfully with my fujitsu scansnap fi-5110eox2. 

Strangely though: I upgraded from edgy to feisty, and now the scanner turns itself off after about 10 seconds?! :confused: If I boot on the older kernel from the edgy install it still works. But if anybody reads this and thinks "ah, he needs to use version x of packet y" then *please* post...

---

