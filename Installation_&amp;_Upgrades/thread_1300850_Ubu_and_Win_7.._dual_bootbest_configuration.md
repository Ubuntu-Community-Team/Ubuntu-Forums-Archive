---
title: "Ubu and Win 7.. dual boot/best configuration"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by nodnarb22 on 2009-10-25
Okay, so im building a new system with some good power to it, i7 920, ive been using Ubuntu 9.04 since release on my laptop and i love it for the most part. im wanting to put windows 7 on my new machine (already ordered) for use of the MCE connection to my xbox 360 and the dvr/pvr stuff associated with that. So my question is what is my best way to be able to use ubu and windows kind of inter connectedly . Im not sure if i want to do a windows install as my main and put ubu in a virtual machine on there or if i want to the opposite of ubu with win 7 in a virtual machine or if i want to dual boot them both. which is more of a hit to power win 7 as main and ubu in virtual or ubu as main and win as virtual.  IF i put win 7 in the virtual will i still be able to cash in on all the media center interactions with the 360? any insight would be great. i know i can dual boot but then it wont let me leave the win 7 copy up and running for the dvr purposes. IS it possible to have ubu and windows 7 installed separately and still access one while inside the other?   Any and all help ideas or thoughts are appreciated thanks.

---

### Post by Mark Phelps on 2009-10-25
> **nodnarb22 said:**
> Okay, so im building a new system with some good power to it, i7 920, ive been using Ubuntu 9.04 since release on my laptop and i love it for the most part. im wanting to put windows 7 on my new machine (already ordered) for use of the MCE connection to my xbox 360 and the dvr/pvr stuff associated with that. So my question is what is my best way to be able to use ubu and windows kind of inter connectedly . Im not sure if i want to do a windows install as my main and put ubu in a virtual machine on there or if i want to the opposite of ubu with win 7 in a virtual machine or if i want to dual boot them both. which is more of a hit to power win 7 as main and ubu in virtual or ubu as main and win as virtual. 
With Vista-vs-Ubuntu, this would have been an easy question to answer -- Ubuntu would have given by far the best performance.  But I run a multi-boot machine, and in my case, the Window  7 performance is as good, if not better, than Ubuntu 9.04 on the same hardware.  Haven't installed 9.10 yet, so don't have a comparison on that.  Either one is going to perform worse in a virtual environment, so if it were me, I'd use the virtual environment for the one for which performance mattered the least.

>  IF i put win 7 in the virtual will i still be able to cash in on all the media center interactions with the 360? 
Don't know.  My guess would be NO.  But, if this sort of compatibility is important, then install Windows 7 in native mode and Ubuntu in virtual.
> i know i can dual boot but then it wont let me leave the win 7 copy up and running for the dvr purposes. 
In a TRUE dual-boot situation, each OS in its own native partitions, only one OS is running at a time.
> IS it possible to have ubu and windows 7 installed separately and still access one while inside the other? 
Yes, but I would caution against having EITHER OS access the other OS's files in read/write mode.  Have seen too many instances where filesystem corruption happened as a result.  If you really want to share files, better approach is to create a shared NTFS partition.

---

### Post by doriard on 2009-10-26
If you don't want to dual boot, but want to run Windows inside of Ubuntu, you can install Virtualbox inside Ubuntu, and then install Windows XP (not Win 7 yet) in the Virtualbox.  Virtualbox is free VM software from Sun.  [www.virtualbox.org](www.virtualbox.org)

---

### Post by nodnarb22 on 2009-10-27
Thanks both, my only slight concern is my version of win 7 is an oem .. IF i happen to install a true dual boot setup like i have now, can i then later on put the same win 7 into a virtual on ubuntu? i mean its still technically on the same machine. I know that question may be better answered else where but i knot alot of people here are knowledgeable of both windows ubuntu and all things computer.

---

### Post by cwsnyder on 2009-10-28
To answer your specific question on whether you can install a virtual copy of Win 7 using the same license as the original, hardware install, the answer is NO.  You will have to re-activate Windows 7.  The virtual machine hardware is going to be different from the original hardware, and Windows 7 will notice and complain, making you reactivate.

---

### Post by Mark Phelps on 2009-10-29
Don't know if you're planning on having two instances of Windows 7 (one in native mode, one in a VM), but I read a post about someone who did that with Vista, and EVERY TIME they booted into the "other" installation, they had to reactivate!  The same thing happened when they figured out how to get their VM install to point to the native install.

Just passing along some info ...

---

