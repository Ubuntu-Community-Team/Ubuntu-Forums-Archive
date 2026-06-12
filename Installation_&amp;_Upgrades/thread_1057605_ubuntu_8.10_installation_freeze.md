---
title: "ubuntu 8.10 installation freeze"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by arch1234 on 2009-02-02
I have tried to install ubuntu 8.10 using the live cd but the installation freezes. Sometimes is freezes right after I enter my name and password, or when it is copying the files to the hard drive. It always reaches 22% and then it just stops. I have tested the cd and it turned out just fine. I have been able to run ubuntu through the live cd, but no luck installing it.

Specs:
Custom made PC about 5 years old
AMD Athlon XP (0.13) 1667 Hz
512 RAM
VIA KM266 chipset

My computer doesn't have any other OS currently installed because I formatted all of it and then created the partitions for the installation of ubuntu.

Could this be a problem of the computer being to old?
Can any one help me install ubuntu successfully!!

---

### Post by ghorwin on 2009-02-08
Same problem here. I can run Ubuntu 8.10 and Kubuntu 8.10 live cd without problems. But during the installation, when copying the files the installer hangs at 23%, sometimes it gets to 25%. Then it hangs (the mouse doesn't move, no reaction on keys or cd tray). 

System is also about 5 years old, AMD Athlon XP mobile 2.2 GHz, 768 MB Ram, 60 GB Harddisk and it's a laptop.

I'm trying to install from a Linux Magazin DVD, so there shouldn't be any read issues with the DVD.

Any idea what's going on?

---

### Post by IamHere on 2009-02-08
I got sort of the same problem.. When I try to install Ubuntu, it refuses to install Ubuntu. It doesnt look like the "how to install ubuntu" faq's at all! The computer gives a message like.... 
-----------------------------------
Loading. Please wait...

Busybox 1.11 (some more text)

>
-----------------------------------
After the ">" i can type evrything i want (commands).
It is a sort of... cmd. But it doesnt install.
But anyway, I think i got the sulution for the freezing installation, i think it might help, to start the installation in safe mode.

---

### Post by Kevbert on 2009-02-08
If you've burnt the live CD yourself have you [[COLOR="Red"]checksummed(md5summed)[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded ISO file? You then need to burn the CD at a slow speed to minimize errors (x2 is about right). Next thing to do is check the CD integrity (from the first menu that appears). Next, it's worth checking your memory (as Windows may have worked previously, but may have had the occasional crash for no apparent reason). Again this is in the first menu (memtest). It's worth running the memory test for two or more passes (in case of dust build-up around memory sockets, poor connections etc). You should not get any errors at all.
Now it's time to install. At least 256Mb of free memory is required (which cannot be dedicated to the display adapter). The more memory the better.
If you still have problems it may be that you need to use some special boot options (especially it you get the busybox prompt). See [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/BootOptions"). 
I'm running Ubuntu (slowly) on an old Athlon 900MHz with only 256Mb RAM.
Good luck.

---

### Post by beatgr on 2009-02-08
Installation of Ubuntu Server 8.10
> 
I got sort of the same problem.. When I try to install Ubuntu, it refuses to install Ubuntu. It doesnt look like the "how to install ubuntu" faq's at all! The computer gives a message like.... 
-----------------------------------
Loading. Please wait...

Busybox 1.11 (some more text)

>
-----------------------------------
After the ">" i can type evrything i want (commands).
It is a sort of... cmd. But it doesnt install.

TRY THIS for your BusyBox error during installation
Thanks to earlier posts, suggestions and answers from:
rjromero10;  movingover; Albinootje

Install Ubuntu Server 8.10 from the LiveCD -- per instructions.  I selected the *Guided installation* for the hard drive partitioning (Selection 2, as I remember).

When the Ubuntu install tries to "come up" the first time, you will get the **busybox** - the built-in shell.  

Type **exit**, the server will complete the boot process and provide you with a command prompt, such as: username@server:"$

As **Kevbert** mentioned, check the Boot Options articles.

FOR MY PROBLEM -- THIS WAS THE FIX:
/boot/grub/menu.lst  needed to have: "rootdelay=60" 
inserted in the menu selection lines that look similar to this:
>  
/boot/vmlinuz-2.6.27-7-server root=UUID=492ac531-c353-xxxx-xxxx-xxxxxxxxd913 ro quiet splash
I had 2 such lines in my file, (Ubuntu and Ubuntu recovery mode)

The modified line will look like this:
> 
/boot/vmlinuz-2.6.27-7-server root=UUID=492ac531-c353-xxxx-xxxx-xxxxxxxxd913 ro rootdelay=60 quiet splash

The first command line crates a copy of the file.  
After the last character "`" ... I had to type an additional space (spacebar) for the command to properly execute.
The second command line uses your text editor (nano, mousepad, gkedit, emacs, vi) to modify the lines in menu.lst as shown above.
> 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.`date +~%b-%d-%Y~%T`
sudo nano /boot/grub/menu.lst
Save the file and close your editor.

Now update the grub!
> 
sudo update-grub

Before rebooting the system, you can run update. 
> sudo apt-get update

Good luck!

---

### Post by ghorwin on 2009-02-08
This is related to the original post of arch1234.

I managed to install Kubuntu 8.10 thanks to the workaround posted in

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/253321](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/253321)

Problem is the DMA mode of the CD drive.

---

