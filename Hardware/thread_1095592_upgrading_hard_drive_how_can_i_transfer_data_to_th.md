---
title: "upgrading hard drive how can i transfer data to the new hard drive?"
date: 2009-03-13
forum: Hardware
---

### Post by sansa dude on 2009-03-13
ive just gotten a 40gb hard drive to replace my 10gb hard drive for my dell laptop. is there a way i can like transfer my programs to a flash drive or my 30gb hard drive on my computer VIA network? or will i have to re install all of it? i know i can simply copy the HOME folder and put it in the new one when i install.any suggestions?

---

### Post by aesis05401 on 2009-03-13
There are a couple strategies for doing this.  If you can have both hdds running simultaneously, then you can boot through GParted utility cd, mount both drives, and simply move the entire image from the 10g to the 40g.

If this is not possible, then you can use the dpkg --get-selections command in combo with a backup of your /etc/apt/sources.list file to at least rebuild your package base.  First you build a list of installed packages, and copy the list of source repos from your existing install.  Put these files on the new machine, copy the /etc/apt/sources.list file into the right directory on the new drive, and then feed apt the list of packages to retreive (download and install from the repositories) all the packages onto the new machine.

Then you would transfer your data folders via USB because all your newly installed packages are virgin.  There are instructions for doing this all over the web.. a search for 'Ubuntu dpkg clone' just pulled up some Debian based instructions for this process. 

Finally, it is possible to make a custom install cd from your current installation, but I have never done this, only heard about it.

---

