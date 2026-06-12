---
title: "No progress with 9.04 install..."
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Thecoolguru on 2009-04-02
I'm trying to set up a dual boot with Vista on my new computer, and I decided I'd try out 9.04. I selected the "Install them side by side, choosing between them each startup" option, and hit the forward button. It's been over an hour, and it still says "Resizing partition..." and is at 0%. I here disk whirs like crazy, but no progress is being shown. I'm afraid to stop the installer and just try a manual install in case it actually is doing something. Any suggestions? (Since this is a relatively new computer, I don't have an ext3 partition yet D:)

---

### Post by unisol on 2009-04-02
try this first:Here's how to install Vista and Linux (with Vista installed first). Step-by-step instructions that assume no knowledge of Linux. (Now updated for Ubuntu 8.04 and Vista SP1).
Page 2 - Get started - prepare the Vista partition
 
Boot into Windows Vista and go into Disk Management - right-click My Computer, Manage, Disk Management. 

 
Right-click on the main Vista partition and select Shrink Volume - the Shrink tool will assess how much space can be freed up. 
As a rule of thumb Shrink will reduce the main system partition by about 50%. As long as the partition is big enough to begin with (at least 10GB) it should accommodate both operating systems. 
Select Shrink and the tool will reduce the volume of the primary partition, leaving the rest of the disk free as unpartitioned space. 
Once that's done, shut down the Vista machine.
 start up computer with ubuntu cd in drive and install it.
this is only if you havent set a partition for ubuntu. if you alresdy have a partition for ubuntu, disregard this.

---

