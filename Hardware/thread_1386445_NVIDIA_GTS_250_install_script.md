---
title: "NVIDIA GTS 250 install script"
date: 2010-01-20
forum: Hardware
---

### Post by carbonbased on 2010-01-20
I just visited Nvidia and was given a file named, NVIDIA-Linux-x86-190.53-pkg1.run, as a driver download for my Nvidia GTS 250X video card.

What is the file extension ".run"?  How do I install this file?
--
Also, the 1st time I attempted to get this card to work I got a white screen, followed by a shut-down. So, to make this query I took it out and am running the old card.

If I install a correct driver with the old card in, is Linux going to match up the new card with the right driver on reboot?  Otherwise, I will not be able to run the computer to install the driver with the new card in the computer.

I've seen the EnvyNG thread and I have it installed, however, I cannot use it with the card in the PC. And EnvyNG seems to depend on the card being in the computer in order to find your correct driver.

---

### Post by hemimaniac on 2010-01-20
I believe it would simply be sh ./<nameoffile>.run

some times you may have to sudo chmod +x it first to make it executable, but i have not run into that from anything off the nVidia site

---

### Post by carbonbased on 2010-01-20
> **hemimaniac said:**
> I believe it would simply be sh ./<nameoffile>.run

some times you may have to sudo chmod +x it first to make it executable, but i have not run into that from anything off the nVidia site
How does one boot into ubuntu without X windows?  Each time I try the shell install above I am told my the program that I can't install while I'm in X windows. I used Cntl + Alt + F1, but still got the warning.

Putty! Pft!

---

### Post by Azteka on 2010-01-21
1) Ctrl + Alt + F1
2) stop X ```
sudo /etc/init.d/gdm stop
```
3) cd /to directory/
4) run script ```
sh NVIDIA*
```
5) run X ```
sudo /etc/init.d/gdm start
```

I think you did chmod +x before, so I didn't include this one to the following steps.

---

### Post by carbonbased on 2010-01-21
**How I cured this problem.**
=====================
Go to** Nvidia.com** and look up your video card in the **Download Drivers** section.  When you get to the page for your card, look under the **Addition Information** tab, and at the bottom of the paragraph is a link to **Read Me** pages of instructions. It covers installation instructions for Linux.  In a nutshell, what I did was select the safe boot option at the Grub boot-options screen (pays to have the log in screen at times). From there, select *boot to root* (at the bottom).

Now you're booted and at the command prompt. You're at Run Level 1 and you need to be at RL 3. Type "telinit 3".  From there I went to my directory where I had the **driver file I had downloaded from Nvidia**.  In that directory I typed, "sudo sh <filename.run>".  The filename is long, so just type the first unique letters of the name and hit the Tab key and it auto-completes the filename.  The script will run and you'll have to answer option questions.  Reboot and you're done.

Most of this is likely elementary to experienced users, but *that* I am not. So, I put this here for those new users like me who might have been running Linux for a matter of weeks, like me. =)

Good luck with you're Nvidia installation.

---

