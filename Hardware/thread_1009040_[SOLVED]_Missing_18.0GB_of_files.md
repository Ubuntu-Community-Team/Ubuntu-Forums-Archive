---
title: "[SOLVED] Missing 18.0GB of files"
date: 2008-12-12
forum: Hardware
---

### Post by tropdoug on 2008-12-12
I have a very strange issue. my /home partition which is on a seperate hard drive got nearly full. I thought 'thats odd' cos I knew I did not have 76 Gig of stuff on there. I began removing stuff to an external drive, and when it was apparently empty there is still 18.0 gig of files showing. They are not hidden files, I have checked, and moved all the config hidden files and miscellaneous stuff off the drive. 

When I look in Gparted it too shows the drive has files in it. 

I tried resising the drive. I even booted off a live CD and tried but it won't do it. 

I don't want to format it without understanding what is going on. Can anyone suggest a reason for this behaviour (see attached snapshots)

---

### Post by logos34 on 2008-12-12
Run the following command:

du | sort -rn > myhomefiles

Now look for 'myhomefiles' text file in home.  It'll list everything in your /home dir, biggest to smallest.  Hopefully that'll show what's taking up so much space.  

You've checked hidden files (and the trash right?).  Not sure what else to suggest.

---

### Post by Zimmer on 2008-12-12
probably  .thumbnails!!

---

### Post by tropdoug on 2008-12-14
Thanks for that, 

I did it, and sure enough a huge list of files that don't show using the 'view hidden files' in the menu. I don't know what they are yet or why they are there. Some of them appear to be redundant files from old programs I uninstalled ages ago. or previous versions of programs like firefox. I don't have the time right now to work it all out, but I will get back to it, in a week or so, and see what happens.

---

### Post by tropdoug on 2008-12-31
I am marking this as solved, but I didn't really solve it, I eventually simply reformatted it, cos couldn't make sense of them 

Anyways thanks for the help

---

