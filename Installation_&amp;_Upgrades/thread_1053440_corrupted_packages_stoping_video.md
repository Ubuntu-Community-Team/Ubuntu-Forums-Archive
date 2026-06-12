---
title: "corrupted packages stoping video"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by ubiubi on 2009-01-28
Hi all
Can anyone help?
I tried to update with synaptic pkg manager after installing Intrepid amd64 (260 packages) and got two error messages. These erros stop me installing codecs so it is impossible to view video! What should I do?

[COLOR="Red"]E: /var/cache/apt/archives/linux-headers-2.6.27-11_2.6.27-11.25_all.deb: corrupted filesystem tarfile - corrupted package archive

E: /var/cache/apt/archives/gimp_2.6.3-1ubuntu1~intrepid1_amd64.deb: corrupted filesystem tarfile - corrupted package archive
[/COLOR]
Cheers

---

### Post by fuzzyworbles on 2009-01-28
delete them from cache and download them again

---

### Post by Partyboi2 on 2009-01-28
Open a terminal (Applications>Accessorires>Terminal) and 
```
sudo apt-get clean
sudo apt-get update 
sudo apt-get upgrade
```

---

### Post by ubiubi on 2009-01-29
Thanks Partyboi2 and fuzzyworbles

Before I saw your replies I had changed my local srever from France to the US. This solved the 'header' package problem. I followed your advice for removing/cleaning and then reinstalling and managed to solve the 'Gimp' package problem. The codecs then installed but still no images. I was then forced to reinstall my ATI driver following insstructions from one of the ubuntu 'How to' tutorials. Everything now works fine!
Thanks again to you both:popcorn:

Oh, how do I mark this as solved, I followed your thread for marking as solved but the 'Mark as solved' ie the fifth option in the thread tools list, but it does not exist on my list?

Sorry to be a pain!

---

### Post by Partyboi2 on 2009-01-29
> **ubiubi said:**
> Thanks Partyboi2 and fuzzyworbles

Before I saw your replies I had changed my local srever from France to the US. This solved the 'header' package problem. I followed your advice for removing/cleaning and then reinstalling and managed to solve the 'Gimp' package problem. The codecs then installed but still no images. I was then forced to reinstall my ATI driver following insstructions from one of the ubuntu 'How to' tutorials. Everything now works fine!
Thanks again to you both:popcorn:

Oh, how do I mark this as solved, I followed your thread for marking as solved but the 'Mark as solved' ie the fifth option in the thread tools list, but it does not exist on my list?

Sorry to be a pain!
The solved thread option has been disabled at the moment due to database problems. Hopefully it will be back soon :)
[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

