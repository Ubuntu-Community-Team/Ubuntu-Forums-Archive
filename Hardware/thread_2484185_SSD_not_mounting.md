---
title: "SSD not mounting"
date: 2023-02-19
forum: Hardware
---

### Post by Laffen_macc on 2023-02-19
Hello.
I purchased a SSD a month ago and I probably destroyed it... I should format the disk and I think I deleted some partition on it. Now it will not mount and I can not format it.

It's empty, so I will not loose anything :-)

Any suggestion to how i solve this?

Thanks
L.

---

### Post by Laffen_macc on 2023-02-20
Gparted gave me this information now...

L.

---

### Post by mIk3_08 on 2023-02-20
Did you try to run the fdisk utility? Run the command below. I'm not that expert on this but maybe this command below will help you enable your extended storage device.
```
sudo /sbin/fdisk /dev/xxx 
```
When you successfully run the fdisk command It will says something like,
Welcome to fdisk (util-linux 2.31.1).

Then after using fdisk utility I run the command below depending on what extension name you use. 
Try to mount the extended partition via command below. 
```
sudo pmount /dev/sda2 /media/Extended
sudo mount /dev/sda2 /media/Extended
```

Regards and cheers

---

### Post by Laffen_macc on 2023-02-25
Thanks for reply, sorry for late response.

I tried fdisk, it did not fix my ssd.

I drop it for a while, but thanks anyway.

L.

---

### Post by DuckHook on 2023-02-26
The warning message in your posted screenshots give you guidance.

[LIST=1]
[*]Do you have dosfstools and mtools installed?
[*]Why were you using such a stunted and primitive filesystem (FAT32) for a SSD this large?
[*]How are you trying to format?
[*]What filesystem are you trying to format to?
[*]Given that you are posting Ubuntu screenshots, you are running Linux. Linux uses ext4 filesystem for good reason. That's the one you should stick to.
[*]Is this a default OS in its pristine state or have you changed it?
[*]If changed, what did you do? This needs to be recounted in detail.
[*]You say that you tried fdisk, but what did you actually do? Post the actual series of steps that your did. Also, post the results back to this thread.
[/LIST]
Rather then posting screenshots, highlight terminal output and post them as text, not images.

---

