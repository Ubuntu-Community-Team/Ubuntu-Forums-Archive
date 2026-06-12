---
title: "How I fixed my Broadcom bcm4311 driver problems"
date: 2011-05-01
forum: Hardware
---

### Post by KiLLeRfriend on 2011-05-01
I fixed my problem with the Broadcom bcm4311 drivers on 11.04 (Natty Narwhal)

Steps I took for fixing this problem: (I stole this method from [http://ubuntuforums.org/showthread.php?t=1700897](http://ubuntuforums.org/showthread.php?t=1700897)[user:nm_geo; post #5])

-open the 'Synaptic Package Manager' and search for 'bcm'

-uninstall the 'bcm-kernel-source' package

-make sure that the 'firmware-b43-installer' and the 'b43-fwcutter' packages are installed

-type into terminal:

[cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl']

(you may want to copy this) and see if the term 'blacklist bcm43xx' is there

-if it is, [terminal]cd /etc/modprobe.d/ [and then]sudo gedit blacklist.conf

put a # in front of the line: blacklist bcm43xx

then save the file (I was getting error messages in the terminal about not being able to save, but it actually did save properly)

-reboot

hopefully this works for you all!

---

### Post by steve19137 on 2011-06-11
hey, it worked like a charm! like others i assume, i tried so many things, and now it actually works :D amazing!

---

### Post by lovinglinux on 2011-10-19
This also solved the problem on Ubuntu 11.10.

Thanks.

---

### Post by yachtmango@hotmail.com on 2011-10-28
Confirm this solves bcm4311 on lubuntu 11.10. The key step is the complete removal of 'bcm-kernel-source' package using Synaptic Package Manager. I also needed to remove the blacklist on bcm43.

Thank goodness for this forum.  Thank you to previous contributors.

Note not using the STA driver at all despite the suggestion to download restricted drivers.

---

### Post by intruderukr on 2011-12-07
Be careful, I followed these directions and lost my wired connectivity!
I looked around the forum and found the broadcom drivers which I have installed.  Now I have wireless, but no ethernet... 
I'm using Dell Inspiron E1405 with Oneric.

---

### Post by bluexrider on 2011-12-07
good fix need to make this a sticky

---

### Post by Failo997 on 2011-12-18
Tried a bunch of solutions.  

This one finally worked for my wireless router.  Thanks!!

It is a broadcom bcm 4311 but Acer lists it as a Acer InviLink 802.11b/g router.  

I followed the steps above except. 

 Ubuntu 11.10 does not come with Synaptic Package Manager installed.  It is easy to find in the Ubintu software center though.  Just search install and follow the steps above.

---

### Post by José Cardoso de Almeida on 2011-12-20
Thank you very much for sharing solution. Worked on my 11.10.

Cheers!

---

### Post by poppypundit on 2013-01-14
Worked like a charm on  LINUX MINT 14. b43-fwcutter worked in Mint 12 and 13 but did not work on Mint14. 

1. Mint 14 came with no bcm-kernel-source so i did not have to uninstall 
2. bc43 -fw cutter installed 
3.  Go to Home -->File--->etc---> modprobe-d---> 
4.  Rt click blacklist.config and open as administrator
5. As the thread says, add # . Mine  read " #blacklist bcm43xx "  with no inverted comas. 
6. Restarted and was fine . 

Thank you . Dont know what id have done without you folks.

---

