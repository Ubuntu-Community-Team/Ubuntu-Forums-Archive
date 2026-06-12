---
title: "Driver for internal SD Card Reader with Realtek RTS5250"
date: 2020-08-16
forum: Hardware
---

### Post by pmaff on 2020-08-16
I have a MSI Laptop MSI GE63 7RD. Everything works fine under Ubuntu 18.04 LTS. But I had no luck in getting the internal SD Card reader to work with Ubuntu.  It works with Windows 10.  Hardware seems to be known to Ubuntu: lspci | grep 5250 04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5250 PCI Express Card Reader (rev 01)  I was searching internet for Linux driver and found only some pages for the RTS5229, I tried this but of course this does not work for the 5250.  Can you point me to the sources for the driver for the RTS5250 PCI Express Card Reader? Does this internal card reader work with Ubuntu 20.04 LTS?  Thanks in advance

---

### Post by crip720 on 2020-08-16
One link you might try.  [http://forums.debian.net/viewtopic.php?f=7&t=140808](http://forums.debian.net/viewtopic.php?f=7&t=140808)  there are others.

---

### Post by pmaff on 2020-08-18
> **crip720 said:**
> One link you might try.  [http://forums.debian.net/viewtopic.php?f=7&t=140808](http://forums.debian.net/viewtopic.php?f=7&t=140808)  there are others.  
Thanks. I know this page already. 

"I made a "workaround" by buying an USB 3.1 SD card reader that works under Linux (Transcend TS-RDF5K)." shows that he also did not find a permanent solution. 

I also have a working card reader but I still would like to get the internal hardware working with Ubuntu the same way as it is working with Windows 10. 

Does anybody know, if Ubuntu 20.04 LTS is solving this issue? 

 Thanks in advance 
Pete

---

### Post by tea for one on 2020-08-18
> **pmaff said:**
> Does this internal card reader work with Ubuntu 20.04 LTS?

Is there a reason why you cannot download the Ubuntu 20.04 image, prepare a bootable usb device and give it a spin?

I can confirm that a similar Realtek (micro) card reader RTS522A PCI Express functions as expected with Ubuntu 20.04.

By the way, have a look at this thread for an unusual suggestion:-

[https://ubuntuforums.org/showthread.php?t=2448747](https://ubuntuforums.org/showthread.php?t=2448747)

---

### Post by pmaff on 2020-08-21
> **tea for one said:**
> Is there a reason why you cannot download the Ubuntu 20.04 image, prepare a bootable usb device and give it a spin?  I can confirm that a similar Realtek (micro) card reader RTS522A PCI Express functions as expected with Ubuntu 20.04.  By the way, have a look at this thread for an unusual suggestion:-  [https://ubuntuforums.org/showthread.php?t=2448747](https://ubuntuforums.org/showthread.php?t=2448747)  

Thanks for the pointer. 

@20.04 : I had the hope that possibly someone already has experienced success with 20.04 and Realtek RTS5250. ;-)

---

### Post by pmaff on 2020-08-30
> **tea for one said:**
> Is there a reason why you cannot download the Ubuntu 20.04 image, prepare a bootable usb device and give it a spin?  I can confirm that a similar Realtek (micro) card reader RTS522A PCI Express functions as expected with Ubuntu 20.04.  By the way, have a look at this thread for an unusual suggestion:-  [https://ubuntuforums.org/showthread.php?t=2448747](https://ubuntuforums.org/showthread.php?t=2448747)  

Funny stuff: turning on VT-d in the laptops UEFI makes SD-Card reader work.

---

### Post by tea for one on 2020-08-30
> **pmaff said:**
> Funny stuff: turning on VT-d in the laptops UEFI makes SD-Card reader work.

That's good news - Can you mark the thread as solved?

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by samlarson on 2020-09-10
> **pmaff said:**
> Thanks for the pointer. 
Here is my latest payday loan project [COLOR=#0000FF][FONT=Calibri][https://directloantransfer.com/](https://directloantransfer.com/)[/FONT][/COLOR]
@20.04 : I had the hope that possibly someone already has experienced success with 20.04 and Realtek RTS5250. ;-)

how is it even possible???

---

### Post by CelticWarrior on 2020-09-10
> **samlarson said:**
> how is it even possible?

Newer kernels support newer hardware.
Not the solution in this case but the hypotheses the question asks about is very plausible.

---

