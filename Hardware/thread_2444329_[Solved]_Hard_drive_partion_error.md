---
title: "[Solved] Hard drive partion error"
date: 2020-05-28
forum: Hardware
---

### Post by thewhitekeygamer on 2020-05-28
Hello everyone. I'm new to this forum so please tell me if this is in the wrong spot. I'm trying to dual boot my windows 10 pc with xubuntu. I already have xubuntu on a bootable usb stick and want to get it on a partion of my hard drive. I tried resizing my main windows 10 partion with GParted, but when I confirm the changes I get an error message. Could someone please explain if I am doing this correctly, or I am using the wrong program or something like that. Thanks for reading. EDIT: I thought I solved the issue but I didn't :oops:

---

### Post by jp41 on 2020-05-28
you will find a nice [tutorial here]("https://itsfoss.com/install-ubuntu-dual-boot-mode-windows")

---

### Post by thewhitekeygamer on 2020-05-28
In the tutorial, it says to delete a partion to free up space. Is it safe to delete any partion as long as it is not the one with windows, or is it only safe to delete ones like free space?

---

### Post by QIII on 2020-05-28
Hello!

Before you follow any advice given, please beware:

***Do not, under any circumstances, modify any Windows partitions with Linux tools such as GParted***.  You will likely render your Windows installation inoperative.  Use Windows tools to modify Windows partitions.

Don't bother deleting a partition.  You can shrink one to free some space using Windows tools.

---

### Post by thewhitekeygamer on 2020-05-28
Ok. I have space for xubuntu now, but when I try to install it, I get the error message Errno 5 input/output error. Could someone please tell me what this means and how to fix it?

---

### Post by wildmanne39 on 2020-05-28
> I get the error message Errno 5 input/output error.
That is usually means you have a drive issue, you may want to check your drive for errors.

---

