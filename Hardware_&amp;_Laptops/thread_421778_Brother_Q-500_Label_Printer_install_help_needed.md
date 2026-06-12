---
title: "Brother Q-500 Label Printer install help needed"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by billwrtr on 2007-04-24
I've got a Brother Q-500 label printer. The Brother website has drivers that are certified for Debian. 

(Interesting: the links to the drivers do not appear with the Windows and Apple drivers on the Downloads page; but if you keep crusing, you might stumble onto the Linux page where they appear.) 

No mention of Ubuntu, but since Ubuntu is based on Debian, they should work, right? Only problem is figuring out how to extract the files to their proper places so that the Q-500 appears as a choice in the Install Printer routine. Or some alternative. Has anyone out there done this? Or have a clue how to proceed? 

(I'm just one step above Ubuntu noob and close to Social Security so please be gentle.)

Thanks in advance!!!

-Bill

---

### Post by ziggykg on 2007-04-25
Use the Debian drivers and if there's as a HOWTO from the Brother website, please follow it.  I have a Brother printer and I got it to work by just following the nice HOWTO on the Brother website.

---

### Post by billwrtr on 2007-04-25
There's no how to. Just a archive of files. What do I do with them. I'm new at this, remember? BTW, my Brother HL-2040 works just fine using the Brother HL-2060 divers.

---

### Post by jay019 on 2008-02-21
You just right click on the files and select "Extract"
Then you navigate into that directory and click on the .deb files. You need to install the LPR driver first, then the CUPS wrapper second. I still havent got it working yet, CUPS prints a test page fine, but no other programs are able to print to it.

---

