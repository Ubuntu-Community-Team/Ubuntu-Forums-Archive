---
title: "Problem creating parport0"
date: 2010-07-29
forum: Hardware
---

### Post by chinleybrewer on 2010-07-29
Hi, I have a JTAG wiggler program (Sharpflash) which makes use of the parallel port however I cannot get it to access the port.

I am using Ubuntu 8.04 (with EMC2 machine controller)

Initially when I run the program I get:
can't open /dev/parport0
Unable to find a parallel port

Ok, so reading around, I need to create the device so I do:
sudo mknod /dev/parport0 c 99 0

Now, I still get the same message when running sharpflash:
can't open /dev/parport0
Unable to find a parallel port

Reading again I try:
ls -al /dev/parport0
which gives:
crw-r--r-- 1 root root 99, 0 2010-07-29 16:48 /dev/parport0

More reading and I try:
sudo chmod a+rw /dev/parport0
so
ls -al /dev/parport0 
now gives:
crw-rw-rw- 1 root root 99, 0 2010-07-29 16:48 /dev/parport0

Unfortunately I now get a different message when running the program:
can't claim device
Unable to find a parallel port

That has me stumped.  I had tried running the program with and without sudo prefix but no difference.

Reading the source code I see:
```
	i = ioctl(ppt, PPCLAIM);
	if (i < 0) {
		fprintf(stderr, "can't claim device\n");
		close(ppt);
		return 0;
	}
```
so the io operation with PPCLAIM is failing.

I have a feeling I am missing something obvious but... 
help:(

---

### Post by chinleybrewer on 2010-07-30
Not sure exactly what the problem was but I realised that I had two kernels installed rtai and 386 (I could choose which one I wanted from Grub).  

I need rtai kernel for EMC2 to work properly and I had mistakenly added the 386 kernel when trying to get my wireless card working.

The Parport was not working when booting into either kernel but I uninstalled the packages which had caused the 386 kernel to appear and then after rebooting, parport0 was auto loading - after sorting out permissions and groups I can now access it perfectly.:D

---

### Post by SEECo on 2010-08-03
I am new to Ubuntu, but have  a little Knowledge about Linux. I have the same problem for the parport0 write access problem. I have done all the tries but without sudo command. Thank for this post I got solved my parport0 problem. Avrdude has got my parport0 successfully.

Thanksssssssssss.
:p

---

