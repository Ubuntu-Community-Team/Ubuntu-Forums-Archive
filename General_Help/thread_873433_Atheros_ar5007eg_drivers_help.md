---
title: "Atheros ar5007eg drivers help"
date: 2008-07-29
forum: General Help
---

### Post by Teriaki 511 on 2008-07-29
I'm (sort of) new to ubuntu, everything seems to have set itself up right out of the box, except for my wireless card...

I'm using a Toshiba Satellite a215 with an Atheros ar5007eg built in wireless card, hardware drivers say that HAL and support for Atheros cards are enabled, but nm-applet doesn't notice that I have a wireless card and I can't connect to my wireless network... I've tried Ndiswrapper, but when I follow instructions, terminal complains that I'm missing a set of files, throws errors at me, and afterward, running Ndiswrapper brings up the message "no utils found" 

Any help would be excellent, thanks.

---

### Post by DagMan on 2008-07-29
I had this problem.  The instructions here are specific to my laptop, so don't download the custom kernel with the module included already, but have a look at the part to compile wifi [http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly#enabling_wifi](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly#enabling_wifi)

Also, there was recently a thread about toshiba laptops with this card up in the absolute beginner forum, and I think it was someone with your same computer or with the same computer series.

In mine, I had to additionally disable the restricted modules from running at boot and put the module in /etc/modules, though I think it would be just as well to deselect the driver in the manager, then add the module ath_pci to the /etc/modules file.

---

### Post by Teriaki 511 on 2008-07-29
i found the thread you were talking about, but the .tar file in that thread, as well as in the link you posted, only contains a readme, which tells me to go download the latest package, and when i do, and continue with the tutorial, i get this: ```
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory

```
and the same stream of errors i get if i try to install ndiswrapper, maybe I've overlooked downloading something?

---

### Post by phidia on 2008-07-29
To use [ndiswrapper]("http://ubuntuforums.org/showthread.php?t=574501&highlight=Atheros+ar5007eg") and for [madwifi]("http://ubuntuforums.org/showthread.php?t=792158&highlight=Atheros+ar5007eg").
BTW I had a HP laptop with the ar5007eg card-once wireless was working resume wouldn't work right & no tweaking/configuring/swearing would get it to work.

---

### Post by DagMan on 2008-07-29
> **Teriaki 511 said:**
> i found the thread you were talking about, but the .tar file in that thread, as well as in the link you posted, only contains a readme, which tells me to go download the latest package, and when i do, and continue with the tutorial, i get this: ```
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/will/madwifi-ng-r3366+ar5007/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory

```
and the same stream of errors i get if i try to install ndiswrapper, maybe I've overlooked downloading something?
Are you sure you installed the build-essential package?  It looks like that could be the problem.
As for the proper package, I think that likely you already found it, but just in case, and assuming you just need to install build-essential, here's a link [http://snapshots.madwifi.org/special/madwifi-hal-0.10.5.6-r3698-20080604.tar.gz](http://snapshots.madwifi.org/special/madwifi-hal-0.10.5.6-r3698-20080604.tar.gz)

---

### Post by Teriaki 511 on 2008-07-29
i get the same errors with all three solutions, looking at the code, it looks like I'm missing these header files:

<stdio.h>
<errno.h>
<getopt.h>
<string.h>
<stdlib.h>
<stdarg.h>
<sys/fcntl.h>
<sys/stat.h>

was I supposed to download these seperate?

EDIT: i tried "sudo apt-get install build-essentials" but terminal says it "can't find package build-essentials", but using synaptic package manager, i was able to install it, things seem to be running a lot smoother now

---

### Post by Teriaki 511 on 2008-07-29
thanks to ndiswrapper, i was able to get ubuntu to recognize my wireless network, but now it won't connect to it! it's set to wpa2 personal, and according to vista it uses AES, but it stalls at "waiting for Network key from wireless network" i know the passphrase is correct, what else could i be missing?

sorry for the double post...

---

### Post by Teriaki 511 on 2008-08-01
-bump-

no ideas?
lowering the security isn't an option

---

