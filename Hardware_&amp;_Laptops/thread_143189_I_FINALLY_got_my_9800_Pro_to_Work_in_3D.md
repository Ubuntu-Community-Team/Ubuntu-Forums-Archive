---
title: "I FINALLY got my 9800 Pro to Work in 3D"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by LateNighter on 2006-03-12
Yea I "FINALLY" got my Ati 9800 Pro 256 MB 8x AGP Graphics Card to work.\\:D/ \\:D/ \\:D/ \\:D/ \\:D/  

 Excuse all the Emoticons BUT I'm So Friggin Happy, I've been workin on this for Over 2 months, and Now Thanks to my FRIENDS here on the Forums it actually Works.

 I tried to find the Exact Thread so that I could give you the Link, but I couldn't Find it.
 The Threads Title is: General - HOW-TO: ATI fglrx driver 8.16.20

 It's Author is: mlomker.
 Excuse me mlomker, but I'm going to type the Terminal Command Lines that I used from (YOUR THREAD), in Hopes it'll HELP someone else.

 I HOPE YOU DON'T MIND....;) ;) ;) 

 But mlomker (GETS ALL THE CREDIT)

 Heres the Terminal Command Lines I used to get Mine Going.

 sudo apt-get remove xorg-driver-fglrx
 sudo apt-get remove linux-restricted-modules-$(uname -r)
 sudo dpkg-reconfigure xserver-xorg #Slect the ATI driver

 After this is done as mlomker has SAID a System Reboot is needed to CLEAR the restricted modules from your memory.

 sudo apt-get install xorg-driver-fglrx
 sudo apt-get install linux-restricted-modules-$(uname -r) #0kay
 sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver

 After this I Rebooted my system, although mlomker did'nt say to do this at this point, this was My own little Twist to it, and it "WORKED" 

 This is for the 32bit systems, I don't know if this will work for you but give it a SHOT...   It's Worth the Try,   and you NEVER can tell.....

 THANKS again mlomker I OWE IT ALL TO YOU..... 

 And Thank You to all those for all of their Suggestions as well.

 I couldn't have done it without YOU ALL..... 

 Now it's OFF to PLAY tuxkart I go....

---

### Post by WildTangent on 2006-03-12
Woah...overusage of caps, but congratulations. I wasn't aware there were specific issues with getting the 9800 working.

-Wild

---

