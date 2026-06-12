---
title: "Install 8.10 on new machine stops with command line."
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by tburge on 2009-05-13
I am assembling a new desktop and installing 8.10.  I have purchased a DVD from Amazon, so I assume that  the install DVD is valid.  The bios is set to boot from the DVD drive and will pause for the Ubuntu menu.  When I select Install ...  it quickly displays the command line (initramfs) and does not seem to continue.  

I purchased a 1T HDD to use on this machine.  Is the install progressing and formatting the hdd?  1T would take some serious time?  The bios recognizes the hdd, therefore I think  that it is installed correctly.  

Am I missing something or is something broke?  

Thanks,

---

### Post by sir_nasty on 2009-05-13
can you boot off the cd just fine?  if so i'd try booting into the live cd then click the install icon and see if it acts any different....


also a quick search yielded this

[http://www200.pair.com/mecham/spam/waiting_for_root_file_system.html](http://www200.pair.com/mecham/spam/waiting_for_root_file_system.html)

---

### Post by tburge on 2009-05-13
I tried booting to run from the CD.  I still ended up with a BusyBox command line (thanks to the article that reminded me of busybox).  

Note, this hdd has never been formatted.  It's Brand New, out of the box.

---

### Post by sir_nasty on 2009-05-14
I'm guessing you bought the cd to avoid this but.... I've recently been playing with a few usb drives and installing from them... if that's an option I'd suggest downloading 9.04 and write it to a usb drive then install....

---

### Post by ozonehole on 2009-05-14
I think the answer to your problem is here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222176)

best regards,
Oz

---

### Post by tburge on 2009-05-14
Thanks Oz, that let me install.  Now it is reluctant to boot from hdd, so I need to re-read that thread some more.

Terry

---

