---
title: "My USB 3.0 hard drives freeze my pc"
date: 2011-02-21
forum: Hardware
---

### Post by TimEnid on 2011-02-21
if my usb 3.0 hds are plugged in, when i reboot my pc, it freezes on the splash screen. or it freezes after i log in. I know its the hds causing this because when i unplug them and then reboot, it starts up just fine. I set it so that my hds are detected and wont auto mount, but the freezing still happens. i thought it to be a bios issue, but am not sure how to proceed. all my specs are in my sig. any suggestions?

---

### Post by fjgaude on 2011-02-21
What OS version are you using? Ubuntu 10.10 seems to handle USB3 okay.

---

### Post by TimEnid on 2011-02-21
> **fjgaude said:**
> What OS version are you using? Ubuntu 10.10 seems to handle USB3 okay.

Yes. 10.10

---

### Post by khelben1979 on 2011-02-22
Have you tried to connect the external harddrive to an USB 2.0 port to see if you get rid of the instability which occurs? If that fixes it, then a newer kernel might be the solution to this problem.

---

### Post by TimEnid on 2011-02-22
> **khelben1979 said:**
> Have you tried to connect the external harddrive to an USB 2.0 port to see if you get rid of the instability which occurs? If that fixes it, then a newer kernel might be the solution to this problem.
i havent tried that, but, i have a usb 2.0 hd connected to my 2.0 port and it never gives me issues. i keep it connected to the pc and it boots with no issues. When i get home today, i will plug them into 2.0 ports and see what happens.

how would i go about getting a new kernel? i have had this issue since 10.4

---

### Post by TimEnid on 2011-02-22
ok, so i connected the hard drives to usb 2.0 ports and didnt experience the issue. so how do i go about getting a new kernel?

---

### Post by TimEnid on 2011-02-24
anyone?

---

### Post by false truths on 2011-02-24
The Ubuntu kernels are stored here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

I've never tried to use USB3.0 because I don't have any, but that has the whole list of Ubuntu kernels.

---

### Post by TimEnid on 2011-02-24
> **false truths said:**
> The Ubuntu kernels are stored here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

I've never tried to use USB3.0 because I don't have any, but that has the whole list of Ubuntu kernels.

thanks, so i should install both header and image files?

and what about previous kernels. should i uninstall those? clean them with ubuntu tweak?

---

### Post by false truths on 2011-02-24
You install the headers-all then the headers for your architecture, then you install the image for your architecture.

As far as previous kernels, you may as well get rid of them. Most people keep one older kernel as a fallback in case the latest kernel fails, but it sounds to me like the older kernels wouldn't make much of a fallback for you.

---

### Post by TimEnid on 2011-02-25
> **false truths said:**
> You install the headers-all then the headers for your architecture, then you install the image for your architecture.

As far as previous kernels, you may as well get rid of them. Most people keep one older kernel as a fallback in case the latest kernel fails, but it sounds to me like the older kernels wouldn't make much of a fallback for you.

thanks. so i installed those files, do i need to do anything further? and how would i go about deleting my older kernels?

---

### Post by khelben1979 on 2011-02-28
I think the best way if you really want USB 3.0 working is that you upgrade to Linux kernel 2.6.37 which means newer drivers for modern hardware.

An other option is to compile it all from scratch and set up the configuration yourself, but it's not an easy thing to do. There are, however, good documentation available if you want to do it.

---

### Post by TimEnid on 2011-02-28
> **khelben1979 said:**
> I think the best way if you really want USB 3.0 working is that you upgrade to Linux kernel 2.6.37 which means newer drivers for modern hardware.

An other option is to compile it all from scratch and set up the configuration yourself, but it's not an easy thing to do. There are, however, good documentation available if you want to do it.
thanks for the response. i went ahead and updated my kernel. its been two days now and i have not experienced the freezing. im just giving it a little bit more time before i can be sure that the issue is fixed. once confirmed, i will come back and mark the thread solved.

thanks again.

---

