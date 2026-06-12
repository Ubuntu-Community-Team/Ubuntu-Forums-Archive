---
title: "I messed up Ubuntu"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by TheHimself on 2009-07-15
I have Intrepid installed on my computer. I just wanted to have the newer version of Evolution which is available in Jaunty so I manipulated with "software sources"  entering Jaunty repository as a "third party". Then I upgraded Evolution and several other packages (needed by evolution) were also upgraded. 

Immediately afterward some functions stoped working like terminal and wireless so I thought what the heck, let's upgrade to jaunty. But I can't do that because Ubuntu won't start. Everything is OK before the login screen and then an eternal busy cursor shows up.  What should I do?

---

### Post by eatberrys on 2009-07-15
can you boot to recovery mode ?

---

### Post by Jimleko211 on 2009-07-15
Clean reinstall.

---

### Post by TheHimself on 2009-07-15
Yes, I can boot to the recovery mode but it has just a few options like fix broken packages, etc. Or maybe it has more features i don't know?

Also does Jaunty installation DVD have an upgrade option?

---

### Post by TheHimself on 2009-07-16
Reinstallation is not an option for me because I have too many applications and settings on the computer.

---

### Post by TimEnid on 2009-07-16
> **eatberrys said:**
> can you boot to recovery mode ?

how do you boot to recovery mode? will this fic corrupt drives?

---

### Post by TheHimself on 2009-07-16
I managed to repair and upgrade. Here is how. I booted to the recover mode and then chose "Fix broken packages" but internet connection was not working. after a little bit of search I used the following command in the shell:

```
dhclient
``` 

and I was connected to the internet. Apparently it's bug that networking is not available in the recovery mode by default. Then I ran "Fix broken packages" again but that didn't bring Ubuntu back to life. So, I used the alternate cd with command

```

apt-cdrom add
apt-get dist-upgrade

```

and now I have jaunty

---

### Post by presence1960 on 2009-07-16
next time don't add sources for other versions of Ubuntu. if you want the latest and greatest of a program go to it's web page and download the deb file for it. Install it that way.

---

### Post by TheHimself on 2009-07-16
Thanks for your advise. In fact I had tried that but  Evolution webpage doesn't offer the package. It says "Evolution is already included in your distribution". It offers the source of course but that's not so easy.

Easier than what I had to do to repair my system though!

---

### Post by tommcd on 2009-07-17
> **TheHimself said:**
> Reinstallation is not an option for me because I have too many applications and settings on the computer.
Glad you got it fixed! In the future, do not add newer repos to your sources.list unless you know exactly what you are doing.

One question though...
How could you possibly have *too many applications and settings on the computer* that a reinstall of Ubuntu is an absolute impossibility?? 
I have seen many people around here claim that it is "impossible" for them to reinstall Ubuntu; but not a single person has ever explained exactly why.
So if you don't mind, I would like to ask:
Why is reinstalling Ubuntu such an utterly impossible task for you??
A reinstall is never an ideal solution to fix a problem; but it is *always* an option of last resort.

---

### Post by TheHimself on 2009-07-17
It's possible of course as it's possible to throw my computer out of window but it's not worth it. My computer is so customized: several Firefox extensions and bookmarks and settings, Kile's settings and dictionary, etc.
But I think the more important point is that fresh reinstallation is Windows style because in Windows one doesn't have so much power over the system internals. One of the first things I was told on a Linux forum was this:

In Linux if something breaks, you fix it and if it works then you break it!

---

