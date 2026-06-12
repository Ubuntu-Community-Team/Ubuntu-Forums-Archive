---
title: "Sudo dpkg --configure -a (Doesn't Work)"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by php99 on 2009-07-06
Sudo dpkg --configure -a

I try to run it but it crashs the whole OS and the Update Manergerl tells me to run it.

So i run it in the command box thing; and it starts 'working' but it only reads the first entry which openoffice, mailmerge as far as i can remember then EVERYTHING crashs.

I tryed loading up recovey mode and select the dpkg option which that spotted an recering error. 

So what can i do to get the command working and allow me to install and update again?

Thankyou all
Paul

P.S Sorry if its in the wrong place

---

### Post by earthpigg on 2009-07-06
can you give us more background on your problem?

and copy/paste the output when you enter the problematic command in the terminal?

(terminal = command box thing)

---

### Post by php99 on 2009-07-06
more information;

Erm...

Well i 1st found out the problem when i wanted to install soome new software. 

It told me that dkpg was interupted and i need to run dpkg --configure -a

So i did run 'sudo dpkg --configure -a'

It  crashed the whole OS i couldnt do anything, except move the mouse, i couldnt load up a program or anything; just move the mouse.

So i thought maybe it might work in the recovery mode.

It gives sevral options to run;
Boot System start using applications
dpkg repair the dpkg
and some others that i can't remember

so i ran the dpgk and it spotted an error ill reboot try it again when i have finished this post and tell you the error.

Is that enough information; what else should i say?
Thankyou All again
Paul

P.S rebooting now and ill give you the error i get.

---

### Post by php99 on 2009-07-06
Okay!

heres what i get

Lots of lines that i can't read because it goes to fast.

Then the bottom to lines which are

end trace 4b124abd53691d7
Fixing recursive fault but reboot needed

I left it for 2 hours once and nothing changed; it didn't crash because i could type, all though when i tryed doing a command nothing happened.

So i reboot with the switch on my PC.

So what shall i do it get this dkpg thing working.

Thankyou all Once Again
Paul

---

### Post by washakie on 2009-07-06
I am having the same problem. I should note, I am using karmic repositories and tried a dist-upgrade (I needed the freshest python packages).

It seems the problem ultimately stems from cups and/or intramfs-tools. Below is the output. I have run apt-get update, apt-get upgrade, and several other tries after reviewing the forum posts, but I still have no success. I remember at one point a while ago having a similar problem and it seemed deleting some packages so that they were redownloaded helped, but I can't recall where this takes place.

Thanks!

OUTPUT:

jfb@niflino:/var/cache$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
jfb@niflino:/var/cache$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu33) ...
update-initramfs: deferring update (trigger activated)

dpkg: error processing cups (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of foo2zjs:
 foo2zjs depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing foo2zjs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-driver-gutenprint:
 cups-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.
dpkg: error processing cups-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on cups; however:
  Package cups is not configured yet.
 ubuntu-desktop depends on cups-driver-gutenprint; however:
  Package cups-driver-gutenprint is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ghostscript-cups:
 ghostscript-cups depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing ghostscript-cups (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic
cpio: ./lib/udev/vol_id: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-13-generic
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by earthpigg on 2009-07-07
have either of you tried system -> administration -> synaptic package manager -> edit -> fix broken packages?

---

### Post by raymondvillain on 2009-07-09
I would like to try that but in my case synaptic will not even start.

I get a message box with this error:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Then synaptic just goes away as soon as I click anything.

---

### Post by earthpigg on 2009-07-09
maybe give this a try:

```
sudo dpkg -C
```
(capital C, not lower case c)

from the manual:

```
        -C, --audit
              Searches for packages that have been installed only partially on your system. dpkg will suggest what to do with them to get them working.
```

---

### Post by raymondvillain on 2009-07-13
SOLVED!

Finally, sudo dpkg -a finished and things are working correctly, for now, anyway.

Thanks for all the help.

---

### Post by earthpigg on 2009-07-14
care to specify *what* exactly solved it? you aren't the only one here to learn :D

---

