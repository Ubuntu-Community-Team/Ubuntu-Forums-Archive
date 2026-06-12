---
title: "Trying to reinstall Ubuntu 8.10"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by GazFighter on 2009-03-03
I had upgraded to the 9.04 Alpha the other day but had too many problems so I decided to reinstall 8.10. The problem is that I keep getting errors when trying to do so. Sometimes I'll get an error that says "Unable to turn Cooling Device 'on'". or in the midst of installation it says that my CdDrive or Harddrive are faulty which I know aren't true as they were working fine just a few days ago. What do I do now?

---

### Post by civillian on 2009-03-03
> in the midst of installation it says that my CdDrive or Harddrive are faulty which I know aren't true as they were working fine just a few days ago.

This is a recurring problem for me, I have found that downloading and burning the cd image on a different comnputer or downloading the image from a different source can often fix the problem.
You could also try the alternate install CD

---

### Post by GazFighter on 2009-03-03
I do not have a different computer to download it on ATM. Also whats the alternative CD and how's it different from the Live CD?

---

### Post by GazFighter on 2009-03-03
Also the 4...yes 4 Live CD's I have all get these magical errors and now my Kubuntu disc is as well. This is really annoying.

---

### Post by civillian on 2009-03-03
The alternate CD is described [here](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate).

The problem is quite widespread, so you are not alone. If you are getting the error that I experienced (errno 5 I/O error) then lots of people seem to have fixed it by using the alternate install CD, burned at the slowest possible speed.

You could also try (as a last resort) installing 8.04 then upgrading to 8.10 via the update manager I suppose, but that seems pretty drastic to me. I suggest searching the forums with your symptoms/error message if you can remember it, which ususally turns up a fair few results.

In the meantime, I will continue to try to find a solution :)

---

### Post by civillian on 2009-03-03
Found one possible fix on launchpad:

> My solution to [Errno 5] on Ubuntu install was to remove some RAM modules.

I had great trouble installing 8.10 to my computer (model: HP d330). It took me three days and countless hours researching around the internet. Here is my success story.

I downloaded the ISO and attempted to install from the Live CD. The following error appeared at about 24% of install process:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

1. Attempted reburn CD-R at slower speed. Same error.
2. Attempted install with "Alternate CD". Same problem (it froze up somewhere in "copy files to disk" process).
3. Attempted boot from Live CD and double click "Install". NO GO. Wouldn't even start process.
4. Repeated all the above in various ways. Same results.
5. Tried changing the various choices under F6 on boot-up. Freeze or same error.
6. Live CD then begin to hang on boot from CD. Couldn't get anything to do anything.
7. Attempted to install from Flash card (using separate PC to set it up). Booted fine, but same error on install.
8. Attempted many solutions offered on various forums online. Still no luck.
9. Tried noapic options and others to no avail.
10. Tried repartitioning hard drive, and wiping hard drive and etc. etc. etc.
11.Gave up and installed Windows XP. Hated it (as usual). Waited several hours. Kept repeating all the above plus anything I could think of. Redownload ISO. Burn at slower speeds. Try Alternate CD. Try Flash card again. NO LUCK. Fiddle with various settings again.

And then I used the little grey cells in my head (as Poirot would say in an Agatha Christie novel). I remembered someone somewhere suggested RAM error as the culprit. I ran the memory test without a problem (that took many hours!), but still I was supicious about the memory. My PC has four memory slots but with 3 actually memory sticks. 256Mb (original memory stick that came with computer) + 1Gb (cheap no brand stick added later) + 1GB (another added no brand stick). I simply took out the two 1Gb stick and left only the original 256Mb stick and attempted an install. Bang! It worked. No error. No problem (except it was as slow as molassis to install...). After the successful install, I replaced the 2Gb of memory and rebooted. Everything worked out. RAM modules might be faulty but everything seems fine.

I'm not sure if this solution will help everyone. The cause of [Errno 5] might be different for each machine, and sometimes just trying a million attempts leads to an eventual success. But in my case, removing most of the RAM solved the problem.

Finally I can get on with enjoying Ubuntu 8.10.

I suppose you could give this a try...

---

### Post by WatchingThePain on 2009-03-03
Unable to turn cooling device on?. That's a new one. Are the fans ok?.

---

### Post by tombott on 2009-05-15
> **C!V!NT said:**
> Found one possible fix on launchpad:



I suppose you could give this a try...

Genius, I think I love you.

Been trying to install 9.04 on a HP d330 for weeks now with no joy. Tried installing from 7.10 up, but various error messages.
Took out all RAM except for original 256mb HP branded module the PC shipped with and 9.04 has installed without any problems.
Stuck my extra ram back in and all is good in the house of Tom.

Cheers.

---

