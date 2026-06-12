---
title: "[SOLVED] How to boot an existing Linux or XP  installation from virtual box."
date: 2008-08-13
forum: General Help
---

### Post by nazish on 2008-08-13
hi guys I found a solution to the problem.
 
The easiest way to run an OS is to install it from the virtual machine. But this is not the case always. In my case I came to know about virtualization only after I had installed all my operating systems. My system config was something like this, I had three OS installed -
 
1. Windows XP
2. Ubuntu 8.04
3. Custom Built Linux.
 
My case was that I needed to boot into my custom built linux through Ubuntu using virtualization. Now I had to choose a Virtualization kit. I had three choices before me 
1. VmVare
2. Virtualbox
3. Qemu
 
I did not try VmVare at all. But between Virtualbox and Qemu Virtual box seemed to be way better. I downloaded the virtualbox from the SUN's website. It had a binary for my Ubuntu 8.04. Two double clicks and it was installed.
 
Now my problem is how to make virtualbox boot into my custom built linux or my existing windows xp installation. To achieve this you have two ways.
1. Create separate entries for each OS you want to boot or
2. Let virtualbox point to your MBR.
 
In the first case you will be booted into the OS os your choice, whereas in the second case when you start virtualbox you will be greeted with your own grub menu which you see every day when you start your system. It is dangerous to start your system in this way as the guest os(os you are going to boot from virtualbox) has all access to your hard disk and you may potetially damage your Host OS(OS on which virtual box is installed.)
 
I found these methods from the following post
> [**http://ubuntuforums.org/showthread.php?t=769883**]("http://ubuntuforums.org/showthread.php?t=769883")
any credit goes to him. This is the best post for running an existing XP installation.
 
**_Caution:_**
These methods require you reactivate your copy of windows. so please decide whether you want to really boot into existing windows installation using virtual box.
 
Installing Guest Additions(tools that make the guest os run faster and smoother on virtualbox) for XP will not let you boot into your existing windows install any more. so proceed with caution.
 
_**1st method -- pointing to existing linux install**_
you need to download and install a package called mbr.
```
sudo apt-get install mbr && mkdir ~/.VirtualBox && install-mbr ~/.VirtualBox/myboot.mbr --force
```
the above command mirrors a copy of your MBR onto a file called as myboot.mbr. we will be using this myboot.mbr in our virtualbox.
 
Then run the follwing command to create a virtual disk that fakes your current hard disk state - Partitions, grub everything.
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/linux.vmdk -rawdisk **/dev/sda -partitions 2 -mbr** ~/.VirtualBox/myboot.mbr -relative -register

```
 
**/dev/sda** -- should be replaced with the device of your choice
**partitions 2 --** the number 2 should be replaced by the partition number where your linux is residing.
 
to know what is your existing setup from the terminal type ```
fdisk -l
```. Then replace the entries. if it is **/dev/sda1** where you want to boot to then your command should be like
 
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/linux.vmdk -rawdisk **/dev/sda -partitions 1 -mbr** ~/.VirtualBox/myboot.mbr -relative -register

```
 
this method may fail in some cases and you just cant boot into the existing installation. then u need to follow the second method . The second method worked for me.
 
**_Method 2 point virtual box to your hard disk._**
 
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/SystemHD.vmdk -rawdisk /dev/sda -register
```
 
this creates a virtual disk called as SystemHD. Just create a virtual machine that uses this HD. Your work is done start the VM and run the OS of choice.

---

### Post by Mgiacchetti on 2008-08-13
you might also wish to know that Guest Additions 1.6.2-1.6.4 have a bug with xp guest that makes it so you cannot use seamless correctly, plus the shares do not show up and you may have a problem with networking.

the fix is to uninstall guest additions 1.6.2-1.6.4  and download guest additions 1.6.0 from [here]("http://www.virtualbox.de/download/1.6.0/") and install that instead.

May be a workaround, but until they really fix it, this is the best so far.

---

### Post by nazish on 2008-08-20
I did not know about the bug in the guest addition thank you for the info.

---

