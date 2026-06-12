---
title: "Firefox screwed"
date: 2008-09-14
forum: General Help
---

### Post by kipman on 2008-09-14
Hi,

Firefox closes randomly. My bookmarks are gone. When I try to open the downloads tab it closes Firefox. The back button dosen't work.

using 8.04

Any ideas?


Thanks.

---

### Post by mikewhatever on 2008-09-14
Could be a recently installed extension. Try uninstalling some, if possible, and see what happens.

---

### Post by ju2wheels on 2008-09-14
Also, if that doesnt work check the permission of your home mozilla Firefox folder, I had this happen when my permissions were set to root accidentally.

Open a terminal (Applications->Accessories->Terminal) then do the following:

```

cd ~/.mozilla
ls -al

```

Make sure the output is similar to this (where username is your ubuntu user name):
```

drwx------  4 username username 4096 2008-07-19 21:54 .
drwxr-xr-x 94 username username 4096 2008-09-14 07:08 ..
-rw-r--r--  1 username username  335 2008-07-19 21:54 appreg
drwx------  3 username username 4096 2008-07-19 16:47 extensions
drwx------  3 username username 4096 2008-07-19 16:47 firefox

```

If you find "root" as the username in this directory or in ~/.mozilla/firefox then do the following:

```

cd ~
sudo chown -R username:username .mozilla

```

Again replace username with your Ubuntu user name.

---

### Post by kipman on 2008-09-15
Cheers.
I cant access the addon section of firefox since it closes firefox when accessing anything from that menu. However the addon was working fine before so i would think it may nto be that.
Ju2wheeels: Its set me my username, how ever i think you might be on the right path, since now all my downloads are back to zero in transmission when i had downloaded around 5 gig out of 20, now its back to zero.

Any ideas?

---

### Post by anotherdisciple on 2008-09-15
> **kipman said:**
> Cheers.
I cant access the addon section of firefox since it closes firefox when accessing anything from that menu. However the addon was working fine before so i would think it may nto be that.
Ju2wheeels: Its set me my username, how ever i think you might be on the right path, since now all my downloads are back to zero in transmission when i had downloaded around 5 gig out of 20, now its back to zero.

Any ideas?

A good way to test if it's an add-on causing the problem is to run it in safe mode. Open a terminal and type this:

```
firefox -safe-mode
```

Also, if you run firefox from the terminal and something causes it to crash... the terminal should output the error.

---

### Post by anotherdisciple on 2008-09-15
Another idea... you may want to change the name of your .mozilla folder to something like .mozillaold and see if you don't just have a corrupted profile... that happens for unknown reasons. If you don't mind setting up all of your personal preferences again... that is an easy fix most of the time.

---

### Post by kipman on 2008-09-24
> **anotherdisciple said:**
> A good way to test if it's an add-on causing the problem is to run it in safe mode. Open a terminal and type this:

```
firefox -safe-mode
```

Also, if you run firefox from the terminal and something causes it to crash... the terminal should output the error.

Thanks guys,

I'm getting 


```
(firefox:6637): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

Any ideas?

---

### Post by codedmin on 2008-09-24
Hy,

After today update (3.0.2) my extesion don't show up anymore! Anyone can help

---

### Post by dodle on 2008-09-24
If all else fails, uninstall firefox and delete ~/.mozilla.  you'll have to reinstall your addons and redo your bookmarks.  But, like I said, if all else fails.

---

