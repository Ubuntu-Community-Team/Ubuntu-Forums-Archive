---
title: "installing swiftweasel"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by redshift88 on 2009-07-16
Hello,

I'm new to ubuntu, but took a class a few years back on command line and C code, so I thought I'd give ubuntu a shot.

I searched and found some information, but not enough to help me.

I'm trying to install swiftweasel RC3 so I can watch streaming video from abc.com and fox.com.  I tried using firefox with WINE, but I only hear the audio.  Someone commented on how swiftweasel works in this situation, so I downloaded it for my intel laptop and extracted the folder, but now I'm not sure how to install it from there.  I'm sure the answer is very easy, but please bear with me.  The file i extracted from was a tar.gz format.

Thank you

---

### Post by Partyboi2 on 2009-07-17
Hi, once you have extracted it if you are not already change into the newly extracted source directory eg If you extracted it to your home directory
```
cd swiftweasel
``` then run it with
```
./swiftweasel
```If you want you can also create a launcher for it from the Desktop by right clicking and choosing "create launcher" and then fill out the details

Name: Swiftweasel
Command: (browse to the extracted source directory and select the 'swiftweasel' file)
Comment: Leave bank or add something.

You can also change the icon for it b clicking on the pic to the left.

---

### Post by redshift88 on 2009-07-19
Thank you.  That worked and was simple.  

I'm running the 32bit version of ubuntu on a 64bit laptop.  There were two choices for swiftweasel: one with an intel x86 in the name and another with intel x86 64.  I'm using the x86 since I'm using the x86 version of ubuntu.  Is this the right thing to do?  I promise this is my last question on this subject.

I finally have my laptop set up the way I want it. :)

---

### Post by SuperSonic4 on 2009-07-19
Yes that is the correct one to have. Chances are it would throw up an error if you tried the x86_64 anyway

---

