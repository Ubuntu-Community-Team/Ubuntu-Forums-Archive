---
title: "&quot;FATAL: Module not found error&quot; using modprobe"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by shariefbe on 2008-12-13
Hello,
i have an problem with modprobe command...i compiled the usbcore module and inserted using "**insmod**" command...and its working..when i see "**lsmod**" its in that list...but when i insert this module using "**modprobe**" i am getting the FATAL error....that is 

[B]root@sharief-desktop:/home/sharief/Desktop/drivers/core# modprobe usbcore.ko
FATAL: Module usbcore.ko not found.[/B]
i dont know whats the error...can anyone help me...

---

### Post by Partyboi2 on 2008-12-13
Try
```
modprobe usbcore
``` without the .ko end bit.

---

### Post by shariefbe on 2008-12-13
yes...getting the same error...see

[B]root@sharief-desktop:/home/sharief/Desktop/drivers/core# modprobe usbcore
FATAL: Module usbcore not found.[/B]

---

### Post by shariefbe on 2008-12-14
i disabled that module while compiling the kernel.....now i am trying to install manually...this is for college project...please help me

---

### Post by iponeverything on 2008-12-14
Generate your module dependencies 

```
sudo depmod -a
```

---

### Post by shariefbe on 2008-12-14
when i use this command am getting the following error...

[B]sharief@sharief-desktop:~$ sudo depmod -a
[sudo] password for sharief:
FATAL: Could not rename /lib/modules/2.6.26/modules.dep.temp into /lib/modules/2.6.26/modules.dep: No such file or directory
sharief@sharief-desktop:~$[/B]

---

### Post by iponeverything on 2008-12-15
attach the file /tmp/find.txt from this command:

```
find /lib/modules > /tmp/find.txt

```

---

### Post by shariefbe on 2008-12-15
this is the attched txt/find.txt file..

---

### Post by iponeverything on 2008-12-15
backup your original module to /root if you have one:

```
sudo mv /lib/modules/`uname -r`/kernel/drivers/usb/core/usbcore.ko /root/

```

Next copy your custom module into its place:

```
sudo cp /home/sharief/Desktop/drivers/core/usbcore.ko  /lib/modules/`uname -r`/kernel/drivers/usb/core/usbcore.ko
```

rerun our depmod command: 

```
sudo depmod -a

```

If this depmod fails run this and upload /tmp/debug.txt.

```
sudo depmod -v -a > /tmp/debug.txt 2>&1

```

If the depmod did work load your module with:

```
sudo modprobe usbcore

```

---

### Post by shariefbe on 2008-12-15
actually i didnt have "**usbcore**" module in /**lib/modules/`uname -r`/kernel/drivers/usb/core/**

so i tried the second command....for that i am getting the following error

[B]root@sharief-desktop:/home/sharief# sudo cp /home/sharief/Desktop/drivers/core/usbcore.ko  /lib/modules/`uname -r`/kernel/drivers/usb/core/usbcore.ko
cp: cannot create regular file `/lib/modules/2.6.26/kernel/drivers/usb/core/usbcore.ko': No such file or directory
root@sharief-desktop:/home/sharief#[/B]

---

### Post by shariefbe on 2008-12-15
but i am getting this command work...

[B]root@sharief-desktop:/home/sharief# sudo depmod -v -a > /tmp/debug.txt 2>&1
root@sharief-desktop:/home/sharief# sudo depmod -a
root@sharief-desktop:/home/sharief#[/B]

---

### Post by iponeverything on 2008-12-15
put it in misc:

```
sudo cp /home/sharief/Desktop/drivers/core/usbcore.ko  /lib/modules/`uname -r`/kernel/drivers/misc/usbcore.ko
```

and rerun your depmod.

---

### Post by shariefbe on 2008-12-15
yes thanks...its working now...

[B]root@sharief-desktop:/home/sharief# sudo cp /home/sharief/Desktop/drivers/core/usbcore.ko  /lib/modules/`uname -r`/kernel/drivers/misc/usbcore.ko
root@sharief-desktop:/home/sharief# sudo depmod -a
root@sharief-desktop:/home/sharief# cd Desktop/
root@sharief-desktop:/home/sharief/Desktop# cd drivers/
root@sharief-desktop:/home/sharief/Desktop/drivers# cd core/
root@sharief-desktop:/home/sharief/Desktop/drivers/core# modprobe usbcore
root@sharief-desktop:/home/sharief/Desktop/drivers/core#[/B]

result of "dmesg" last 7 lines

[B][   49.171452] NET: Registered protocol family 17
[   52.641079] NET: Registered protocol family 10
[   52.646322] lo: Disabled Privacy Extensions
[   62.696213] eth0: no IPv6 routers present
[ 6316.438077] usbcore: registered new interface driver usbfs
[ 6316.438782] usbcore: registered new interface driver hub
[ 6316.442780] usbcore: registered new device driver usb
root@sharief-desktop:/home/sharief/Desktop/drivers/core#[/B] 

even though my usb port is not working...what to do?please help me...

---

### Post by iponeverything on 2008-12-15
> i disabled that module while compiling the kernel.....now i am trying to install manually...this is for college project.

There is only so much a person can do. I did the easy part in getting your module to load using the modprobe command, I think you going to have to figure out why it does not work the way you expect on your own. 

BTW -- you don't have to "cd" to any special directory for modprobe to work.

---

### Post by shariefbe on 2008-12-16
yes...i dont know why it does not work.....can you help me to make my USB port work...

---

### Post by iponeverything on 2008-12-16
This is school project right? What is the project?  I am afraid we can't do your projects for you. 

Does USB work with the stock kernel?

---

### Post by shariefbe on 2008-12-16
yes..its college project...my project is "hacking the USB port"...i have to gather all the details about "USB port"...for that i planned to disable the usb support in the menuconfig....after that i compiled the "usbcore" module manually and planned to install dynamically...yes i done that..but now my usb port is not working....now i dont know what to do....can you help me...just now my usb port should work..by installing the module dynamically....Thanks a lot

---

### Post by iponeverything on 2008-12-16
If your usb works with original default kernel and does not work with your module, I would say that problem is with your module and not with the usb port.

If the issue is with your module, it may mean that you are not quite done with your project yet --

---

### Post by shariefbe on 2008-12-16
yes i know that...for that only am finding help from you...now i have to find the problem with my module....but i dont know how to find and how to rectify that...please help me....

---

### Post by shariefbe on 2008-12-16
i have to make my USB port to work....help me

---

### Post by iponeverything on 2008-12-16
no. I can't help you. 

No one is going to be able to give you some magic command for you to paste into your terminal window to make *your* modified usb module do whatever mysterious thing that it is supposed to do  - for you to complete *your* assignment.

---

### Post by shariefbe on 2008-12-16
ya Thanks...i didnt ask like that...just i want to know the necessary "modules" which is needed to make USB port work....Thats all...after that i will do the remaining things....

---

### Post by iponeverything on 2008-12-16
```

foo@lp:~$ lsmod |grep usb
usbcore               148848  3 uhci_hcd,ehci_hcd

```

FYI - modprobe loads all the necessary ancillary modules. 

So -- The problem is with your usbcore.ko.

---

### Post by shariefbe on 2008-12-17
whether i need to install this "**uhci_hcd,ehci_hcd**" modules?

---

### Post by iponeverything on 2008-12-17
type ```
lsmod |grep usb
``` and see.

I am done with this thread. Don't expect another response from me. Don't PM me. 

Ask your teacher or a classmate for help or use google.

---

### Post by shariefbe on 2008-12-17
ya ok Thanks.....Thanks a lot

---

### Post by danger89 on 2010-04-08
I found wusbcore (*.ko) in my kernel is this the same?

---

