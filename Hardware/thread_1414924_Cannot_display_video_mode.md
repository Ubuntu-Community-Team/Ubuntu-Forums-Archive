---
title: "Cannot display video mode"
date: 2010-02-24
forum: Hardware
---

### Post by dc_atkinson on 2010-02-24
Hi,

I recently installed ubuntu using the wubi installer for windows.    

When i boot up ubuntu I get a black screen with a message saying that it "cannot display video mode".   I am guessing that I need to change some configuration setting however as I have a blank screen I can't access any files. 

Is there a way that I can boot up to a command line interface?   Does anyone know what file i need to edit to get the display settings right for my monitor (which is a Dell).

Any help/advice appreciated.

---

### Post by kyrinae on 2010-03-09
I know, I'm having the same problem, still waiting on replies though.

---

### Post by Joe325 on 2010-03-22
CTRL+ALT+F1 will get you a command line

Im having an issue trying to test a Live CD - v.910 gives me a " Analogue Input Cannot display this video mode"...Even with F4 > Safe mode selected

---

### Post by th1bill on 2011-11-07
Incredibly simple solution after chasing my tail for months on end. I finally went to the documentation and found, in the Terminal run ¨sudo update-grub" and rebooted to see my issue resolved in 11.10.

---

