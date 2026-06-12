---
title: "Radeon &gt; lost screen"
date: 2016-03-09
forum: Hardware
---

### Post by asearle on 2016-03-09
Hallo Everyone,

I installed Lubuntu 15.10 on a friend's computer and we found that it was running very hot and that graphics were "juddery".  My suspicion is that there is a problem with his AMD Radeon graphics so I installed the fglrx-drivers.  However this caused a non-boot situation with a black screen with just a few heiroglyfic characters.

I googled around and there seems to be a lot of discussion about this issue and several suggested solutions so I booted to a shell prompt and tried to deinstall fglrx but found that the commands/packages were not found.  Here I assume that paths have been changed and that it is a simple syntax issue.

So can anyone point me to a reliable solution for a.) the deinstallation of fglrx and b.) the correct drivers/settings for Radeon graphics  (under Lubuntu 15.10).

That would be a great help!

Many thanks,
Alan Searle
Cologne, Germany

---

### Post by ajgreeny on 2016-03-09
Which AMD Radeon graphics?

Some of the AMD graphic cards are no longer able to use the fglrx driver as AMD has stopped support for all the 3xxx and 4xxx series.
If the machine uses either of those you will be able to use only the open source, default radeon driver, which would be what is used at installation and by the live system, if you installed via that live OS.

It is always worth running the live OS in my opinion, and installing from that, to see if there are likely to be any problems after installation.

---

### Post by asearle on 2016-03-09
Yes, I see.  Thanks.

But now I am in a bit of a fix because installing fglrx has messed up my installation and I get a black screen (at boot).

I went into the command-line environment and tried to use ...

<code>sudo apt-get remove --purge xorg-driver-fglrx fglrx*</code>

... to get rid of fglrx in order to get the system to boot properly but got the message:

No lock for the read-only file /var/lib/dpkg/lock
Write not possible
Packet list or status file could not be read or opened

(I am translating from German)

So any ideas on how I can get rid of fglrx and boot the system?  It would be an absolute pain if I had to do a complete re-install.

Many thanks for any tips that you can give me.

Regards,
Alan

---

### Post by howefield on 2016-03-09
> **asearle said:**
> I went into the command-line environment and tried to use ...

Are you referring to Recovery mode ?

If so, you'll probably need to mount the file system as writeable.

```
sudo mount -o remount,rw /
```

then

```
sudo apt-get remove --purge fglrx*
```

should work ?

---

### Post by ajgreeny on 2016-03-09
Alternatively just boot to the login screen, hit Ctrl+Alt+F1 to get to a command line, login with username and p'wd, (the latter will not show on screen), then run that final command from howefield above, and finally reboot with ```
sudo shutdown -r now
```

---

