---
title: "Compaq Evo N410c not being nice W200 not working"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by Mimsy on 2006-09-01
I very recently installed ubuntu, my first attempt at Linux ever, with on a gift laptop. The WLAN wouldn't work, but fortunately was pointed [a detailed how-to]("https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200") by a couple of nice forum members. 

Thank you for that, by the way. :) 

I have tried several times to follow the how-to, and have tried to put in the commands in several different ways, but to no avail. My most recent problem is what happens when I try to make sure all the prerequisite packges are installed. I have copied the terminal's response, in the hopes that someone in the laptop forum might be able to help me.


> chili@chili-laptop:~$ sudo apt-get install build-essential cvs linux-headers-2.6.15-26-386 gcc3.4 cpp3.4
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
cvs is already the newest version.
linux-headers-2.6.15-26-386 is already the newest version.
E: Couldn't find package gcc3.4

This is my "write term papers and check emails from my colleg and fromfuture employers"-laptop. I *have* to get the W200 to work. If I can't, I may actually have to go back to That Other OS, with it's memory hogging and bloatware... :-( 

Any and all help is appreciated. I am very ignorant about Linux, so far, but I'm pretty sure I am good at following detailed instructions. :) 

/Mimsy

---

### Post by encompass on 2006-09-01
It can't fine the package your installing... looks liek gcc3.4 have you tried using synaptic?  and you can search for the gcc3.4 program and try installing it.
I can help you more if can't find you way.  I am not at my linux box at the moment.

---

### Post by Mimsy on 2006-09-01
I tried searching for "gcc3.4" in Synaptic, and it came up blank. So I thought for a moment, then did a new search for just "gcc" and it found a ton of stuff. Among the packages Synaptic found in my second search are:

gcc-3.4
gcc-3.4-base
gcc-3.4-doc

Should I install any or all of these three and then try downloading the firmware and then follow the configuration directions in the how-to again?

Thanks,
Mimsy

---

### Post by Mimsy on 2006-09-01
Since I am morbidly curious about anything new, I installed gcc-3.4 and tried configuring the W200 again. I got to the part about downloading the firmware,then things go weird. I have marked the line that puzzles me with bold, to try ane make it esier for people to help me. 

> chili@chili-laptop:~$ sudo apt-get install build-essential cvs linux-headers-`uname -r` gcc-3.4-base cpp-3.4
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
cvs is already the newest version.
linux-headers-2.6.15-26-386 is already the newest version.
gcc-3.4-base is already the newest version.
cpp-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chili@chili-laptop:~$ cvs -z3 -d:pserver:anonymous@cvs.savannah.gnu.org:/cvsroot/orinoco co orinoco
cvs checkout: CVS password file /home/chili/.cvspass does not exist - creating a new file
cvs checkout: Updating orinoco
cvs checkout: Updating orinoco/firmware
cvs checkout: Updating orinoco/net
chili@chili-laptop:~$ cd orinoco
chili@chili-laptop:~/orinoco$ make
make -C /usr/src/linux-headers-2.6.15-26-386 M=/home/chili/orinoco KERNELRELEASE=2.6.15-26-386 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
chili@chili-laptop:~/orinoco$ sudo make install
make -C /usr/src/linux-headers-2.6.15-26-386 M=/home/chili/orinoco KERNELRELEASE=2.6.15-26-386 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make -C /usr/src/linux-headers-2.6.15-26-386 M=/home/chili/orinoco KERNELRELEASE=2.6.15-26-386 modules_install \
                INSTALL_MOD_DIR=kernel/drivers/net/wireless
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  INSTALL /home/chili/orinoco/hermes.ko
  INSTALL /home/chili/orinoco/orinoco.ko
  INSTALL /home/chili/orinoco/orinoco_cs.ko
  INSTALL /home/chili/orinoco/orinoco_nortel.ko
  INSTALL /home/chili/orinoco/orinoco_pci.ko
  INSTALL /home/chili/orinoco/orinoco_plx.ko
  INSTALL /home/chili/orinoco/orinoco_tmd.ko
  INSTALL /home/chili/orinoco/orinoco_usb.ko
  INSTALL /home/chili/orinoco/prism_usb.ko
  INSTALL /home/chili/orinoco/spectrum_cs.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
/sbin/depmod -ae
chili@chili-laptop:~/orinoco$ cd firmware
chili@chili-laptop:~/orinoco/firmware$ ./get_ezusb_fw
./get_ezusb_fw: line 26: curl: command not found
**./get_ezusb_fw: line 40: ezusb.drv.pkz: No such file or directory**
436+0 records in
436+0 records out
6976 bytes (7.0 kB) copied, 0.00373 seconds, 1.9 MB/s
chili@chili-laptop:~/orinoco/firmware$


The firmware doesn't exist anymore? Or am I just typing in the commands all wrong? I still don't understand the command line in Linux, so that's a distinct possibility.

/Mimsy

---

### Post by encompass on 2006-09-01
it said you don't have the curl command installed.
sudo apt-get install curl
if that works... try the make command from there...
Just a guess...

---

### Post by Mimsy on 2006-09-01
And tonight I have learned that when the terminal says it can't find something, I need to search the ubuntu wiki and forums for information on how to install that something, because it's probably important. In retrospect, that one line should probably have made me wonder...

The little green light on the W200 is on now, and everything seems fine again. Next time the laptop is on campus I will test to see how good it is at connecting... but activating it was the main issue.

THANK YOU! \\:D/ 

/Mimsy

---

### Post by encompass on 2006-09-01
Good job... it ireally ins't that hard... and if companies would start opening there drivers and not trying to keep them secret, Ubuntu and oth linux versions could start making drivers that work on plug and play.  Linux is great when the drivers are open by the company.  But are much harder when made without knowledge and end up hacking.

---

### Post by Mimsy on 2006-09-01
Thank you, and no, it really isn't, once I know what to type in the terminal and what the command does.

Tonight's project is to get all those resctricted formats worked out, since my whole music collection is in mp3.

I might be back with a whole new set of questions soon. :)

Thanks for helping,
Mimsy

Late edit: Ah, the glory of wireless...! Now if only I could learn not to spill donut crumbs over the keyboard. :(

---

### Post by sas on 2006-09-04
Was it installing gcc3.4-base that fixed the original problem?

I'll add curl to the wiki page - I never noticed it before because I always install it anyway.

---

### Post by Mimsy on 2006-09-04
Well, I didn't notice that curl was missing until gcc-3.4 was installed, since I didn't get past that part of the installation until after that was taken care of. Then I made it further, the terminal told me curl was missing and encompass was nice enough to dechiffer that for me. So I installed curl as well, and everything was fine from then on.

It could have been the gcc-3.4, it could have been the curl, it could have been both. I don't think I could have gotten the W200 to work without installing both, but I don't know enough about the inner workings of Ubuntu to do more than speculate on that. :) 

Thanks,
Mimsy

---

### Post by encompass on 2006-09-04
Thanks for the thanks Mimsy... always nice to hear the credit... even if I didn't do much.:mrgreen:

---

### Post by Mimsy on 2006-09-05
Well, "much" and "enough" are hardly ever synonyms. And my parents taught me to always say "thank you" when someone helped you fix a problem you can't fix on your own. So technically you should thank them, not me. ;)

/Mimsy

P.S. 

Since I'm so ignorant about everyting Linux I doubt I could even boot my laptop without searching for instructions on these forums. You think I'd be stupid enough to risk losing access to this goldmine of information by being rude and unappreciative to the ones providing it? Never. :mrgreen:

---

