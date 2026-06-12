---
title: "2 problems"
date: 2008-07-15
forum: General Help
---

### Post by whalogreg on 2008-07-15
8.04 has been just a little disappointing...

The first problem I've been running into is with update manager/package managers/problems in terminal when updating anything...
I've been getting an error saying "Unable to get exclusive lock. This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.". I get this error no matter what, even immediately after rebooting, when I am sure there are no other package management apps are running...

The second has been a long hard battle with getting my radeon card and/or driver (i'm assuming) to work properly so I can enable things such as desktop effects, and 3D graphics to work properly... I've followed the instructions from just about every thread I could find in the forums... I've followed ATI's download and intallation instructions, and most recently the driver instructions here.... [http://www.phoronix.com/forums/showthread.php?t=9951](http://www.phoronix.com/forums/showthread.php?t=9951)

No matter what I do, I either freeze after the logo screen on boot, or when I try to enable desktop effects the screen turns white for about 60 seconds (mouse cursor still visible) and then reverts to no effects enabled... I don't know, didn't have any problems like this with 7.10 with the same hardware... 

never had either problem with 7.10.. anyone have a clue?

---

### Post by cmnorton on 2008-07-15
As to your post title, I suggest that in future you use a more descriptive name, and split the two problems into different posts. It's not a biggie, just a suggestion.

As to the first problem, I assume this continues after reboot. Does anything interesting show up in ps -ef? You probably did shut down another dpkg update instance, but sometimes things hang around.

Also, have a look at this link: [http://ubuntuforums.org/showthread.php?t=97473](http://ubuntuforums.org/showthread.php?t=97473)

As to the second problem, hopefully one of the desktop knowledgeable ones will answer that. I struggle with graphics stuff.

---

### Post by PmDematagoda on 2008-07-15
About the ATi problems, did you only try fglrx or did you try using the open source ati driver as well?

---

### Post by whalogreg on 2008-07-15
> **PmDematagoda said:**
> About the ATi problems, did you only try fglrx or did you try using the open source ati driver as well?

I've tried the driver from ati, evny, fglrx, open source... I've tried everything and can't get anything to work...

---

### Post by sowelie on 2008-07-15
I recently set up my parents computer with desktop effects.  They are running on an ATI X700.  I found that the ati drivers worked best.  What happened when you tried to install the ati drivers?

---

### Post by whalogreg on 2008-07-15
> **sowelie said:**
> I recently set up my parents computer with desktop effects.  They are running on an ATI X700.  I found that the ati drivers worked best.  What happened when you tried to install the ati drivers?

ok, here's what ati's site told me to do...

"1.  Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux driver download.
2. Enter the command ati-driver-installer-8-6-x86.x86_64.run to launch the ATI Proprietary Linux driver installer. The ATI Proprietary Linux Driver Setup dialog box is displayed."


and here's what I got when I "navigated to the ati proprietary linux driver" and entered the command "ati-driver-installer.... ect" as instructed...

"bash: ati-driver-installer-8-6-x86.x86_64.run: command not found"

this confused me, so to make sure that I was in the right directory, i typed "dir" in the terminal and it displayed "ati-driver-installer-8-6-x86.x86_64.run" in the list...

---

### Post by inteluser on 2008-07-15
You may need to type "./ati-driver-installer-8-6-x86.x86_64.run" instead of "ati-driver-installer-8-6-x86.x86_64.run" to get the (script, I presume) to run.  You may also need to "chmod u+x ati-driver-installer-8-6-x86.x86_64.run" to mark the file as executable.

---

### Post by Taxman415a on 2008-07-15
For the update manager issue this can happen when one of the package managers fails to clear it's lock file. There are a couple places they can be. Googling for your error brought this link which shows the ways to solve it. [http://www.ubuntux.org/synaptic-sudden-reboot-exclusive-lock-problem](http://www.ubuntux.org/synaptic-sudden-reboot-exclusive-lock-problem)

---

