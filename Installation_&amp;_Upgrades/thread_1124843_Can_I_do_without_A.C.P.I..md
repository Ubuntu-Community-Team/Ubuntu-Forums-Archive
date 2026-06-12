---
title: "Can I do without A.C.P.I.?"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by imaginashawn on 2009-04-13
I preffer two machines for learning programming. So, I recently installed Ubuntu 8.10 on my five year old mini tower. Being that old, the hard drive hardly ever stops running, so I thought I'd start taking out any uneeded software. As I go through the list in Synaptic Package Manager, I come to the A.C.P.I. ... ? I understand what it's for basicly, but can I do without it? It shouldn't cause major problems to not have it should it? I'd really like to lighten the load of the 'background'. 
Thanks):P

---

### Post by antikristian on 2009-04-13
I'd keep it in if I where you. It's basically powermanagement, but it also controls fans and thermal, powerbuttons and more. 

If you leave it out: 
-the computer will do a hard shutdown when you press the physical powerbutton, without sending shutdown events to stop programs and unmount filesystems, which might corrupt the filesystem in worst case scenarios.
-you'll have to press the physical powerbutton manually after you have shut down the computer from within Ubuntu.
-Newer kernels have an issue with networking without acpi, I lost my network completely on my server after an upgrade:P

If you leave it in:
-Computer might consume less power 
-A shutdown either within ubuntu or by pressing the powerbutton results in a soft shutdown, which unmounts filesystems, stops services and shuts down the computer completely without an additional press of the physical powerbutton

The load on the system is minimal, there are one additional service running, but it doesn't really hog any resources.

Sure, some computers still support apm which is an older tech that does some of the same jobs, but I'd leave acpi in:)

Use top if you want to see what's using your cpu and hogging memory, sleeping processes does not use any resources other than some ram, and that does not slow your computer down before you use up all of the systems memory, then those processes will be written to your swap partition.

---

### Post by imaginashawn on 2009-04-13
Interesting. Thank you for sharing your knowlege with me. You guys are the best! I'm finding lots of other things to uninstall instead, i.e. players, drawing and photo programs etc. .:grin:

---

### Post by antikristian on 2009-04-13
Aah, the joys of uninstalling;-)

---

### Post by Stupendoussteve on 2009-04-13
Having a program installed does not create background load. If your hard drive keeps running you may want to see what is using it, install iotop and then run it from the command line. It will show in near real time what is using your drive (as well as how much, something quick is probably not what's keeping it grinding).

If your system has very little ram, it is possible the swap is being used quite a lot which would also cause a drive to keep running.

---

