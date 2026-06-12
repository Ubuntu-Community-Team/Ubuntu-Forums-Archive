---
title: "Can't login after installation"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by RatchetRenegade on 2009-09-16
I downloaded the ubuntu-9.04-server-powerpc.iso, burned it on a CD twice (both successful and have the same checksum). Then I attempted to install it on an old G3 PowerMac and everything went flawlessly except after a while I get the message "Installation Step failed: Select and install software".

I get asked what to do and I choose to retry the step "Select and install software."
Everything seems to be working now and a while later it says the installation was successful and wants me to reboot.

After it has rebooted and I get asked for the login and password and I type in exactly what I entered during the installation, but I get "login incorrect". I've entered both the login info a gazillion times and I've also reinstalled the system a number of times with the same and different login info but I still get the same installation error and login incorrect message.

I have no idea why this is happening and it's getting really frusterating!
Thanks a million in advance! :)

P.S. I wasn't sure wether to put this in Installation & Upgrades or the Apple Users forum.

---

### Post by Lofstaf on 2009-10-10
I have no solution but I have pretty much the same problem, except the installation does not give me any errors.
After the installer has finished and the system reboots, I can't login. All I get is "Login incorrect". 
I have tried reinstalling at least ten times, and also tried with different usernames and passwords.
When starting up in rescue mode and looking in /etc/passwd I have no entry for the username entered in the installation.
Have also tried passwd to change the password for root using rescue mode, but no luck.

Hardware is: PowerMac G5 2x1.8GHz, 2GB RAM, 80GB HD.
Ubuntu Server 9.04 for PowerPC.

---

### Post by Lofstaf on 2009-10-10
Hmmm.... I managed to get it to work, finally. What I did:
1. Set the date and time correctly. I used another drive with Mac OS X to do this.
2. Partitioned the disk without LVM.

I don't know which of these steps that made it work, perhaps both?

---

### Post by nmvictor on 2010-05-05
> **Lofstaf said:**
> Hmmm.... I managed to get it to work, finally. What I did:
1. Set the date and time correctly. I used another drive with Mac OS X to do this.
2. Partitioned the disk without LVM.

I don't know which of these steps that made it work, perhaps both?


I have had hard time for the last 48 hours installing and reinstalling jaunty and karmic in my power-book G4 because of this problem, I believe the above quoted text could be the solution, however, I wish more info was provided about the first step: Set the date and time correctly.., in all the installations and re installations, I have not partitioned my disk with LVM, so I believe the first step would solve my problem, please help me achieve this, I am a quite new in both mac and Linux world. Thanks in advance
:sad:

---

