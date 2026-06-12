---
title: "ppscsi does not work in feisty"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by nicco on 2007-05-26
I am trying to get the ppscsi modules (for parallel port scanners) to work on feisty, but they refuse to compile.  I get an error of the type:

/usr/src/modules/ppscsi/ppscsi.c:1147:39: error: macro "INIT_WORK" passed 3 arguments, but takes just 2

After doing som googling it seems clear that these drivers are not updated to work with newer kernels. (The last time I tried them was on dapper, where they worked great.) Are these modules still being maintained? Or are there any other available options for parport scanners?

---

### Post by klytu on 2007-05-26
> **nicco said:**
> I am trying to get the ppscsi modules (for parallel port scanners) to work on feisty, but they refuse to compile.  I get an error of the type:

/usr/src/modules/ppscsi/ppscsi.c:1147:39: error: macro "INIT_WORK" passed 3 arguments, but takes just 2

After doing som googling it seems clear that these drivers are not updated to work with newer kernels. (The last time I tried them was on dapper, where they worked great.) Are these modules still being maintained? Or are there any other available options for parport scanners?

I use a parallel port scanner in Feisty and I didn´t have to compile any additional modules. It worked right ¨out of the box¨. What make and model of scanner do you have?

---

### Post by nicco on 2007-05-27
According to the label it's a "Microtek Phantom Parallel" (MRS-600V3). In dapper I used the modules ppscsi.ko and onscsi.ko, meaning that it uses the OnSpec parport scsi interface.

When I try xsane, I get an error message and the following pops up in dmesg:

[  922.016000] ppdev0: registered pardevice
[  922.064000] ppdev0: unregistered pardevice

It's hard even to find windows drivers for this thing, the drivers on the disk were designed for win9x and refused to work in xp.

---

### Post by klytu on 2007-05-27
> **nicco said:**
> According to the label it's a "Microtek Phantom Parallel" (MRS-600V3). In dapper I used the modules ppscsi.ko and onscsi.ko, meaning that it uses the OnSpec parport scsi interface.

When I try xsane, I get an error message and the following pops up in dmesg:

[  922.016000] ppdev0: registered pardevice
[  922.064000] ppdev0: unregistered pardevice

It's hard even to find windows drivers for this thing, the drivers on the disk were designed for win9x and refused to work in xp.

I did some research and found out what you probably already know - it does seem that you need those models in order to operate your scanner.  Some things you might try, if you haven´t done so already:

1. If you still have Dapper up and running - the models you compiled for Dapper might possibly work in Feisty.  You could try copying the pre-compiled modules from Dapper to the appropriate locations in Feisty. If you don´t still have Dapper installed and you have a Live CD version, you could try compiling modules in the Dapper enviroment, saving them to the appropriate place in Feisty.

2.  Check all of the docs in the source package - there may be an explanation somewhere on what arguments  the ¨INIT_WORK¨ macro should take and how to control that. Maybe there is an environment variable that needs to be set before you do the build. In compiling the modules - do you do a typical make configure, ./configure, make sequence? If so the setting of the environment variables is usually done by passing options to ./configure. You could try contacting the developer for help with this part if you can´t find it in the docs - they might be able/willing to assist even though the project hasn´t been updated in a while. 

3. If all else fails you could try filing a bug report. 

I haven´t had direct experience with your scanner or with compiling those modules, but those are the things I would try. Hope some of this turns out to be helpful. Good luck...

---

### Post by nicco on 2007-05-28
I believe INIT_WORK is a kernel macro, and not really part of the ppscsi modules. There were other errors when compiling such as missing header files, that are all related to changes in the linux headers. I managed to compile the modules againt an older set of linux headers, but insmod refused to load the resulting files.

So in summary I think there is nothing wrong with the ppscsi code, it just needs to be updated for newer kernels. This might be easy (even trivial) for someone with kernel development experience, though.

---

### Post by duglaswb on 2007-05-30
could someone give me some info on how to install these modules.  I have a microtek parport scanner that is going to require these modules to work.

I am not using ubuntu, I am using debian etch, my kernel is 2.6.18

It's not as simple as:  apt-get install ppscsi  - is it?

I have downloaded the file from debian unstable repos.  It is "ppscsi-source_0.3_all.deb"  and now I assume that I must depackage and compile it.  That is where I am stuck.

Do I do:  dpkg -i ppscsi-source_0.3_all.deb  ?
If so do I need to do that in a specific directory?  and then what?

As you can see I am very new to linux and very confused.


Thanks for any help that anyone has to offer.

---

### Post by haydnc on 2007-06-02
I have managed to get ppscsi to work properly in feisty. I'm posting the full instructions I've typed up here for anyone else who stumbles across them. The individual parts of this all exist out there on the net, but I've not found anywhere that puts the whole lot together, so here goes:

**How to make a HP ScanJet 5100/5200C work with Ubuntu Feisty (Kernel 2.6.20)**

1. Make sure that you have the kernel headers installed: 

```
sudo apt-get install linux-headers-`uname -r`
```

2. Download the latest(?) version of ppscsi from [http://penguin-breeder.org/kernel/download/](http://penguin-breeder.org/kernel/download/) : ppscsi-beta2-20060424.tar.gz

3. Once downloaded extract the file:
tar zxvf ppscsi-beta2-20060424.tar.gz

This next bit is from translated instructions on the spanish Ubuntu website: 

> When extracted and running make we get two significant errors as per the above website:

… /ppscsi-beta2/ppscsi.h: 16: 26: error: linux/config.h: The directory file does not exist or

… /ppscsi-beta2/ppscsi.c: 1148: 39: error: macro “INIT_WORK” received 3 arguments, but it only took 2

Analysis:

The file linux/config.h this obsolete and macro “INIT_WORK” at the moment receives two arguments.

That is to say, the file config.h is replaced at the moment by the file autoconf.h

**Solution:**

4. Open ppscsi.h in the editing program of your choice. 
Change the where it says **#include <linux/config.h>** to read **#include <linux/autoconf.h>**
*This is on line 16 of the copy of ppscsi.h that I'm working with.*

5. Save and close ppscsi.h and open ppscsi.c

Change the following lines:
**static void ppsc_tq_int (void *data) **
change to 
**static void ppsc_tq_int (struct work_struct *data)**
*(Note: This is line 191 in the copy of ppscsi.c I'm working with)*
[B]
INIT_WORK (&pha->wq, ppsc_tq_int, pha);[/B]
change to
**INIT_WORK (&pha->wq, ppsc_tq_int);**
*(Note: This is line 1148 in the copy of ppscsi.c I'm working with)*

6. Save and close ppscsi.c and run make. This should produce a set of .ko files, including the all important (to us anyway) ppscsi.ko and epst.ko.

7. Since the Makefile for ppscsi has no instructions for installing these files we need to copy them to their new location manually:
```
sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
```

8. Next we need to tell the kernel that they exist:
```
sudo depmod
```

9. Lastly we need to load the modules:
```
sudo modprobe ppscsi
sudo modprobe epst
```

This will make the scanner useable until next time the computer is rebooted. 

In order to make sure that the scanner is recognised from the moment you boot up it is necessary to edit **/etc/modules** and add the following two lines to the end of the file:
```
ppscsi
epst

```

My apologies if this seems a little cluttered, but hopefully it should work as well for you as it did for me.

---

### Post by CheeseEatingBulldog on 2007-07-22
> **haydnc said:**
> I have managed to get ppscsi to work properly in feisty. I'm posting the full instructions I've typed up here for anyone else who stumbles across them. The individual parts of this all exist out there on the net, but I've not found anywhere that puts the whole lot together, so here goes:

**How to make a HP ScanJet 5100/5200C work with Ubuntu Feisty (Kernel 2.6.20)**

1. Make sure that you have the kernel headers installed: 

```
sudo apt-get install linux-headers-`uname -r`
```

2. Download the latest(?) version of ppscsi from [http://penguin-breeder.org/kernel/download/](http://penguin-breeder.org/kernel/download/) : ppscsi-beta2-20060424.tar.gz

3. Once downloaded extract the file:
tar zxvf ppscsi-beta2-20060424.tar.gz

This next bit is from translated instructions on the spanish Ubuntu website: 



**Solution:**

4. Open ppscsi.h in the editing program of your choice. 
Change the where it says **#include <linux/config.h>** to read **#include <linux/autoconf.h>**
*This is on line 16 of the copy of ppscsi.h that I'm working with.*

5. Save and close ppscsi.h and open ppscsi.c

Change the following lines:
**static void ppsc_tq_int (void *data) **
change to 
**static void ppsc_tq_int (struct work_struct *data)**
*(Note: This is line 191 in the copy of ppscsi.c I'm working with)*
[B]
INIT_WORK (&pha->wq, ppsc_tq_int, pha);[/B]
change to
**INIT_WORK (&pha->wq, ppsc_tq_int);**
*(Note: This is line 1148 in the copy of ppscsi.c I'm working with)*

6. Save and close ppscsi.c and run make. This should produce a set of .ko files, including the all important (to us anyway) ppscsi.ko and epst.ko.

7. Since the Makefile for ppscsi has no instructions for installing these files we need to copy them to their new location manually:
```
sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
```

8. Next we need to tell the kernel that they exist:
```
sudo depmod
```

9. Lastly we need to load the modules:
```
sudo modprobe ppscsi
sudo modprobe epst
```

This will make the scanner useable until next time the computer is rebooted. 

In order to make sure that the scanner is recognised from the moment you boot up it is necessary to edit **/etc/modules** and add the following two lines to the end of the file:
```
ppscsi
epst

```

My apologies if this seems a little cluttered, but hopefully it should work as well for you as it did for me.


It all works ecept inserting EPST which gives me:

root@ifrit:~# sudo modprobe epst
FATAL: Error inserting epst (/lib/modules/2.6.20-16-generic/kernel/drivers/parport/epst.ko): No such device

I have tried changing EPP modes in the bios, but nothing seems to work.

---

### Post by vze2jdnz on 2007-08-27
I have tried everything in here too and get the same error message:

root@ifrit:~# sudo modprobe epst
FATAL: Error inserting epst (/lib/modules/2.6.20-16-generic/kernel/drivers/parport/epst.ko): No such device

I can't get my scanner to work no matter what I do!
Does anyone know what to do to remedy this?

---

### Post by Titik on 2008-02-14
Hi,

I havee  the same problem on my gutsy.
when I 'm doing 
```
sudo modprobe epst
```


I get 
```

FATAL: Error inserting epst (/lib/modules/2.6.22-14-generic/kernel/drivers/parport/epst.ko): No such device

```

do you have a solution??:(

Sorry foor my english but I'm French so....:lolflag:

---

