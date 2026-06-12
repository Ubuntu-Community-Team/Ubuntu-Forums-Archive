---
title: "Running Ubuntu in Virtual Box Monitor Issue"
date: 2010-12-14
forum: Hardware
---

### Post by warmnscsi on 2010-12-14
Hello, I am running Ubuntu 10.04 as a guest OS on my desktop which has win 7 as my host OS. My problem is that ubuntu doesn't recognize my monitor and only allows two resolutions 800x600 and 640x480. As you can imagine, using 800x600 on a 1920x1080 monitor is rather frustrating. But here's the kicker. My monitor is an LCD TV so as far as I know there arn't any drivers downloads that I could simply install and fix this problem. 

Any ideas?

---

### Post by squenson on 2010-12-14
Have you installed the VirtualBox guest extensions in the guest OS?

To do it, select (in the host window) the menu Device guest extensions. Then a CD drive should appear in Ubuntu, so open a terminal, go to the folder /media/cdrom0* and execute the command ./VirtualBox-x86.sh*

*: I am typing this from my (poor) memory, so the names may not be exactly correct. But until someone else makes a more qualitative answer, you can fiddle around this.

---

### Post by warmnscsi on 2010-12-14
> **squenson said:**
> Have you installed the VirtualBox guest extensions in the guest OS?

To do it, select (in the host window) the menu Device guest extensions. Then a CD drive should appear in Ubuntu, so open a terminal, go to the folder /media/cdrom0* and execute the command ./VirtualBox-x86.sh*

*: I am typing this from my (poor) memory, so the names may not be exactly correct. But until someone else makes a more qualitative answer, you can fiddle around this.


Thanks but I don't have a driver's disk. It's a tv, Hannspree ST259MUB. When I go into windows device manager to see what driver win 7 is using it says Hannspree M19N3. Now if I can find where windows got that driver from.

---

### Post by squenson on 2010-12-14
I was most probably unclear. After you launch your virtual machine, which appears in a Window, select from the menu of that Window the option Device > Install Guest Edition (again, please forgive me if it is not exactly correct).

This should mount in your Ubuntu machine a CDROM called guestedition, but this is not a physical CD, it's a software that you have downloaded together with VirtualBox. This CDROM contains a program called VirtualBox-Linux-x86.something and this is what you have to execute inside your Ubuntu machine. This will setup the virtual graphic card and allow better resolutions.

---

### Post by warmnscsi on 2010-12-14
:D

Thanks with your help I was able to get it working. It's still not full screen but 1360x768 is far better than 800x600. For anyone else who may encounter the same thing and would like to know what to do:

While the guest OS is running click devices - Install Guest Additions at the top of the vbox window. Go to terminal and type sudo nautilus(to run the script with root access)  and then click on the virtual cd drive in the places menu on the left. Run either VBoxLinuxAdditions amd64 or x86 (for whichever version of the OS you are running). Hit enter to close and restart your virtual machine. System - Preferences - Monitors.

It's what squenson said but with more detail. Thanks squenson.

---

### Post by squenson on 2010-12-15
> **warmnscsi said:**
> It's what squenson said but with more detail. Thanks squenson.Thank you!

It's strange that you cannot go further than the resolution you mentioned. I can even set up resolutions much bigger that the physical screen, there should be a limit but it seems very high. How much memory did you allocate to the graphical card? Have you tried to use the menu option (once again from memory!) Machine > Full Screen?

---

