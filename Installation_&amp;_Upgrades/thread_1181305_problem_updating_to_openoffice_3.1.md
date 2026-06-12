---
title: "problem updating to openoffice 3.1"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by johnapeterson on 2009-06-07
Hello all,

I am having a problem trying to update openoffice to 3.1 on unbuntu 9.04.  For some reason, the system freezes up on me.  When I open synaptic I get the follwoing message in a window:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

If I try to remove the old version of openoffice it will get to the point where it says:  Removing openoffice.org-writer2latex   and then go no further.  At that point I cannot open any other window, and have to hit the reset button on the computer to reboot the system.

Thanks for any help.

---

### Post by s3MA00RRNY on 2009-06-07
Did you follow the directions and try 'sudo dpkg --configure -a' in the terminal? That might help.

---

### Post by johnapeterson on 2009-06-07
When I type in sudo dpkg --configure -a  the response is:

john@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for john: 
john@ubuntu:~$ 

(should I be getting some type of message?)

After I do that when I go into Synaptic I press the ¨Mark All Upgrades¨, and then ¨Apply¨.  It downloads the Openoffice 3.1 files and tells me that it will remove 1 file (openoffice.org-writer2latex).  After downloading the files it gives the message ¨Removing openoffice.org-writer2latex¨, goes no where, and then I cannot open other windows and need to restart the machine.

Thanks

---

### Post by johnapeterson on 2009-06-08
I should have mentioned that openoffice.org-writer2latex is still on the computer when I restart, and repeating the process gives the same results.

Thanks for any help.

---

### Post by johnapeterson on 2009-06-08
I just tried sudo dpkg --force all --remove openoffice.org-writer2latex in the terminal and am getting the same results.  

I cannot open windows, but my mouse is still able to move on the screen, and I have to hit the reset button to get the computer operating again.

Thanks for any help.

---

### Post by johnapeterson on 2009-06-08
When the computer restarted, I went into the grub menu and choose recovery mode and choose the ¨Fix broken Packages¨ option.  After pressing ¨d¨ for details, it gives me the list of Openoffice files it will install, and the removal of openoffice.org-writer2latex.

Continuing with the installation in gives a bunch of address (I guess), and finally a line that says:

[135.739009] Fixing recursive fault but reboot is needed!

After leaving it be for 20 min, I come back and the same message is there on the screen.  It does not seem to be doing anything.

After restarting the computer, I am still having the same problem.

Thank for any help.

John

---

### Post by s3MA00RRNY on 2009-06-08
Try booting into recovery mode and using fsck. It might find some errors. You also are having trouble getting into Windows? So you dual-boot? Or are you talking about having trouble getting into GNOME?

---

### Post by johnapeterson on 2009-06-08
Actually, I only use ubuntu.  I do not have a dual boot machine.  Sorry if that confused anybody.

Went into recovery mode and choose the ¨fsck¨ option.  The screen says:

mount: /is busy

Then goes back to the boot option screen.

If I drop down to a shell and type ¨fsck¨ it gives me a worrying that doing so on a mounted drive is not advisable.

Thanks for any help.

---

### Post by johnapeterson on 2009-06-09
I got it.  There seem to be a conflict with openoffice and the real time kernel.  After installing the generic kernel and booting to it, I was able to remove the package.  Openoffice does not seem to operate with the real time kernel, but is doing fine with the generic one.  I guess that is another problem for another thread.

Thanks for everyone help.

---

