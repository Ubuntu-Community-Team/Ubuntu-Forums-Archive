---
title: "Inspiron 8000 Install (Screen Issues)"
date: 2009-06-11
forum: Hardware
---

### Post by RKilbride on 2009-06-11
New to Ubuntu and very excited!  Anyway I took the plunge and started with an old Inspiron 8000. Got a brand new Ubuntu 9.04 mailed to me and did my research on Inspiron 8000 issues. Came across the screen issue from someone else (the screen was split into three parts and looked fuzzy. This is a common problem with this model and was caused by a bug in the Xorg code). 
I would need to tweak the refresh rates in xorg.conf to fix this. So ..... I tried to do this:

switched to the terminal by pressing ctrl+alt+f1, after logging in I edited the xorg.conf using the following command. 

sudo vim /etc/X11/xorg.conf


Could not get this command to work in the terminal  in any variation but could get a gksudo gedit command to work from the desktop.

 

I then inserted the following two lines under the monitor section.
 

HorizSync	31-82
VertRefresh	40-110


Should these lines go directly under monitor section or after the other 2 lines that are already there?



That made it worse on reboot so I rebooted Ubuntu into safe mode and had it re install the original xorg.conf.


So.... what am I doing wrong? Pretty comfortable with editing registry in Windows etc but I feel like I'm missing something. It's hard to even edit anything from the desktop, can I do it from the root shell on bootup?
Thanks!

---

### Post by michaelos on 2009-06-12
I  have the same issue.  When I installed Win200, my display was shrunk (big bars all around) I had to  install a driver from dell.  Once installed and rebooted everything was fine.
 
Now, installed 9.04 in "low graphics mode" (due to the 3 bar issue) and I have the shrunk screen again.  No resolutions above 800x600 are availabel.  When I connect to an external monitor, I do get 1024x768 on it BUT I can not get both the monitor and the laptop screen to display at the same time.
 
There has to be something simple that we are missing.  So if anyone can help us that would be great!

---

### Post by thubin on 2009-07-28
I found that the Fn-F7 key combination changes the Dell Inspiron 8000 laptop display from messed up full size to proper half size. Then do it a second time to get proper full size display.

Tom

---

