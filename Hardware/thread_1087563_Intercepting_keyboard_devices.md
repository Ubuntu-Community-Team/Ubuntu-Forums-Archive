---
title: "Intercepting keyboard devices"
date: 2009-03-05
forum: Hardware
---

### Post by Arancaytar on 2009-03-05
General information first: I'm using Ubuntu 8.10 on a Samsung V25 laptop, my kernel version is 2.6.27-11-generic, and I'm using a USB keyboard ("Microsoft Digital Media Keyboard 1.0A, Model 1031", according to the label).

During the years of Windows XP, I have been using a utility called HomeKeyLogger to continuously archive keystrokes. Besides the ease of recovering unsaved text (less of an issue since Linux crashes less), this is extremely helpful whenever I need to find out when exactly I typed something, registered an account, installed/used a program, etc. Comfort far outweighed the data (~20MB/year) and performance overhead (imperceptible), and I simply took some time to purge sensitive pass-phrases before archiving. All in all, this has worked very well and I'd love to do the same thing now that I am on Ubuntu. This is in fact the only remaining reason I'm still reluctant to use Linux exclusively.

I have already tried uberkey and lkl. lkl didn't work at all (it ran, but never logged anything). uberkey gave me a lot of keymap trouble (I use a German QUERTZ keyboard) and didn't manage to read the USB keyboard at all. I'll probably have to write something myself (I know the bash shell quite well, but only enough C and Perl to hurt myself.)

I have come across a utility called *interceptty*, which may be the solution (in combination with a script). But while I was able to use it on /dev/stdin and the name of the current terminal (returned by *tty*), of course it only logged what I typed into the terminal window it ran in. Obviously, I need it to run in the background and capture all input, regardless of which window is active.

Question time: Would it help me if I knew the device path of both keyboards - and if so, how do I find them? Could I accomplish all this in some other way I haven't thought of yet?

Thanks! :)

---

