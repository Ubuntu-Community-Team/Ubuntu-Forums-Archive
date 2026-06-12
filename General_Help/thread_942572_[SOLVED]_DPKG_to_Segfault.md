---
title: "[SOLVED] DPKG to Segfault"
date: 2008-10-09
forum: General Help
---

### Post by Sprag-O on 2008-10-09
Hey everyone... 
 I'm new to the forum here, and have lurked for a little while. I see some people with the "dpkg --configure -a" issue when working with apt-get. Mine seems to be causing a few more issues...

First, when running apt-get "anything"
  
   I get "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

That doesn't seem too bad, but when running commands I'm getting...
    
   " dpkg --configure -a
Setting up libc6 (2.7-10ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Segmentation fault
dpkg: subprocess post-installation script returned error exit status 139"

I've searched a bit, some people have cleared the cache from apt, and some other random fixes. I've tried about everything I could find, just seeing if anyone has anymore advice :(

---

### Post by Kevbert on 2008-10-09
Probably the best thing to do is to purge the package and then try re-installing it.  First try
```
sudo apt-get install -f
```
to try to repair any damaged packages.  **What's your sources.list look like ?**

---

### Post by Sprag-O on 2008-10-09
Sorry I can't remember everything I've tried already to list...

That was one I have done, just returns...

"apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

---

### Post by drs305 on 2008-10-09
Run the following if you haven't. I know you said you've run it but in your example you didn't include the sudo part. So just in case:
```
sudo dpkg --configure -a
```

---

### Post by Sprag-O on 2008-10-09
Yup, I ran that right after just to make sure... results with,

"dpkg --configure -a
Setting up libc6 (2.7-10ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Segmentation fault
dpkg: subprocess post-installation script returned error exit status 139"

---

### Post by drs305 on 2008-10-09
You might try reverting to an older dpkg status and then trying it again. It will depend partially on how old the status-old file is. If it doesn't work run the third command to restore the original.

```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.09102008
mv /var/lib/dpkg/status-old /var/lib/dpkg/status

```

Try running your commands again.
If not successful, restore the original status file:
```

sudo cp /var/lib/dpkg/status.09102008 /var/lib/dpkg/status

```

---

### Post by Kevbert on 2008-10-09
See if you can remove libc6 via Synaptic (mark it for complete removal and note all packages that are removed), then try to re-install them.

---

### Post by az on 2008-10-09
> **Kevbert said:**
> See if you can remove libc6 via Synaptic (mark it for complete removal and note all packages that are removed), then try to re-install them.

You can't remove libc6 - everything depends on it.

I suggest you try to reinstall the package manually.

Be sure to not mix repositories.  Do not try to install a package that was build for another version or another distro.  If this is what you tried to do here, it may have tried to pull in the correct version of libc6 for that package.  Correct the situation by manually installing the correct version of libc6 for your release.

---

### Post by Kevbert on 2008-10-09
> **az said:**
> You can't remove libc6 - everything depends on it.

I suggest you try to reinstall the package manually.

Be sure to not mix repositories.  Do not try to install a package that was build for another version or another distro.  If this is what you tried to do here, it may have tried to pull in the correct version of libc6 for that package.  Correct the situation by manually installing the correct version of libc6 for your release.

That's why I asked what the sources.list looked like. Assuming that all of the sources are for Hardy, would a 
```
sudo apt-get install libc6
```
work ? or how would you suggest it should be done (I'm learning all the time from these forums).

---

### Post by Sprag-O on 2008-10-09
Reverting didn't help, still got seg fault,

Synaptic wouldn't even open until I fixed the dpkg issue, which I can't because the seg fault :p

apt-get install libc6 just results in the dpkg error...

I think im going the manual install route

---

### Post by Sprag-O on 2008-10-09
Is there any real good download locations for such files? I'm only seeing entire ISO's listed on all the mirrors

---

### Post by az on 2008-10-09
By installing manually , I meant using dpkg, not apt.

You download the packages from the archive.  You find them using this:

[http://packages.ubuntu.com/search?keywords=libc6&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libc6&searchon=names&suite=all&section=all)

---

### Post by Sprag-O on 2008-10-09
I've got the libc6 package I need... but when trying to install the .udeb now, the Package installer is telling me I need to turn off other software management software... I killed update manager, and running like ps -ax doesn't show any other related proceses.

---

### Post by Kevbert on 2008-10-09
So you mean
```
sudo dpkg -i package_file.deb
```
I've never tried this...

---

### Post by Sprag-O on 2008-10-09
dpkg -i libc6-udeb_2.7-10ubuntu3_amd64.udeb
Selecting previously deselected package libc6-udeb.
(Reading database ... 99037 files and directories currently installed.)
Unpacking libc6-udeb (from libc6-udeb_2.7-10ubuntu3_amd64.udeb) ...
dpkg: error processing libc6-udeb_2.7-10ubuntu3_amd64.udeb (--install):
 trying to overwrite `/lib/ld-2.7.so', which is also in package libc6
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 libc6-udeb_2.7-10ubuntu3_amd64.udeb

---

### Post by drs305 on 2008-10-09
Since you don't seem to be making much progress  :-( , here is a final suggestion (at least from me). Try renaming /var/lib/dpkg/libc6.postrm and libc6.postinst and try running the apt-get commands again. Rename to the original if it doesn't work. If it does, reinstall libc6 to reset the .postrm and .postinst files to the correct status.

---

### Post by Sprag-O on 2008-10-09
So far... That seems to work. When I go to re-install libc6 to get back .postrm and .postinst it says there's nothing to do, It's already on the newest version. I'm afraid to leave as is, but it is technically working now.

---

### Post by Sprag-O on 2008-10-09
Also, I do have...

"libc6-i386.postinst
 libc6-i386.postrm"

and I'm on an amd64 box, could I have possibly added generic libc6 files as well? or should I have both libc6.postrm and libc6-i386.postrm for example?

---

### Post by drs305 on 2008-10-09
> **Sprag-O said:**
> So far... That seems to work. When I go to re-install libc6 to get back .postrm and .postinst it says there's nothing to do, It's already on the newest version. I'm afraid to leave as is, but it is technically working now.

I don't think this is going to present a problem unless libc6 didn't finish any post-install actions it needed. Apt-get/dpkg seem to be 'happy'. You aren't likely to be uninstalling libc6. If everything is working I wouldn't worry about it. 

If everything is now working and you don't have any further questions, please mark this as solved via the "Thread Tools" link at the top right of the first post. You don't have to be in a rush to do this (although it is reversible). It does help in that others with similar problems might find this post a bit easier and 'helpers' won't have to spend time reading posts which are already resolved.

Welcome to the ubuntu forums!

---

### Post by Sprag-O on 2008-10-09
Thank you everyone... Seems to work great... Will close as I wish I could have found this post before I had to ask :)

---

### Post by az on 2008-10-09
A udeb is not the same as a deb.

A udeb is used for installing packages to build the installer environment.  You shoul dnever need to install a udeb.

You should find the corresponding libc6 deb package.

---

