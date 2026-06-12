---
title: "fedora to Ubuntu?"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by Utsukushii Tsubasa on 2009-06-02
alright. so i started off running Ubuntu on my laptop right? right. well when we put the desktop in i decided to try fedora. (i know, traitor!) anywho i want to switch back. i tried running a cd (wich works) on and it wouldnt install. can someone PLEASE PLEASE help me? i prefer Ubuntu to Fedora and i cant switch back ;_;

---

### Post by RedSingularity on 2009-06-02
What error comes up?

---

### Post by munky99999 on 2009-06-02
Can you simply livecd-install?

Can you not boot a live cd?
can you no overwrite the partition and start fresh?

In otherwords, where is the problem that you get?

---

### Post by Utsukushii Tsubasa on 2009-06-02
k. i tried to boot from live cd but when it ran through and said read error i didnt mind caring. that happened with my laptop, but then it said something else about SQUASHFS and i had never seen that before. then it started talking about kernel panic and stopped there. im not sure if that explains the problem or not. but i did try to boot from cd.

---

### Post by Niva on 2009-06-02
Run a media check on your cd, make sure it burned correctly.  If it hasn't then reburn it again.

I also had a really odd thing trying to install 8.10 a few months ago where on a laptop, if I was plugged into power during the install, I'd get read errors off the CD.  My best guess was that when the battery would kick in and start charging in the middle of the install the laser inensity of the cd-reader would dip a bit and miss a few bits.  I had to do the entire install on battery though I think I'm a total exception on this.

Good luck!

EDIT:  To run the media check you can see that off the main menu when you first boot, same place where you select to install Ubuntu.

---

### Post by Utsukushii Tsubasa on 2009-06-02
ill check the disk, but im running a desktop so the power SHOULDNG phase in and out. if i unplug it it dies:p.
if it turns out to be teh cd then i will have to find another cd since a dumbass at school took my flash.

---

### Post by Utsukushii Tsubasa on 2009-06-02
so i ran the disk check (and took a shower) and it ran clean. but this only happens when im already running a unix based os. last time i was trying to convert from Ubuntu to Windows and couldnt, this time its from fedora to Ubuntu. anywho it would at least show me the preview with the install option on the desktop when i was running windows. but i cant even load that. ill try to create a new live cd but idk if it will work.
so can anyone tell me how to make a live on fedora?

---

### Post by Niva on 2009-06-03
Live cd means you boot from it, not run it inside of Fedora.

Pop the CD in, make sure in your BIOS boot options are set to boot from cd player before it boots from HD.

---

