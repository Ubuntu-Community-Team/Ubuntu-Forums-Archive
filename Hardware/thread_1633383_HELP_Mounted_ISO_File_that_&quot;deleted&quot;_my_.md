---
title: "HELP Mounted ISO File that &quot;deleted&quot; my computer hard drive"
date: 2010-11-29
forum: Hardware
---

### Post by confederatesoldier on 2010-11-29
The title is as much as I know.

I mounted an ISO file per a "reliable" friend's instructions using the "sudo mount ... -o loop" command and suddenly my entire hard drive vanished.  I tried to remount the hard drive but for some reason the drive is listed as still mounted while only the contents of the iso file are present.  I cannot even open any of these contents as Nautalis does not work anymore

Could someone help me out of this problem?  I don't actually know what I've done in the first place.

Thanks.

Edit:

Only my home folder was deleted and that was the destination of my ISO mount.  At this point I can only assume it is gone for good.

---

### Post by ajgreeny on 2010-11-29
I doubt that your /home "has gone for good" and suspect that what you are seeing is much more innocent than that.  I don't know what you actually did in detail to mount the ISO file, but I imagine it was something like ```
sudo mount -o loop -t iso9660 path/to/file.iso /mount/path
```
I think that if you unmount the ISO file your /home will appear again. ```
sudo umount /mount/path
```

If you don't know exactly what you did in terminal you can find all your old commands by using the "up cursor key" to go through the history.  That should show you where you mounted the ISO, and may help to unmount it again.

In future you do not need to mess around in the terminal to mount an ISO file, you can either open it with Archive manager, or Archive mounter.  On my system ISO files are opened by default in the archive manager, but a right click on the file shows archiove mounter as an alternative.

---

### Post by confederatesoldier on 2010-11-29
Thanks, for the first time in my life when I restarted my computer it actually fixed the problem.  I still don't know exactly what happened but the entire problem has been reversed.  In the future I will not mount ISO files in terminal in the way I did before.  Thanks for your time and effort!

---

### Post by efflandt on 2010-11-29
What specific instructions did you use to mount the iso?  It sounds like you mounted it in place of your home directory.  But a manual mount like that is temporary.  So once you **umount** it (note no n after the u), or reboot, it is no longer mounted (as long as there is no entry for it in /etc/fstab).

What you should have done is first created a directory (mkdir) as a mount point, and then mount it to that directory.  Then you could cd to that directory (or use Places) to see what is on the iso.

---

### Post by ajgreeny on 2010-11-30
> **confederatesoldier said:**
> Thanks, for the first time in my life when I restarted my computer it actually fixed the problem.  I still don't know exactly what happened but the entire problem has been reversed.  In the future I will not mount ISO files in terminal in the way I did before.  Thanks for your time and effort!
When you restarted the computer the mounted file was automatically unmounted so the problem went away.  If you use the archive mounter application in future the ISO will be mounted on your desktop, and show there as an icon, or at least that is where they mount on my machine.

---

### Post by pricetech on 2010-11-30
Go though your command history.  You'll probably find that you mounted the ISO in ~/home.  That would do it.

---

