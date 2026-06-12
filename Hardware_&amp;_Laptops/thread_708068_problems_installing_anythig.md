---
title: "problems installing anythig"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by Dogmaster on 2008-02-26
hey im new to the linux way of life. finding it difficult to adapt but trying damn hard.when i try to install automatix from www.getautomatix.com an error comes up with the download as follows

Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/tango-icon-theme/tango-icon-theme_0.8.0~cvs070515-0ubuntu1_all.deb Could not resolve 'archive.ubuntu.com'

Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/tango-icon-theme-common/tango-icon-theme-common_0.7-0ubuntu1_all.deb Could not resolve 'archive.ubuntu.com'

im going through a windows network for net access any help would be grand

p.s it says ti check installation medium?

---

### Post by em3raldxiii on 2008-02-26
Well, I know this doesn't help your issue, but those of us who've used Ubuntu for a long time generally recommend against using automatix.  In fact, there are those who will tell you that using Automatix is not safe for most users.

It would be better if you told us specifically individual types of things you are trying to do ... such as how to install codecs, etc.  I can tell you that I have never  had 100% good luck with using automatix ... it always managed to break something, or just make something "messy".  

What I would recommend is to do this:

```
sudo aptitude install -f
``` which will check for broken installation packages and stuff, and offer solutions to fix them.  Make sure you read any outputs before you enter "yes" to any questions it might ask (it may not ask any).

Then install specific things one at a time.  We will help :D I promise!  For new users such as yourself, I recommend using Synaptic Package Manager for installing most things.  But learning to install things with the command line is a good idea because it's really fast.  You may have to enable additional repositories for some software, so if you can't find something specific, let us know and we'll steer you in the right direction.

---

### Post by FrancesL on 2008-02-26
What I would recommend is to do this:

```
sudo aptitude install -f
``` which will check for broken installation packages and stuff, and offer solutions to fix them.  Make sure you read any outputs before you enter "yes" to any questions it might ask (it may not ask any).


Thank you for this...I was just cruising the threads and found this. Used the CLI and it found and removed a load of things which it flagged as unused. I wouldnt have had any idea other wise.

---

### Post by Yellow Pasque on 2008-02-26
It sounds like a connection issue. Do other internet apps work?

---

### Post by Dogmaster on 2008-03-09
followed the advice didn't say anything was wrong and it came back as following. 



dogmaster@ACER:~$ sudo aptitude install -f
[sudo] password for dogmaster:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done 


assuming this doesn't help. i am thinking that it may be something to do with the wireless network i am connecting through.

---

