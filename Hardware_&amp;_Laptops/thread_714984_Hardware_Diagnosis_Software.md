---
title: "Hardware Diagnosis Software"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by RSIxidor on 2008-03-04
I'm new in the whole Linux field, but am absolutely loving it. I was wondering about finding a software application that worked similar to Fresh Diagnose for Windows, but obviously for Ubuntu (Gutsy Gibbon)

The reason I'm asking is the Hardware Information (Device Manager) utility that's built in lists a lot of my hardware as unknown or generic. I was hoping their might be a more powerful system information tool but have not found anything in the Add/Remove programs window.

Its possible I just don't know what I'm supposed to be looking for, so I was hoping someone here could tell me what I need.

Thanks, guys

EDIT: I think this program, [Hardware Lister]("http://linux.softpedia.com/get/System/System-Administration/Hardware-lister-6180.shtml"), would be what I need, but again, with my newnessity to Ubuntu, I'm having trouble. I've still got to learn some of the basic commands. Shoot.

---

### Post by kaurman on 2008-03-04
Hi!

If you are just looking for hardware information, then you could try lshw. It can be done in terminal.

Just open the terminal and type 'sudo lshw'. Now enter your root password and you're done.

---

### Post by RSIxidor on 2008-03-04
Well, I found a program in Add/Remove thats giving me as close to what I wanted as possible.

I wasn't being observant enough to see the thing at the top that allowed you to look at a bigger selection of programs.
 
lshw is helpful, but I was hoping to find a GUI version, and I did, hooray! The two programs I downloaded were hardinfo (which has closed itself several times while I tried to select a new option, I blame this one low memory, I've actually only got 128 mb, something which will be resolved soon). The other is Sysinfo, which had the same information but didn't crash.

Thanks, though.

---

