---
title: "How do I run UNR as a 'live' image?"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by madarieder on 2009-07-20
I recently bought an Asus EEE PC 1005ha preinstalled with Windows XP. I am happy with the OS but.. I have the need to try out new things so I thought UNR would be cool. However, since I don't have a DVD Drive I can't restore my Windows XP if I don't like UNR, so I thought i'd run it as a live image as the installation page said I could do. I've gotten everything installed onto a flashdrive I just have no clue what to do next. any help?

---

### Post by sharonbetts on 2009-07-20
I managed to do this over the weekend.  First insert the thumbdrive. Then you will need to get to the BIOS setup by clicking F2 during the initial bootup - hit it more than once!
Then change the boot order to make the thumbdrive first to boot.

There is an option to boot from "removable device" first - but this did not work!

I also cannot get this version to detect the wireless card on my 1005HA.  I upgraded to the next version (not stable) and the wireless worked, but I get an error on login about windows not saving and needing to load manually.  I can click through the error(s) and all works fine.  Not ready for production, but good to test.

Sharon

---

### Post by madarieder on 2009-07-20
Hey sharon, thanks for your help. I toured UNR for about two minutes.. and its not for me. I guess I'm stuck with 'ole XP.

---

### Post by Rroet on 2009-07-21
Well, I can tell you XP is a lot slower on the 1005ha then linux is. I'm quite happy with it right now.

It's correct that wired and wireless aren't working out of the box. This is a small flaw.

It's easilly corrected by downloading the backports modules deb file and installing it. This will get your wireless working after a small reboot. 

Wired is a different story though, you'd have to download a tarball from the manufactorer and compile it against the kernel headers. Instructions can be found here: [http://ubuntuforums.org/showpost.php?p=7525735&postcount=2](http://ubuntuforums.org/showpost.php?p=7525735&postcount=2)


Kinds regards,

Jelle

I love my 1005ha with 10h of battery life :)

---

