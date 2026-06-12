---
title: "How to create a Windows Virtual Machine in Ubuntu from an existing installation?"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by giyad on 2009-11-12
I currently have an installation of Windows Vista on an internal drive.  This is my default OS as I am new to Linux and Ubuntu.  I've installed Ubuntu 9.04, and I was wondering if it would be possible for me to run the existing Windows partition as a virtual machine from within Ubuntu??

I already have a copy of VMware Workstation if that helps.

I found [this link]("http://imrannazar.com/Running-a-Windows-Partition-in-VMware"), and [this one]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_run_Windows_with_VMware_Player_in_Linux_for_free"), but they seem outdated and they also don't take into account that I have VMware Workstation.  Would it be easier with VM Workstation, or should I follow those steps?  Or is there a better way to go about this?

---

### Post by audiomick on 2009-11-12
Hi.
I read something about this a while back. I believe it is possible, I think it was a function of VM Ware or one of the other Virtualisation programs.
Do a bit more searching... :-)

---

### Post by giyad on 2009-11-12
> **audiomick said:**
> Hi.
I read something about this a while back. I believe it is possible, I think it was a function of VM Ware or one of the other Virtualisation programs.
Do a bit more searching... :-)
Well, I've got my Boot Camp partition of Windows working on my Mac with Parallels, it was extremely easy to set up. 

It doesn't look to be that easy with vmware on linux, and I don't want to buy Parallels for Linux now (cuz I just got vmware), so I'm hoping someone can point me in the right direction.

---

### Post by Mark Phelps on 2009-11-12
> **giyad said:**
> I currently have an installation of Windows Vista on an internal drive.  This is my default OS as I am new to Linux and Ubuntu.  I've installed Ubuntu 9.04, and I was wondering if it would be possible for me to run the existing Windows partition as a virtual machine from within Ubuntu??


If what you're asking is can you use virtualization inside Ubuntu to run a Windows installation NOT installed inside the virtual machine -- the answer is NO.  Virtualization allows you to INSTALL and RUN another operating system inside an existing host OS, not to run another OS outside the virtual machine.

---

### Post by giyad on 2009-11-12
> **Mark Phelps said:**
> If what you're asking is can you use virtualization inside Ubuntu to run a Windows installation NOT installed inside the virtual machine -- the answer is NO.  Virtualization allows you to INSTALL and RUN another operating system inside an existing host OS, not to run another OS outside the virtual machine.
Well obviously I don't want to run an OS outside the virtual machine, that would just be dual booting.  What I'm trying to do is take the existing installation of windows, and virtualize it (or boot it) within Linux.  This is definitely possible as I've provided a link in my original post about a guy who did it with XP.  And I've done it on my Mac with Win 7 on Bootcamp and Parallels according to [this guide.]("http://lifehacker.com/267905/virtualize-and-dual+boot-the-same-windows-on-your-mac")  

I want to get it done on Ubuntu, but I'm a first time linux user so I'm not sure how to go about it, whether it would be easier to use VMware workstation, parallels, openvz, or some other method?

---

### Post by Hilko on 2010-03-21
A very very interesting question. Have you succeeded in doing this ?
If so, please post it here and share it with us. I wish I could do this too.

---

