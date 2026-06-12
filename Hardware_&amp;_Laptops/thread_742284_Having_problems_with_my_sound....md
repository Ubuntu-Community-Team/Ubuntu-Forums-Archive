---
title: "Having problems with my sound..."
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by Num19 on 2008-04-01
Hello everyone,
I have no sound on my computer, I tried to reinstall my drivers but unfortunately, it didn't work.
At start, before I deleted my sound driver I had sound just when my windows started, the starting tune of windows and the for a couple of minutes I succeeded to get sound of my sound control in the task line, but then, nothing, I even couldn't open my sound control and getting the notification  that there are no mixing devices that are available.
Now, after I deleted my driver and installed it a several of times, I'm not getting any sound even when windows starts.
Every time that I'm restarting windows I get the message of a new hardware (PCI DEVICE), even that I installed the right driver.
My sound card is Realtek ALC888/S/T @ Intel 82801GB ICH7 - High Definition Audio Controller [A-1].
My motherboard is Intel Newberry Lake D945GCNL.
I tried to install the updated versions of the bios and the chipset as well.
I have to say that it might be related to the incident when I tried to backup C partition with Norton Ghost and it got stucked in the middle, and I had to run windows 98 boot disc in order to get C partition activated instead of the ghost partition.
I thank the responders in advance.

---

### Post by prshah on 2008-04-01
> **Num19 said:**
> 
At start, before I deleted my sound driver I had sound just when my windows started, the starting tune of windows and the for a couple of minutes I succeeded to get sound of my sound control in 

Every time that I'm restarting windows I get the message of a new hardware (PCI DEVICE), even that I installed the right driver.
My sound card is Realtek ALC888/S/T @ Intel 82801GB ICH7 - High Definition Audio Controller [A-1].


I hope you are not asking for Windows advice here. In any case...

The Intel GCNL/GCPE/etc boards come with RealTek High Definition Audio Driver, which uses (In Windows XP/Vista) the new "UAA" or "Universal Audio Architecture", which personally I believe is MS's attempt at an ALSA equivalent.

So what you need to do, BEFORE installing sound drivers, is get and install the UAA from the MS website, THEN install your sound drivers.

In linux, there is no problem, Realtek high-def audio is automatically recognized and enabled as Intel high-def audio.
>  lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Wed Apr 02 01:01:34 ~:$ 


---

### Post by Num19 on 2008-04-01
A few days ago, I downloaded Microsoft UAA Bus Driver for XPSP2 - KB888111.exe from Emule, and i tried to open it but it says that update\update is illegal in win32 application.
I tried to open kb888111xpsp2.exe from the realtek driver installation and it's opening the same notification.
I didn't succeed to find the UAA in MS website.

---

### Post by Num19 on 2008-04-02
Hey,
please help me, I have been muted for a whole week!
If this forum is not related to my problem, can you please direct me to the relevant one?

---

