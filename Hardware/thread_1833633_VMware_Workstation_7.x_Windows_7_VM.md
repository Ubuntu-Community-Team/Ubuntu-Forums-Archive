---
title: "VMware Workstation 7.x Windows 7 VM"
date: 2011-08-26
forum: Hardware
---

### Post by lslwoodley on 2011-08-26
Hi Folks, 

i'm brand new to linux and the sorts = total newb 

My question is: How can i mount my external HDD to my Windows VM. 
My Issue: When i stick in my ext HDD, UBUNTU mounts it fine>But i cannot mount it then to my Windows VM which is a pain, because all of my data is there from the Windows Backup. I can mount ISO's to the VM fine, so i have installed most of my windows apps, but i can mount the ext hdd to the VM without getting this error..

[COLOR="Red"]"The specified device appears to be claimed by another driver (usb-storage) on the host operating system which means that the device may be in use. To continue, the device will first be disconnected from its current driver."[/COLOR]

I made the big jump to linux + virtualization so i can learn this new thing side by side... 

Any assistance will be greatly appreciated.

---

### Post by lslwoodley on 2011-08-26
So let me be clear of my setup. 

T500 Lenovo Laptop running Ubuntu 11.x 64bit, with VMware Workstation 7.x on top of it. 

One (1) windows 7 vm, which is going to run all of my usual windows utilities as well as work tools.

---

### Post by e79 on 2011-08-26
> **lslwoodley said:**
> [COLOR=Red]"The specified device appears to be claimed by another driver (usb-storage) on the host operating system which means that the device may be in use. To continue, the device will first be disconnected from its current driver."[/COLOR]

That is a normal message from VMware simply telling you that your host (Ubuntu) has it mounted, and you just need to press 'OK' once or twice and it should be mounted in your Windows VM (guest). It would do the same if your host would be Windows and your guest Ubuntu or any other distro for that matter. So just accept (press OK once or twice) and you should be home free  ;)

Hope this helps

---

