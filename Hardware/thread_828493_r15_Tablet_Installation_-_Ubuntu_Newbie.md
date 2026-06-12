---
title: "r15 Tablet Installation - Ubuntu Newbie"
date: 2008-06-13
forum: Hardware
---

### Post by todomartinez on 2008-06-13
Hi,

I'm commited to Ubuntu.  I have it running great on my kid's desktop computer.  And, to a great extent, it is working fine on my Toshiba Tablet PC r15-s829.  But, the pen tablet is not.  There seems to be a myriad of different posts across the internet that seem to document how to make the tablet work.  The bottom line is that I don't know which way is the right way.  Can anyone help me with the specific steps to make UBUNTU 8.04 work with my TABLET PC.  I use it extensively to teach math with a projector and MS Office Onenote.

Thank You
JJM

---

### Post by todomartinez on 2008-06-14
I can't believe how hard it is to try and setup my Tablet PC.  I've been trying to get the tablet pen working for a week and I still have nothing to show for it.  It really shouldn't be this hard.  Also, playing DVD's is a pain as well.  I would have switched all of my home computers to Ubuntu if it wasn't for these issues.  Is one out of three bad, or good?  That's only a 33.33% success rate.  If that was a passing percentage in football it would be attrocious.  But, if it was a batting percentage in baseball, it would be considered good.  I've been an on and off again user of Ubuntu since 2005.  I'll probably keep my kids computer on Ubuntu, but I will keep my tablet pc and wife's laptop on Windows for the foreseable future.

---

### Post by Dougie187 on 2008-06-18
Hey, Sorry it has taken a little while to get your thread answered, but I have a Toshiba r10, and I recently got my tablet working to help someone else figure out how to get theirs working. Anyways, if you are still having some issues with it, let me know, also you can check out this post I made to help the other guy out,
[http://ubuntuforums.org/showthread.php?t=829245](http://ubuntuforums.org/showthread.php?t=829245)

As for your dvd issues, go here and read up on how to install the dvd playback codecs
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

Please let me know if you need anything else.

---

### Post by todomartinez on 2008-07-11
Thanks for responding!  I had given up on getting any help.  I didn't see your post until today.

I could really use some help with getting the tablet pen to work with my Toshiba R15-s829.  I do have DVD's playing okay on my tablet and my kid's computer.  But, I would like to use my tablet with Ubuntu the same way that I use it with Windows.  I take a lot of notes with it and I tutor high school students in Algebra 1 & 2.  So, I write out equations/problems/graphs on the tablet and project them onto a screen.  So, if a student requests a copy of something we worked on, I just e-mail or print it for them.

Anyway, I feel that I have tried everything to make it work.  But, I still don't have the pen working. I've owned computers since 1989 and I have been using them since 1981.  So, I am not a stranger to command lines.  But, I've met my match with Tablets & Ubuntu/Linux.

I have started from scratch and have a fresh install of Ubuntu 8.04.  I have wacom-tools & xserver-org-input-wacom installed.  What do I do next?

Thanks,

---

### Post by pibach on 2008-07-12
a) edit your xorg.conf to get the wacom driver engaged
b) set up rotation (I use a script for this)
c) install some tablet apps. that are easytroke, cellwriter, xvkbd, xournal.
d) enjoy! Works great on my x61t

---

### Post by todomartinez on 2008-07-13
> **pibach said:**
> a) edit your xorg.conf to get the wacom driver engaged
b) set up rotation (I use a script for this)
c) install some tablet apps. that are easytroke, cellwriter, xvkbd, xournal.
d) enjoy! Works great on my x61t

1) What changes need to be made to the xorg.conf?

2) I've heard of most of those apps, but I still haven't gotten the pen working.


Thanks,

---

### Post by todomartinez on 2008-07-18
My tablet pen is working!!!!!!  I followed the following instructions at: [http://ubuntuforums.org/showthread.php?t=590747](http://ubuntuforums.org/showthread.php?t=590747) and it worked great.  I just need to work on rotating the screen, but I am so super happy for now!!!!!  I'm minutes from deleting my Windows XP partition.  Well, maybe a weekend or so from deleting it.

Thanks Everyone!:popcorn:

---

