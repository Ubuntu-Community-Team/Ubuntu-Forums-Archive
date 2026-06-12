---
title: "Unmountable Hard Drive"
date: 2009-03-04
forum: Hardware
---

### Post by justiceerolin on 2009-03-04
Hello all, absolute noob in Ubuntu, been a Windows techie for quite some time.

Last weekend, my 74GB WD Raptor failed and wouldn't boot Windows XP.  

I figured the best thing I can do would be to buy another HD, reinstall Windows (and possibly dual-boot with Ubuntu) and attempt to recover my data from the old drive by putting it in an external enclosure.

So far, everything has worked out great.  I'm currently dual-booting.  I've set up everything with Ubuntu just nicely, and admittingly, 100x easier than setting up Windows XP Pro x64.  

I also put the old Raptor into an enclosure, however, neither Windows nor Linux are able to read the drive.  Windows assumes it's a RAW drive.

Ubuntu sees the drive with the correct drive name, but when I double click to mount it, it tells me that it cannot be mounted.  

Upon searching for clues, I found out through this forum that it may have to be "safely removed" from a Windows machine.  Since I cannot do that (It's not being read by a Windows OS), I tried the next step--force mounting the drive.

However, it gave me an another error.  Any ideas?

Sorry, I don't have the error it gave as I am currently at work.  If you need me to run any other commands for more info, I'll post the results once I get home.

Thanks again.

---

### Post by taurus on 2009-03-04
I assume the old (external) harddrive is /dev/sdb1.  Try mounting it from a terminal and see what the error message is.

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
df -h
```

---

### Post by justiceerolin on 2009-03-04
I tried to get the same unmountable error, but this time I got something different.  This is the GUI error:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

However, right after that, I noticed that it became mounted.

I opened the drive and saw my old files and folders.  Now, I'm trying to pull the files from it, but it's reading really slowly.

Would this be a problem with the drive itself?

---

