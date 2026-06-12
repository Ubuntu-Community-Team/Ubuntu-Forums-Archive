---
title: "Bluetooth problem in Ubuntu 9.04"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by bazola on 2009-09-24
I recently discovered Wubi and Hardy Heron Ubuntu because of the arstechnica article that was talking about the new stable Ubuntu release. So I wanted to test out Wubi because it would make it very easy to put linux on a few of my windows machines. The first machine was a dual core dell desktop, only a few months old. It installed and functions with no problems at all.

The second machine is an older Dell, a pentium 3ghz. I've got Wubi using 10gb of space. All that is in the file structure are basically the install ISOs for the desktop version of ubuntu 9.04. If you can't tell, I'm a linux novice but it seems mostly intuitive so far.

So here is the problem I'm having. I can select Ubuntu from the dual boot screen, and everything seems to be loading and initializing fine, but towards the end of the terminal screen booting it attempts to initialize bluetooth, and then it gives me an error message that says something like "info: task hid2hci:4511 blocked for 120 seconds." It continues to try to initialize bluetooth over and over and it hasn't yet let me get into the operating system. This has happened with all of the different boot options I've tried. 

I'm not sure exactly what I need to do to fix this. I don't actually have bluetooth so I just need to disable it. I found some ways to disable it for specific IBM netbooks but this is a dell desktop. Hopefully somebody can point me in the right direction.

Thanks!

---

### Post by bazola on 2009-09-26
Hate to bump, only going to do it once.  I was hoping somebody else has had this exact problem.  I think the solution will end up being running a specific bluetooth disable command during the installation.  I really have no idea what it would be, though.

---

### Post by bazola on 2009-10-07
So I ended up finally succeeding in putting 9.04 on the problem PC.  I suspect that it might have been the USB wireless card (Netgear WG121) that Ubuntu was seeing as bluetooth.  But what I did that actually got me a successful install was starting with Wubi 8.04 and then chain upgrading to 9.04.

---

