---
title: "Running 9.?? on live cd need to access my external HDD to move files URGENTLY"
date: 2011-04-30
forum: Hardware
---

### Post by teddy101 on 2011-04-30
11.04 was a total disaster. I can't get to anything, I have exams looming. I need to get my computer working. So I am going to do a total re install of 10.10. Much saver idea. however to do that, i need to get move my files over.

When I plug my external HDD in it appears in computer as USB drive. it can't be mounted and can't be accessed.

How do I get this working.

I am running from a live disk in one of the 9s i think 9.10.


thankyou

---

### Post by slooksterpsv on 2011-04-30
First is the drive an NTFS formatted drive (you can connect it to Windows)? If so connect the 9.xx to the internet, open up a terminal and type in the following:

gksudo apt-get install ntfs-3g

This will make it to where you can access the NTFS drive.

---

