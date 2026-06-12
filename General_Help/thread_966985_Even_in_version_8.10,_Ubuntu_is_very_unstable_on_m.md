---
title: "Even in version 8.10, Ubuntu is very unstable on my PC."
date: 2008-11-01
forum: General Help
---

### Post by LIJI on 2008-11-01
Hello,

After trying Ubuntu and other Linux distributions many, many times, I've decided to give Ubuntu yet another try.

Despite the fact that I've [reported my problems before]("http://ubuntuforums.org/showthread.php?t=862362"), and the members of the forums hasn't helped me to find the cause of most of the problems, I've been waiting for the 8.10 release of Ubuntu, in order to give it yet another try.

Because of my previous experience with Linux on my PC, I've tried Ubuntu in VMWare before trying it on my actual PC.

First, I've booted it as a Live CD on my existing Virtual Machine, with Windows XP installed. The results: **After running Ubuntu for 15 minutes, using only some settings dialogs and Firefox, Firefox already crashed 3 times**.

I've tried to making a VM specially for Ubuntu, configured as Linux->Ubuntu. The results (Live CD): **Other than the desktop and panels, Ubuntu was unable to start any application, including the setup itself. The Desktop and Panels crashed several times and restarted. All that in only 3 minutes.**

My hardware:
Intel Core 2 Dou @ 1.86GHz x 2
1 GB of RAM
nVidia 8600 GT
2 Hard drives, 160GB and 80GB.

VMWare host:
Windows XP Professional SP3.
VMWare Workstation 6.
All settings in the Ubuntu VM were the defaults for Ubuntu.

Could anyone please explain, why on earth would Linux renders completely unusable on my PC, including when ran in virtual machines?

Thanks,
LIJI.

---

### Post by zoffmann on 2008-11-01
01. set more ram to virtual machine ( > 256 mb)
02. more ram on your real computer (ie. 1.5 - 2G)
03. maybe you need to update vmware workstation to the latest version

try live cd on your real computer and see what is happening if you didn't do it already

I am not expert in this issue but maybe you'll get an idea how to solve this

hope it will help :)

---

### Post by LIJI on 2008-11-01
1. The VMWare is already set to 512MB of RAM.
2. Ubuntu (Version 7.04 at that time) was running perfectly on my older PC with only 512MB of RAM. The minimum RAM required for Ubuntu is 256MB anyway, and I'm not getting more RAM only to install an OS, while I'm prefectly happy with my current amount of RAM.
3. Haven't done it in a while, I'll try it tomorrow. Though Fedora (Version 6, 7 and 8 if I remember correctly) was running flawlessly on this version of VMWare.

---

### Post by Stefanie on 2008-11-01
you can't expect ubuntu to run flawlessly in virtualbox/vmware. even the live-cd will be much faster (and that's still very slow compared to a full install). try out the live cd if you don't want to make any changes to your system. it is also possible to install ubuntu "inside" windows - google for "wubi", maybe it's what you're looking for.

also bear in mind that intrepid is very new. it might take a while before all bugs have been reported and fixed. if you're affected by a bug, stick to hardy. in general i'd recommend intrepid though, it's very fast and stable on my laptop, better than hardy.

---

### Post by LIJI on 2008-11-01
Of course I do not except an OS to run flawlessly in a virtual machine, however I do except the minimal functuality of acutally running applications.
I've been using Linux for a while, however since I got a new and better PC, I've had very bad exprience with Linux. I've tried Wubi before, and after defragmatting my partition it stopped booting, though I'm not sure if that defragmation is the cause of the problem, as I've had problems with Linux distributions suddenly stopping to boot (Read post linked from the first post). Also I didn't quite like the way it's located in the hard disk as a file, it felt quite "annoying" and somewhat limiting.

The reason I've actually tried Intrepid is **because** Hardy was causing problems in my computer, I don't see any reason to downgrade back as it will literally change nothing. (Read link from first post again.)

---

### Post by Doji on 2008-11-01
Bad memory can cause erratic program behavior, so try burning a live cd and running memtest86+.

---

