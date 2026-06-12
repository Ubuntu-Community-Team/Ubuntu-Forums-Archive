---
title: "Running Wubi"
date: 2008-08-15
forum: General Help
---

### Post by kwinslow on 2008-08-15
I ran the installer, but not sure how to run it after it is installed.  I am blind and using a screen reader.  In other words I use speech to read the screen.  I could sure use some help with this.  Thanks.

---

### Post by Orlsend on 2008-08-16
I wish I could be of better help

If you install it (ubuntu)

re-start you pc and select the Ubuntu Option rather than the default one (If yopu have only one version of windows then you should be able to just restarta and hit the "down" key once and then hit enter (warning there is a timer, if you dont  do in less then 12 seconds it will load your default OS)

If you done this correctly it should load and create some folder and do some, settings this could take a while.

when its finished it will reboot and you need do the step number 1 (choosing to ran ubuntu instead of windows).

But this time it will take you to your login screen, by default you type your username fisrt and then your password, if you done it correctly you should hear the ubuntu loadind music (Like a african drum mixed with aura)

then you are done!

If you dont understand any of the step feel free to ask any questions

---

### Post by alzie on 2008-08-17
I'm assuming the screen reader is a Windows program.  The screen reader for Ubuntu is Orca. 

The link for Orca is: [http://live.gnome.org/Orca](http://live.gnome.org/Orca)

Orca can be activated by typing alt + F2 to open the run application box and typing orca and enter. 

I am not personally familiar with using Orca but I hope I've given you enough information to get you started.

---

### Post by Fox Johnston on 2008-08-17
Waddaya know, another blind newbie.  I too am blind and attempting to test drive Ubuntu via the Wubi install.  I am not sure how far you got, but this is where I am at currently.  I ran Wubi, rebooted, and upon first reboot, selected Ubuntu with sighted assistance.  Now I know it takes about 20 seconds after my scanner wakes up before I can down arrow to select Ubuntu and hit enter.  After the reboot, Ubuntu began completing the installation, my sighted Wife enjoyed the background and I even heard Orca speak once during the process.  However, upon 2nd boot, after selecting Ubuntu, I was brought into Grub, no Orca here and clueless as what to do next.  I can almost taste it...

---

### Post by alzie on 2008-08-17
I believe if you follow orlsends instruction in grub and hit the down key once then hit enter you should go into ubuntu.

After Ubuntu loads you should get a prompt for your user name and password.  I'm afraid I don't know how long that takes, it could be different on different computers.

I hope this helps.

---

### Post by Fox Johnston on 2008-08-18
Hmmm.  Well as I said, I already hit down arrow, selected Ubuntu and hit enter.  Where I end up is not at log in but a Grub command line with a flashing cursor.  The only successful thing I have done from here is type reboot.  My wife tells me there are plenty more commands to arrow through if I hit tab from the command line, and even more options if I hit escape.  Is this more clear as to where I find myself?
> **alzie said:**
> I believe if you follow orlsends instruction in grub and hit the down key once then hit enter you should go into ubuntu.

After Ubuntu loads you should get a prompt for your user name and password.  I'm afraid I don't know how long that takes, it could be different on different computers.

I hope this helps.

---

### Post by Orlsend on 2008-08-18
Oh You might have "Initramfs" Problems, this is usually caused by a bad shut down or some software installed in windows that causes to look like a bad shut down, Usually just turning ON your computer and then loading windows with out logging into windows and then when you get to logging screen click the "shut down" option. This Usually takes care of the "Initramfs" (allowing you to continue with Linux with the instructions I gave Above) if not then You may have to run a HD check on windows to check for errors.

---

### Post by Fox Johnston on 2008-08-18
Ah ha!  This makes sense and is consistant with what I am experiencing lately with this system and BSODs.  I guess it is time to dust off my copy of Spinrite and fix the hd.  Would you suggest reinstalling after I repair the hd?  Thank you.
Fox

> **Orlsend said:**
> Oh You might have "Initramfs" Problems, this is usually caused by a bad shut down or some software installed in windows that causes to look like a bad shut down, Usually just turning ON your computer and then loading windows with out logging into windows and then when you get to logging screen click the "shut down" option. This Usually takes care of the "Initramfs" (allowing you to continue with Linux with the instructions I gave Above) if not then You may have to run a HD check on windows to check for errors.

---

### Post by Orlsend on 2008-08-18
Try checking for errors with Ubuntu installed, If not try reinstalling it.

At the end if not of them work maybe do a defrag on Windows

---

### Post by molochi on 2008-08-19
When I get the "Initramfs" prompt, I go back into windows and just run chkdsk. Wubi installs are actually running in a NTFS partition so use windows or a windows program to fix problems with the disk. So far I haven't had to do more than run chkdsk.

---

### Post by benhur99ph on 2008-08-20
Yes! molochi is right. Since Wubi runs ubuntu on NTFS, it is more vulnerable to hard reboots and will decrease performance over time. I think defrag or chksk is a way around this problem.

---

### Post by Fox Johnston on 2008-08-21
I want to thank everybody for their replies.  I guess I should also apologize to the original poster for the highjack.  I have also discovered that I have been ignorantly been trying this on a raid 1 configuration and that Wubi/Ubuntu is not ready for that yet, oops.  That said, I think I might rethink the raid before waiting for 8.1.  This will make things easier for me in several respects.  Spinrite also would not run on the raid 1, I would have to physically detach from the raid controller and reattach to the ide channels and back and forth.  That and there are plenty of backup options out there as an alternative to the lazy raid 1.  Thanks again for helping a newbie get started and rethink his rig.
Fox

---

