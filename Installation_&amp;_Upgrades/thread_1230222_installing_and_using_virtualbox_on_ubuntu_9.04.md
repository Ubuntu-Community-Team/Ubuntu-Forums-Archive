---
title: "installing and using virtualbox on ubuntu 9.04"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by alazar22 on 2009-08-03
hi there every body, i am new to ubuntu and i wanted to use virtual box 3.02 to install a virtuall windows xp. when i tried to install virtualbox-3.0_3.0.2-49928_Debian_etch_i386 a message that says "Dependency is not satisfyable pyton 2.4 (>= 2.3.90)". what do i have to do to get virtual box working and install the windows xp ? thanks in advance!

---

### Post by Psicolonia on 2009-08-03
sudo apt-get install python

OR

System -> Administration -> Synaptics package manager
then search for python and mark "install". Click apply and all is done.

---

### Post by The Thug on 2009-08-03
You can also install VB through Synaptics although its an older version.

---

### Post by T3CHKOMMIE on 2009-08-12
hi,

im also having a problem installing virtualbox. i switched from a OS X and XP and love ubuntu. i have 9.04 installed on my 1005ha eeepc. i have the netbook kernal 2.6.29-1-netbook but i have general headers... cant get my deb of the 2.6.29-1 headers to find its dependancies.... another problem for another day but might be realted.

i installed VB 2.2.2 and the newer 3.0.4 from the website all deb ran nicely, but when the program tried to complie vboxdrv....i get a failure to complile sgesting to run setup as root and get this 

VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-<version> whereby <version> can be determined by 'uname -r') and execute
  /etc/init.d/vboxdrv setup
as root.

the logs give me some erros that i feel are kernel-header realted. but im new to all this... any ideas? i love running my VMs i really would like to do it in ubuntu! thanks for your help!

---

### Post by pteja on 2009-08-13
I have a similar problem as T3CHKOMMIE. Getting the same error while installing VB.

Am running Jaunty. Linux kernel 2.6.22 is installed and running :)
However, cannot get the sources / headers for this version of the kernel :(

Linux kernel headers / sources / image for 2.6.28 are installed :)
However, cannot boot (by updating GRUB entries) using this version of the kernel :(

So - I need to either get the headers for 2.6.22 or need to make the machine boot using 2.6.28.

Any ideas for doing 1 or 2?

Thanks.

---

### Post by T3CHKOMMIE on 2009-10-03
petja,

im not sure if i can help much but i DID finally get VB working. however, im running NBR and a something . something . 15 kernel.  and headers. i was having vbx driver issues with the kernel and something kept installing multiple headers (when i had more than one header installed ubnutu wouldn't boot... maybe look into that). i had to install an legacy version of VB i think it was 2.2.2... i ran the Deb. and it asked me if i wanted to keep the current version or install the new DVR. i elected to keep the currently installed one, and VB worked just fine. albeit slow on my netbook, but i did get it to work. im not sure what the deal was with my headers, but it sounds like you're running eeebuntu? i think i had a kernel ending in 28 when i was on eeebuntu and just didn't like it so i went with the conical version and the Net book remix headers ended in 15. 

hope this helps! im no expert but i figured anything is better than nothing right? good luck!

---

### Post by ausbuscon on 2009-10-13
Hi 

I have recently got a 1005ha and have put jaunty on it.  I have successfully installed virtual box. I am trying to get windows into the virtual box.

 I copied the eeepc support cd which came with the 1005ha over to the machine and mounted with winpe.iso within virtualbox.  when I ran VB it started OK with the eeepc recovery program, but said it could not find the recovery CD.  creating and ISO of the entire CD didn't work either.

Any thoughts about how to get windows into VB on the 1005ha would be appreciated.

---

### Post by BigCajun on 2009-10-13
> **The Thug said:**
> You can also install VB through Synaptics although its an older version.

You could also add Virtualbox's repository to your /etc/apt/sources.list to get the latest 3.0.8 (I've been running theirs for a number of months now on both Jaunty and Karmic).

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Scroll down to the section "Debian-based Linux distributions" and it gives you the details.

---

### Post by ausbuscon on 2009-10-14
Hi

Did you load windows using the 1005ha support cd???? Can you let me know how you did it?

Ta

---

