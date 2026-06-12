---
title: "Problems with external hard drive"
date: 2012-10-03
forum: Hardware
---

### Post by orentsur on 2012-10-03
Hi all in the forum.  First thread so please be gentle... :p

I am at a complete loss!  I have a Dell D630 running Xubuntu very happily.  Before you direct me to the Xubuntu forums, this problem happens in Ubuntu as well.  In fact it happens in Debian as well...  the only place it does not happen is under Windows....

My HDD recently died so I bought a bigger hard drive to replace it.  I then wanted to use another HDD for backing up stuff.  I bought an enclosure, planted the drive in it and connected it.  I started moving files across from the external drive to the 'new' drive when all of a sudden I started getting all sort of errors.  At first they were about a directory not being there.  Then permission errors and eventually the ext drive could no longer be read.  I checked the ext drive using the Ultimate Boot CD and it checks out 100% fine and no S.M.A.R.T errors to be found.  All good.  Further more I can format it and install an OS on it.  So, planted it back in the enclosure and attempted to format with GParted.  Formatting works fine and GParted lets me know that all successfully completed.  However, as soon as GParted scans the drive again the drive then shows as unallocated space.  The drive is not recognised when reconnected.  I then bought a new enclosure with a new USB cable and tried again.... no luck.  Exactly the same behaviour.....

If you are still awake - any ideas?

Thanks for reading!

Oren

---

### Post by Crafty Kisses on 2012-10-03
What are the results of the following
```
sudo gedit /etc/fstab
```

---

### Post by sidzen on 2012-10-03
I had a D610 with a PentiumM -- its BIOS would only recognize a hdd of 80GB or less for some reason.  And no BIOS update was available. So I spent too much for a 80 gig IDE hdd and replaced the malfunctioning original.  I loaded SolusOS on it and gave it to a 12-yr-old girl as her first PC.  (Start 'em young and they don't care about the OS!)

re: external hdd -- I use file manager (in your case Thunar) and get the path to my external devices (usually /media/*something*/) then move files via the CLI and the **mv** command from one to the other hard drive or other device. This saves a lot of errors and frustration.

Best wishes and welcome!

---

