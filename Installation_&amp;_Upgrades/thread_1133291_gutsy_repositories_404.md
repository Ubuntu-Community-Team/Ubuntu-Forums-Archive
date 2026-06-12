---
title: "gutsy repositories 404 ?"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by mykel-- on 2009-04-22
Hi guys,

im trying to install a few packages and it looks like the repositories have been taken offline.

please dont tell me this is because "7.10 is not a LTS release so we dont offer repositories anymore".

i have hardware issues with 8.04 AND 8.10, will try out 9.04 when it comes out, but until then, please tell me the repos have moved or something...

```

Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]

```

---

### Post by hansdown on 2009-04-22
Hi mykel--

Sorry to say, but 7.10 has reached it's end of life. The repositories are no longer available.

---

### Post by mykel-- on 2009-04-23
im raging. i cant believe nobody wants to keep less-than-2-year-old repos going. sigh. im hoping 9.04 will work with my sata controllers.

---

### Post by amac777 on 2009-04-23
You should be able to use [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) if you really need to keep running gutsy

---

### Post by MaxVK on 2009-04-23
I'm having this problem too (waiting for a disk to arrive before I update!)

amac777: Thanks for that link, but what do I do with it?

Cheers
Max

---

### Post by Kokopelli on 2009-04-23
> **MaxVK said:**
> I'm having this problem too (waiting for a disk to arrive before I update!)

amac777: Thanks for that link, but what do I do with it?

Cheers
Max

Update your /etc/apt/sources.list to use the new URL.

"security.ubuntu.com" becomes "old-releases.ubuntu.com"
in my case (since I am in the U.S.)
"us.archive.ubuntu.com" becomes "old-releases.ubuntu.com"
etc...

in my case
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
sudo sed -ie 's|//security|//old-releases|' /etc/apt/sources.list
sudo sed -ie 's|//us.archive|//old-releases|' /etc/apt/sources.list
sudo apt-get update

```

was sufficient.  If you use third party (or different) repositories you might need to adjust the commands or the file itself.

---

### Post by Windsurfer619 on 2009-04-23
Keep in mind that if you do a distribution upgrade to 8.04, that will be supported for quite a while, and you'll be able to upgrade straight to 9.10 when it comes out.

---

### Post by MaxVK on 2009-04-24
Thanks Kokopelli, thats done the trick.

Windsurfer619: I have 9.10 on order and I'm waiting for the disk. Once that comes Ill do a clean install and go from there, but in the last few weeks that I'm on 7.10 Ill be checking out various bits of software still, so I need these repository links for dependencies etc.

Anyway, thanks all.

regards

Max

---

### Post by adit on 2009-04-24
[_http://old-releases.ubuntu.com_]("http://old-releases.ubuntu.com") has only iso images of old releases, no repositories.  Does anyone know where the repositories are?

---

### Post by adit on 2009-04-24
Sorry, I didn't go through the site completely. The repositories are in
[http://old-releases.ubuntu.com/ubuntu/dists/gutsy]("http://old-releases.ubuntu.com/ubuntu/dists/gutsy")

---

### Post by MaxVK on 2009-04-24
Just to clarify if anyone else happens across this thread:

Following the link/instructions above will enable the old repos so you can use synaptic etc again. Its pretty seamless and everything works as it did before.

---

### Post by msnel on 2009-04-24
I'm having the same problem.

I'm trying to upgrade to 8.04 (eventually to 9.04) and the upgrade notes say "Be sure that you have all updates applied to your current version of Ubuntu before you upgrade."

However, I can't apply the updates because of this 404 problem. Should I use the link advertised here ([http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)) to install the updates, or can I ignore the advise of the upgrade notes and upgrade directly?

Thanks
Matt

---

### Post by cantony on 2009-05-29
Thank you for your post, (with the slight change of us- for gb- because I'm in UK) it worked a treat

---

### Post by xolot1 on 2009-12-05
Hi,

Would someone please describe how to update the respository urls?
Must I manually go through /etc/apt/sources.list or is there a script somewhere.
Thanks!

Willi

---

### Post by xolot1 on 2009-12-05
Alright,
I ended up just using Emacs search and replace in my /etc/apt/sources.list file so that apt would hit the old-releases server.  The affected lines included enough information so that I could dist-upgrade. 
Im up and running again!

---

