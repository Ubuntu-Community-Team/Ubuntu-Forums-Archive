---
title: "rollback to 8.10 due to installation problem ?"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by iggynig on 2009-04-27
Hi, i just installed Ubuntu 9 and it hasn't installed properly. 

How do I rollback to V 8.10 ?

thanks

Nige

---

### Post by mikewhatever on 2009-04-27
You reinstall. That said, perhaps you can tell us about the problem first.

---

### Post by iggynig on 2009-04-27
> **mikewhatever said:**
> You reinstall. That said, perhaps you can tell us about the problem first.
Thanks for the reply, I was checking for updates last night and saw that there was the new version available. I clicked on instal and it was taking forever so i left my webbook on overnight and when i got up it had crashed. 

I then restarted it and was faced with a blank screen so i restarted it again then did the fault check which allowed the system to start up but the resolution was far to big.

I tried changing the display options and tried every available resolution but they are all far to big for the screen.

As i've only been using Ubuntu for a couple of months i thought re-installing the old version would be a quick fix

Any ideas ?

Cheers

Nige

---

### Post by 24*7 on 2009-04-27
point #1) Always backup before u upgrade. 

In case of continuing error, check 9.04 release notes and see whether ur machine is supported or not.

If it is, in case ur problem doesn't get resolved, u can atleast backup and install 9.04 fresh copy using live CD

---

### Post by iggynig on 2009-04-27
it's a webbook, there aint no CD drive

---

### Post by DJKnut on 2009-04-27
I too am new to Linux.. using an eeePC 900a and eeebuntu.. and started the 9.04 upgrade as I went out for dinner as it forecasted to download in 3.5 hrs... and when I returned, everything was asleep, and an error had occurred... but there was a posted suggestion to issue a command from the terminal..."dpkg -- configure -a" and that resulted in needing to issue a "sudo apt-get install -f" first, then the package manager suggested doing a partial install, and after that (the next morning...) all was well!!  Everything is working correctly, and looks good! KUDOs!!  Dave

---

### Post by mikewhatever on 2009-04-27
> **iggynig said:**
> it's a webbook, there aint no CD drive

In case of a netbook (same as webbook?), Ubuntu UNR would probably be more appropriate. [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook) I also wonder if there was enough disk space for the upgrade.
You could try finishing the upgrade with the following command:
sudo apt-get dist-upgrade

---

### Post by iggynig on 2009-04-27
Thanks for the reply,

i had checked the disk space before installation and there was plenty. I have also tried sudo apt-get dist-upgrade command but it starts the installation then i get the following

dpkg: error processing libchipcard-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

I also tried to download the netbook version of Ubuntu 9 but when I go to install it it say a newer version is already installed

any ideas,

once again thanks to all the replies

Nige

---

### Post by mikewhatever on 2009-04-27
If a reinstall is an option, I'd go ahead and instal UNR-9.04.

---

### Post by iggynig on 2009-04-27
Ok, next question

How do I re-install 8.10 ? 

I have tried dowloading the file from the Ubuntu website, waited half an hour for it to download then it won't open. 

It only asks me if i want to make a CD which I can't due to not having a CD drive. I thought i might have been able to store it on a USB stick but no options to do it

---

### Post by mikewhatever on 2009-04-27
If you have a working Ubuntu, perhaps on another computer, use the utility under System->Admin->USB Startup Disk Creator. If you have a Windows computer, use Untebootin for Windows. You might also want to check the installation guide. [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

---

### Post by Dragonorb13 on 2009-05-08
Here's how to do it. 1) get a computer with a CDR. your's, your friends, you're mom's... doesn't matter as long at it's capable of running 8.10.
2) download Ubuntu Intrepid 8.10 onto that computer.
3) Make a CD of the file.
4) reboot your computer that has the disk burner in it, go into the CMOS and set it to boot from the CD and boot Ubuntu as a LIVE CD.
5) Hook up a USB device of atleast 1/2 gigabyte, then go to System > Administration > USB Start-up Disk Creator and run it.
6) it works just like and Winblows Installation Wizard. follow the steps
7) Insert your USB into your Netbook and boot it up off of the USB and BAM! you're cooking with fire!

---

