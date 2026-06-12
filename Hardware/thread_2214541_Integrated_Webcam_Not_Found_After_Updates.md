---
title: "Integrated Webcam Not Found After Updates"
date: 2014-04-01
forum: Hardware
---

### Post by jcjanko on 2014-04-01
I have looked through the forums, but cannot find an answer, so I apologize if this is easy.

I had just finished an online tutoring session with my webcam about an hour ago, then automatically installed 11 new updates that were ready to be installed. I went back on to start a new session, and for some reason my webcam can no longer found anywhere (Cheese, gstreamer-properties, websites, etc). 

I have a Dell E6400 with 12.04. I had no problems before the updates. This is obviously a HUGE problem as I need the webcam for these sessions. Thanks!

---

### Post by jcjanko on 2014-04-01
I just grabbed a backup old USB webcam to test it out, and it worked fine.

---

### Post by jcjanko on 2014-04-01
Just tried lsusb, is not showing up.

---

### Post by Dowiro on 2014-04-03
I have the same problem, my webcam isn't working for some reason, cheese can no longer take photos or video through the integrated webcam. And if I try to log in to online sessions I get error message of no webcam found. Mine is a Samsung NP350 running 12.04

---

### Post by mörgæs on 2014-04-03
If a bug has been introduced to 12.04 you can't be sure it will be fixed. 14.04 is on the way, and developers are changing focus.
While you wait for a fix to (maybe) come up you could try a live boot of 13.10.

---

### Post by jcjanko on 2014-04-13
> **mörgæs said:**
> If a bug has been introduced to 12.04 you can't be sure it will be fixed. 14.04 is on the way, and developers are changing focus.
While you wait for a fix to (maybe) come up you could try a live boot of 13.10.
I am confused. What is the point of "LTS" if support is only given for the first 2 years of the 5?

---

### Post by mörgæs on 2014-04-13
Support means that security bugs are fixed. Non-security bugs may or may not. 

In general people should be better in abandoning old versions, supported or not, and install new ones in stead, especially when a problem appears.

---

### Post by jcjanko on 2014-04-13
> **mörgæs said:**
> Support means that security bugs are fixed. Non-security bugs may or may not. 

In general people should be better in abandoning old versions, supported or not, and install new ones in stead, especially when a problem appears.

OK, that makes sense about security updates. 

Dowiro: I went into Grub (holding Shift while booting), and just selected the option to use a previous kernel. Problem solved for me until 14.04 is ready (couldn't use Final Beta due to bugs, but they look like they are solved).

EDIT: I am using 3.8.0 now.

---

### Post by mörgæs on 2014-04-13
That's a good idea. When a new kernel arrives you can check if the bug has been fixed.

Please mark the thread 'solved'.

---

### Post by jcjanko on 2014-05-06
> **mörgæs said:**
> That's a good idea. When a new kernel arrives you can check if the bug has been fixed.

Please mark the thread 'solved'.

So I have been using 14.04 since the day it came out, and everything worked great. Just updated the system, restarted, and integrated webcam is out again. 

This is ridiculous.

---

### Post by jcjanko on 2014-05-06
This time, I cannot revert back to a previous kernel, so I am stuck as of right now. I have searched the internet, and this is a common problem. Unfortunately, my integrated webcam is essential, and I am losing money with it down every second, so I am going to have to erase my install, reinstall Ubuntu 14.04, and then make sure I note every single update every single day in order to catch the culprit.

Like I said, ridiculous, since this has been going on for years and no solution has been found.

As a side note, I ran the Live DVD, and I could not "reinstall" 14.04. It was grayed out.

---

### Post by jcjanko on 2014-05-06
OK, a fresh install did nothing.

---

### Post by mörgæs on 2014-05-06
How does 13.10 work?

Also, it would be a good idea to remove the SOLVED flag if you want more people to help.

---

