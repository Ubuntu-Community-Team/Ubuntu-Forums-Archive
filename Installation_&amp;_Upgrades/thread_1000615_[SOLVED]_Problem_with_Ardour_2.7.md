---
title: "[SOLVED] Problem with Ardour 2.7"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by daniel_w93 on 2008-12-03
Hi,
I'd really like to try the new Ardour version because I worked with expensive stuff like adobe Audition in the past and I'd like to see if ardour is as good as audition or even better...

My problem, if I download the Adour 2.7 file I can't install it.
my system configurations are:
Ubuntu 8.04 (hardy)
Kernel Linux 2.6.24-22-generic
Processor: Intel Celeron M CPU  420 @ 1.60GHz
Memory: 495 MB

Please help me

---

### Post by Partyboi2 on 2008-12-03
What do you mean by you can't install it? Are you installing a deb or from source? If you are trying to install from source what are the errors if any? Debs are easier to install so I would suggest downloading the deb package from [[COLOR=Blue]here[/COLOR]]("http://www.getdeb.net/release.php?id=3505") then double click on it to start installing. You may need to install a few dependencies to get the deb package installed. :)

---

### Post by daniel_w93 on 2008-12-05
> **Partyboi2 said:**
> What do you mean by you can't install it? Are you installing a deb or from source? If you are trying to install from source what are the errors if any? Debs are easier to install so I would suggest downloading the deb package from [[COLOR=Blue]here[/COLOR]]("http://www.getdeb.net/release.php?id=3505") then double click on it to start installing. You may need to install a few dependencies to get the deb package installed. :)

Okay... if I do it like that it says: Error: Dependency is not satisfiable:libasound2

thanks for the help so far...would be great if you can tell me how to get it right

---

### Post by Partyboi2 on 2008-12-05
Means you need to install the libasound2 package. You can search through Synaptic (System>Admin>Synaptic Package Manager) for libasound2 or open a terminal (Applications>Accessories>Terminal) and type
```
sudo apt-get install libasound2 
```

---

### Post by daniel_w93 on 2008-12-05
whoohooo it works :D 
thank you soo much I was kinda desperate^^

---

