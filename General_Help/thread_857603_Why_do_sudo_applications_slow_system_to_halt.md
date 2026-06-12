---
title: "Why do sudo applications slow system to halt?"
date: 2008-07-12
forum: General Help
---

### Post by Johnny K on 2008-07-12
I'm using Hardy Heron and have noticed this problem within the past couple of months. I don't believe this problem existed before I upgraded to Hardy Heron.

sudo applications slow my system to an absolute halt. The application will begin running and I will start to hear my hard drive spinning. The mouse pointer becomes less responsive and it becomes very difficult to interact with any open programs. After a couple of minutes, everything slows down to the point that my computer becomes so unusable that I consider going outside (don't worry, I haven't done anything that drastic yet :))

In my case, the offending appliactions are gdebi-gtk, Synaptic, Update Manager, and Simple Backup (my backup program). It's interesting to note that this slow-down process only begins when the sudo application in question begins to write to the disk. For example, I can load Synaptic and search with it just fine, but as soon as I hit "Apply", everything slows down. It's also worth mentioning that I don't notice this slow-down when I am doing other disk-intensive work, such as large scp or ftp downloads. The slow-down only seems to occur when a sudo application writes to the disk.

---

### Post by Johnny K on 2008-08-12
Does anybody have any insight on this matter? Not only for me, but for the hundreds (if not thousands) of other people who must be suffering from this same, beyond frustrating problem.

---

### Post by DeathOnJuice on 2008-08-12
I haven't heard of this problem before, but I'm not exactly a regular on the forums. Regardless, it's not normal, so if no other help is given, a reinstall will have a very high probability of fixing the issue. Good thing you're keeping backups ;) .

---

### Post by MaindotC on 2008-08-12
I don't think many people are suffering from this problem.  It's difficult to propose a suggestion based on the information that you've given but here are some root issues that generally affect everything else.  

Did you dist-upgrade to Hardy or perform a clean install?  

It sounds to me like you could have a hardware problem (like a bad memory module or even BIOS) - have you used this hardware before without issue, and for how long? 

Your video driver could be configured improperly (this affects almost everything) - please give your hardware specifications (like in my signature) and links to each item that contains the documentation and specifications.

The initial installation may not have happened properly and that will depend on your answer to dist-upgrade or clean install.  If it's not the installation, can you think of any significant events that happened when you first noticed this problem?  Check your sys logs.

---

### Post by cariboo on 2008-08-12
What applications are you running using sudo?

Jim

---

### Post by MaindotC on 2008-08-12
> **Johnny K said:**
> I'm using Hardy Heron...In my case, the offending appliactions are gdebi-gtk, Synaptic, Update Manager, and Simple Backup (my backup program).

He's already stated which applications.

---

### Post by Johnny K on 2008-08-13
Thanks for all the help everyone.

> **strAlan said:**
> I don't think many people are suffering from this problem.  It's difficult to propose a suggestion based on the information that you've given but here are some root issues that generally affect everything else.  

Did you dist-upgrade to Hardy or perform a clean install?  

It sounds to me like you could have a hardware problem (like a bad memory module or even BIOS) - have you used this hardware before without issue, and for how long? 

Your video driver could be configured improperly (this affects almost everything) - please give your hardware specifications (like in my signature) and links to each item that contains the documentation and specifications.

The initial installation may not have happened properly and that will depend on your answer to dist-upgrade or clean install.  If it's not the installation, can you think of any significant events that happened when you first noticed this problem?  Check your sys logs.

I upgraded from Gutsy to Hardy. I didn't run into any major problems that I can remember, other than an issue with Mozilla's xulrunner not upgrading. But I fixed that right away.

Yes, I have used this same hardware with Feisty and Gutsy without this problem.

The machine is a Dell e1505n, one of the machines shipped with Feisty back last year. Here are some more detailed specs:
[Intel Integrated Graphics Media Accelerator 950 GM]("http://www.intel.com/design/chipsets/mobile/945_fam.htm")
[Intel Core 2 Duo T5600]("http://processorfinder.intel.com/details.aspx?sSpec=SL9U3")
[1GB, DDR2, 667MHz 2 Dimm for Inspiron E1505]("http://accessories.us.dell.com/sna/products/Memory_Upgrades/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A0743833") (link may not be correct, I'm not sure).
[100GB 7200RPM SATA hard drive]("http://www.shopping.com/xPO-Seagate-100GB-MOMENTUS-2-5-SATA-150-NCQ-7200")

The only other interesting note is that my hard drive suffered from the acpi bug ([https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)). I fixed the problem in Gutsy or Feisty by using [this workaround]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14"). The workaround worked then, and continues to work - that is, it resolves the original problem. The question is whether it caused this new problem.

---

### Post by Johnny K on 2008-09-14
The reinstall seemed to do the trick.

I don't know what caused the problem, but I also did not do the hard drive bug workaround ([https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14)) since reinstalling, so maybe that had something to do with it.

Anyway, thanks for all the help everybody!

---

### Post by mb_webguy on 2008-09-14
I'm glad you got it working.  

While this doesn't directly have anything to do with your problem... You really shouldn't use sudo for graphical applications.  That's what gksudo (or simply gksu) is for.  Using sudo for GUI applications can cause problems.

---

### Post by Johnny K on 2008-09-14
> **mb_webguy said:**
> I'm glad you got it working.  

While this doesn't directly have anything to do with your problem... You really shouldn't use sudo for graphical applications.  That's what gksudo (or simply gksu) is for.  Using sudo for GUI applications can cause problems.

I was using whatever was used by default to launch applications like Synaptic, which I would assume would be gksu.

In the end, I don't even know if it was related to gksu or not because some non-gksu disk-intensive work (e.g. Banshee importing music) would also freeze the system.

In short, a very weird problem. But at least it's fixed now.

I also noticed that a fresh install solved many other problems which I didn't even expect to see fixed. It seems that doing standard distro upgrades introduced some problems that I was unaware of. For example, when I upgraded to 8.04 the bootup splash screen stopped working. I assumed it was just a bug in Hardy, but it appears it only came about because I did a distro upgrade. Doing a fresh install resolved this and some other minor problems. The Ubuntu team should really spend more time to ensure that distrobution upgrades work correctly, as I and many others have run into plenty of problems with them.

---

