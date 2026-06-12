---
title: "Downloading, Installing, Updating..."
date: 2005-11-18
forum: General Help
---

### Post by Alpha_toxic on 2005-11-18
I'm not that new to Linux, but I'm not used to this "sudo apt-get" thing. Please someone explain me what it actually does and is it posible to run sth like this in grafical mode. I'd also want to know where is this thing downloading from (perhaps some server of the ubuntu comunity?), is there a way to browse through the packages in Firefox or sth, how to find what is the exact command for a specific app. Well actually I want to know everyting about downloading, installing apps, and updating. I hope someone takes the time to give me some advices or even beter point me to a guide/help/info on that. Thanks in advance.

---

### Post by aysiu on 2005-11-18
Read these two links and call me in the morning:
[http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php)
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by Alpha_toxic on 2005-11-18
10x, I'havent read those yet, but it looks like they'll solve everything.
And wow that was a fast response... 10x alot again.

---

### Post by aysiu on 2005-11-18
You can always come back if you have more questions.

---

### Post by Alpha_toxic on 2005-11-24
It all works fine, but as far as I can see the downloaded packages are kept in "/var/cache/apt/archives". It makes sound not to delete things that took pretty long to download, but in my case they tend to take too much space (around 500MB for now, and I still haven't dl javaSDK and Eclipse). As my Kubuntu partition is only 5GB, I realy can't afford such a waste of space.
So is it safe to just delete them or I would have to do sth more (edit files where the info of cached packages is kept perhaps??)??

---

### Post by aysiu on 2005-11-24
System > Administration > Synaptic Package Manager > Settings > Preferences > Files > Delete Downloaded Files after Installation.

---

### Post by Alpha_toxic on 2005-11-24
This did the trick. And why did no one told me to use Synaptic anyway. I was ](*,) whit Adept (the option you gave me is not present in Adept, actually there are no options at all...). Now after installing Synaptic and permanently removing Adept as described above(:twisted:) I am one realy happy Kubuntu user:D

---

### Post by aysiu on 2005-11-24
No one tells you to use Synaptic because Adept is the "native" KDE application. I happen to like Synaptic a lot better, but some people think native apps and desktop environment "integration" are really important.

---

### Post by nortonedd on 2005-11-26
aysiu, thank you very much for the up-to-date repositories. your signature worths pure gold.

---

