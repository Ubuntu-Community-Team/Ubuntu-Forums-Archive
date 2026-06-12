---
title: "Req help remastering mini.iso network install CD"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by med458 on 2009-01-27
Hello my friends.  I am working on a remastering project.  The ultimate result would cause the 9.9 MB mini.iso network boot CD to boot directly into a text-based application I have already compiled with no prompting at all.  I am having great difficulty locating the scripts that control prompting.

My goal is this:  
1)  I would like to eliminate the main menu that gives the user the option of installing or booting live.  I would like the CD to default to booting live.
2) I would like the language to default to US English and the keyboard to default to US English, all with no prompting whatsoever.
4)  Essentially, I would like my non-gui application to start right after the computer is powered on (but I do want all drivers to load silently in background).

I have experience remastering live CD's and using the loop util.  I have searched all around the root directory of the network install CD, as well as in initrd.gz.  I do not know how to uncompress the 2.1 mb "linux" file.  I have failed at locating any scripts that pertain to the above-described prompts or menus anywhere in the uncompressed .iso.  /lib/ and /sbin/ look promising, but do not appear to contain any menus or prompts.  I will give 10 internets to anyone who can point me in the right direction.  Thank you my friend.

---

