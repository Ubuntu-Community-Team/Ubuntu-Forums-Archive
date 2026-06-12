---
title: "[SOLVED] can not apt-get due to bad sources.list (Breezy)"
date: 2008-09-10
forum: General Help
---

### Post by jgemelli on 2008-09-10
Yes I know this box is old LOL

I love the speed of it and it has worked great 4 the last 4 years.  I just wanted to upgrade Firefox only to find that all my url's in /etc/apt/sources.list are all 404.

Anyone know of available repository URL's I can add to this 5.1 box?

Thanks

---

### Post by kostkon on 2008-09-10
> **jgemelli said:**
> Yes I know this box is old LOL

I love the speed of it and it has worked great 4 the last 4 years.  I just wanted to upgrade Firefox only to find that all my url's in /etc/apt/sources.list are all 404.

Anyone know of available repository URL's I can add to this 5.1 box?

Thanks
Breeze went out of support and its repositories went down, officially that is. I am saying this, because now you can access them from a different URL, the repos are still up. They are not updated anymore, of course.

I will come back shortly with the new repo URL's.

And what do you mean by saying you want to upgrade Firefox? Do you mean you want to install Firefox 3?

---

### Post by jgemelli on 2008-09-10
Yes I was hoping to go to Fox 3 as a test on this machine.  My other ubuntu machine is a 7.10 a bit more up to date.

If you can find those links it would rock thanks!

---

### Post by kostkon on 2008-09-10
Please see [this post]("http://ubuntuforums.org/showpost.php?p=5605768&postcount=3") and follow the instructions. And of course, replace everything *edgy* with *breezy*. Also, if you have your own extra repositories in the *sources.list* file, modify it accordingly.

Now about *Firefox 3*, one thing you can try is to download it from *Mozilla*'s site and try to run the binary. If it runs OK, then perfect. You can then move it to a system folder, for example
```
/opt
```
But I don't know how you'll be able to make it the default browser in Breezy.

---

### Post by jgemelli on 2008-09-10
Worked like a charm thanks a million!:KS

---

### Post by nickgaydos on 2008-09-10
Sorry to be off topic here, but were did you get a copy? I found some in torrents, but not enough seeders lol. Or did you have a copy from when it came out?

---

