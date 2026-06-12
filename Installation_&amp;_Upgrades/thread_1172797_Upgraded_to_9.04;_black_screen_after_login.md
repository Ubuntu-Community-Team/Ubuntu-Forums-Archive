---
title: "Upgraded to 9.04; black screen after login"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by mas0n on 2009-05-28
I've been happily running 8.04 since it launched and jumped through some hoops to get the F@H GPU2 client running on my 9800GT. It's been running great for months, but for whatever reason I am thinking that may have something to do with my current problem, I followed this guide: [http://foldingforum.org/viewtopic.php?f=54&t=6793](http://foldingforum.org/viewtopic.php?f=54&t=6793)

Like I said, everything was great for quite some time. Yesterday I upgraded to 9.04 using the automated update utility (sorry I don't know the real name, the same utility that checks for system updates, etc)

The system boots fine and stops at the login prompt. I enter my username and password. Then the screen goes black and displays only the mouse pointer, which I can move around. I can also drop to terminal (Ctrl - Alt - F1) but have no idea what I need to do or where I can check log files to see what is not working correctly.

I assumed there was an issue with the Nvidia drivers, so I downloaded the latest and installed while in command line interface, but no luck.

Help!?

---

### Post by tommcd on 2009-05-29
> **mas0n said:**
> I've been happily running 8.04 since it launched and jumped through some hoops to get the F@H GPU2 client running on my 9800GT...
  Yesterday I upgraded to 9.04 using the automated update utility 

Did you upgrade from 8.04 *directly* to 9.04? If you did, this is not recommended. You should upgrade in sequence: 8.04 > 8.10 > 9.04. Skipping versions (8.04 > 9.04) is not recommended.
I would suggest doing a clean install of Ubuntu 9.04. It would be the best way to get up and running quickly with a clean system.

And welcome to the Ubuntu forums!

---

### Post by mas0n on 2009-05-29
> **tommcd said:**
> You should upgrade in sequence: 8.04 > 8.10 > 9.04. Skipping versions (8.04 > 9.04) is not recommended.

I did indeed got straight from 8.04 to 9.04. Thanks for the info.

Cheers

---

### Post by Custom Cowboy on 2009-05-29
Is it possible to upgrade to 9.04 kernal but keep exsisting seperate HOME partition

---

### Post by tommcd on 2009-05-29
> **Custom Cowboy said:**
> Is it possible to upgrade to 9.04 kernal but keep existing seperate HOME partition
Yes, if you have /home on a separate partition, then you can keep it and all your data and hidden config files that are stored in /home, and just install 9.04 to the root partition of your current installation.
Choose manual partitioning when you install 9.04. Then choose to install Ubuntu 9.04 to your root partition, with mount point / (root) and choose to reformat that partition.
Then choose you home partition with mount point /home. Be sure to choose *not* to reformat home. Swap will be automatically selected as swap and used accordingly by the installer.

EDIT: If you are doing a dist-upgrade instead of a clean install, then yes also. If /home is on a separate partition it will be safe during the dist-upgrade. In a dist-upgrade /home would still be safe even if it was on the same partition as root.

---

### Post by Custom Cowboy on 2009-05-29
Thanks

---

### Post by tommcd on 2009-05-29
> **Custom Cowboy said:**
> Thanks
Be sure to see the EDIT I added to this thread after you posted. I was not sure if you were doing a clean install or a dist-upgrade.

---

### Post by steve_ on 2009-08-06
I had the exact same problem described here (black screen after login) and the problem ended up being that a bunch of files in my user dir (incl some hidden files) were owned by root.  Once i fixed ownerships everything worked fine.

---

