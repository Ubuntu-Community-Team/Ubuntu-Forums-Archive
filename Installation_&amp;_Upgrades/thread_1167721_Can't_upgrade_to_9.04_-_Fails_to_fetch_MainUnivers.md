---
title: "Can't upgrade to 9.04 - Fails to fetch Main/Universe Sources.bz2 files"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by ipsi on 2009-05-23
I currently have Ubuntu 8.10 installed. I just upgraded from 8.04, and that went flawlessly, as far as I can tell.

However, now that I've rebooted and all, I'm getting an error when I try to update to Ubuntu 9.04:

```
W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2  Hash Sum mismatch
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

At that point, it reverts my configuration and doesn't upgrade.

I don't get it on my EEE PC which runs Easy-Peasy (effectively 8.10) when I started (but didn't go through with!) the upgrade to 9.04, nor did I get it on my work laptop, which I upgraded from 7.10 to 9.04 on Thursday (Wednesday for everyone in America).

Given that, it's very likely a problem with my configuration, but I couldn't possibly say why. Only major difference that leaps to mind is that I've got the NVIDIA Restricted drivers installed (version 180), for my video card.

So, does anyone have any idea as to why I'm getting this error?

Thanks all,

- ipsi

---

### Post by ipsi on 2009-05-23
I switched from using the New Zealand Ubuntu Repositories to the Main ones and that seems to have solved the problem. Weird.

---

### Post by richardh9936 on 2009-08-18
Ipsi,
I agree, it's weird.  My eee-pc has failed to upgrade from Intrepid to Jaunty, too.  Following your suggestion, I swapped from the "Australian" server to the "Main" one, and the package manager now agrees that there are many packages to update. 

Still failed, though.  Ho hum.

---

### Post by richardh9936 on 2009-08-18
I think [http://ubuntuforums.org/showpost.php?p=7486673&postcount=8]("http://ubuntuforums.org/showpost.php?p=7486673&postcount=8") has the answer.  Somehow, our EEE-PC sources.list contained a remnant reference to intrepid.  Once that was corrected, the update process works.

tgelati4 worked it out.

---

