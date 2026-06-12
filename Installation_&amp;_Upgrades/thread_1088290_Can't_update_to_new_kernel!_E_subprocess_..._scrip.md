---
title: "Can't update to new kernel! E: subprocess ... script exit 2"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by rbrauns on 2009-03-05
E: linux-image-2.6.28.7-ultimate: subprocess post-installation script returned error exit status 2

HELP!  I cannot update my kernel and all programs now that I manually install using the terminal sudo  apt-get install also come up with error messages that end with E: linux-image-2.6.28.7-ultimate: subprocess post-installation script returned error exit status 2.

I can boot up with the old 2.6.27-11 no problem but trying the new kernel causes a problem.  It won't boot at all.

I found this somewhere on the forums and tried it:

sudo dpkg --configure --pending
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean

sudo apt-get update
sudo apt-get --reinstall install linux-image-2.6.27-7-ultimate

No matter what I do, I get this error:
E: linux-image-2.6.28.7-ultimate: subprocess post-installation script returned error exit status 2

It also happens when I update using Synaptic, the terminal or KernelChecker.

I have searched the forums and can't find an answer anywhere.

How to fix?

---

### Post by martrn on 2009-03-05
Can I ask if you are running [Jaunty Jackalope]("https://wiki.ubuntu.com/JauntyReleaseSchedule") or another version ?

---

### Post by rbrauns on 2009-03-06
Thanks for getting back to me.

In GRUB, I boot from the kernel 2.6.27-11-generic.  If I boot from the 2.6.28-7-ultimate kernel I get an error about not finding boot device and I get a program called initfts or something.

I do have some repositories in my sources list file that say jaunty.  Do I need to uncomment these?

deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) jaunty main 
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

Also some restricted ones:
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse 

I added these to try to fix a network manager problem and reading the forums here to make my system more stable.  It hasn't worked.

---

### Post by Partyboi2 on 2009-03-06
Can you open a terminal and post the output to
```
sudo dpkg --configure -a
``` The lines before>   		E: linux-image-2.6.28.7-ultimate: subprocess post-installation script returned error exit status 2 should give a clue to what is going wrong.

---

### Post by rbrauns on 2009-03-06
here ya go...

Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28.7-ultimate
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28.7-ultimate.postinst line 1181.
dpkg: error processing linux-image-2.6.28.7-ultimate (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28.7-ultimate


I have an ATI video card not Nvidia so is this the problem?

---

### Post by Partyboi2 on 2009-03-06
Your problem could be to do with nvidia-common. Open a terminal and try removing it
```
sudo apt-get purge nvidia-common
```
I am not a 100% sure but I don't think you would need to reinstall nvidia-common afterwards since you are not using nvidia.

---

### Post by rbrauns on 2009-03-06
Hey thanks mate. That worked ! All updates completed now without a single error.

---

