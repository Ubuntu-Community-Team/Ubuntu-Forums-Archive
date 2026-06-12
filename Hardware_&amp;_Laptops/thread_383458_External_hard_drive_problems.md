---
title: "External hard drive problems"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by Snyper64 on 2007-03-13
I'm having a problem with my external drive(Western Digital partitioned in ntfs). I'm running the 64 bit Ubuntu Edgy and had no problems accessing the drive before I tried [THIS]("http://ubuntuforums.org/showthread.php?p=1647295#post1647295") upgrade. This is the error I am getting: "mount: unknown filesystem type 'ntfs-3g' error: could not execute pmount". Any ideas or suggestions on how to fix this, or atleast get my old drivers back so that I could atleast access the drive.

Thanks
Snyper64

---

### Post by matburton on 2007-03-13
I'm not sure if this would cause this problem, but did you make sure that the NTFS partition was unmounted when it was last used by windows?

For instance you didn't hibernate windows it the USB HD still plugged in?

Just a wild stab in the dark!

Otherwise you could go to synaptic, re-add the the source from the guide, do any upgrades that come up and mark pmount, ntfs-3g, ntfs-config for re-install and restart.

Sorry if that's not much help but I'd suggest actually posting in the thread the guide is in.

---

### Post by Snyper64 on 2007-03-13
Yes it was unmounted by Windows, it worked fine until I tried to give it write support, and than it wouldn't mount at all. Also how would I go about with reinstalling pmount, ntfs-3g, and ntfs-config? I just switched over to Linux 2 days ago with all of the DRM Micr$shaft is tossing into its new OS and the plain headaches Windows XP was giving me with all of its annoyances(believe it or not this hard drive problem is small compared to most of the problems I have had with XP) so I am just learning how to use this new OS.

---

### Post by matburton on 2007-03-13
Its only a suggestion and may not work

System menu -> Admin -> Synaptic Package Manager

the choose Settings menu -> Repositories -> Third Party Tab

Make sure [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) is there, if not paste the following in
```
deb http://flomertens.free.fr/ubuntu/ edgy main main-all
```

Then close that window and hit the Reload button...

Wait a bit, you might be notified of new updates, if so close the package manager and do the updates.

If not or after, search for pmount, ntfs-3g and ntfs-manager and click right mouse button and select mark for reinstall.

Then hit the Apply button.

After that run sudo nfts-manager in a terminal window to see a couple of NTFS options.

Hope that helps!

EDIT: ntfs-manager should be ntfs-config, woops!

---

### Post by Snyper64 on 2007-03-13
Ok, followed what you said, had to add the site to the repository, went to upgrade the packages and got this error:
```
http://flomertens.free.fr/ubuntu/dists/edgy/main/binary-amd64/Packages.gz: 404 Not Found
http://flomertens.free.fr/ubuntu/dists/edgy/main-all/binary-amd64/Packages.gz: 404 Not Found
```
So I decided to search for pmount, I found it but there is no option to reinstall, just mark for removal and mark for complete removal. I also searched for ntfs-3g and found that it wasn't even installed(:confused:strange:confused:) so I installed it, I also searched for ntfs-config and ntfs-manager but didn't find either one.

Edit: I hooked up my external and it seems to be working, its reading the drive(I haven't tried opening or running anything yet) and when I right click it shows add new document. I'll post again if everything is working again or isn't working.

Edit 2: Everything is working fine now, I got full read/write support.

Thanks for your help matburton, now I just need to get my sound and second monitor problems fixed and I'm good to go.

---

