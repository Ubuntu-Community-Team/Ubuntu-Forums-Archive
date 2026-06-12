---
title: "Installing ubuntu remix in the eee pc 1000; disc defect"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by asoto on 2009-04-29
Hi, I just bought an Asus eee pc 1000 (Which shipped with 8G solid state, 32 flash, and Xandros Linux), and was thinking of installing the ubuntu netbook remix (ubuntu nrm) in it.  So I downloaded the image and burned it into a usb-drive using usb-imagewriter as suggested in the webpage.

I checked the md5sum for the file, and it was correct.

I then proceeded to "Check the disc for defects" and received  the "error in 1 files found"

I burned the file using two different computers running ubuntu several times, and two different flash drives, always getting the same error.

I did it again, this time  pressing CTRL-ALT-F4 (or CTRL-ALT-F8?), and I could see which was the corrupted file:

Checking ./pool/main/p/ppp/ppp_2.4.5~git20081126t100229-0ubuntu2_i386.deb...No such file or directory


In spite of the above, I can run the "live usb" without problems (I  am writing this from the "live usb").  The camera worked after I enabled it in the BIOS, and the microphone worked after I went to Volume control->Preferences; enabled Capture and then ummute the microphone and raise the Volume for it.

I don't know how to fix it.  I took a screen shot of the error when it was found.

Apparently the Asus eee pc 1000 is one of the computer  where almost everything works fine, so This is unexpected.

Please let me know if someone can confirm this problem, before I filed it as a bug.

Apparently it is related to bug #360925 as reported 

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/366086/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/366086/+viewstatus)

and 

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/366086/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/366086/+viewstatus)

But I still don't know if the alledged reports are for Jaunty.  Also, the md5sum got the right answer in my case.

---

### Post by flavio1 on 2009-05-16
For sure, I can confirm this problem.
Like you, I used different pen drives, different computers, different operative systems (also windows), different geographic locations to download from and ALWAYS found at the disc check "1 error found in 1 file!"
Tried to install anyway, on my brand new eee pc 900a (atom), two times, and the system crashes (freezes, I would say) as soon as I switch from one desktop to another (from nrm to normal and viceversa).
This is the second time I return to the normal ubuntu, whose check does not find defects, but neverthless I find some graphical instability in it.
It seems to me that the files img distributed worldwide are all defectives, also if this does look absurd!
So, what should we do?
                       Greetings                          Flavio

---

### Post by asoto on 2009-05-16
This is a reported bug (Bug #360925).  You can read the comments in the discussion.  In particular, it is unrelated to the freezing problem you mention.   It might be good to continue any discussion there:

[https://bugs.launchpad.net/ubuntu/+source/mobile-meta/+bug/360925](https://bugs.launchpad.net/ubuntu/+source/mobile-meta/+bug/360925)

Peace.
-Adrian.

---

### Post by flavio1 on 2009-05-17
I read the discussion in the link you posted, but, sorry, I' m not so clever to follow you all in a discussion like that.
I just wanted to know if it is possible for me to get a jaunty nrm flash stick without defects, but in a SIMPLE way.
Seems not, for now... .Thanks, indeed.

---

### Post by asoto on 2009-05-17
It suffices to rename the file after you burn it into the USB.  It is the same file (the md5 is for both files is ff0358bc3eb43e9420a7f009482c278a).
It says:
/pool/main/p/ppp/ppp_2.4.5~git20081126t100229-0ubuntu2_i386.deb

It should say:
/pool/main/p/ppp/PPP_245~.D

Then, after you boot your disc, it will pass the test.

I wish there were a simpler way.

-Adrian.

---

