---
title: "Synaptic: &quot;W: Failed to fetch&quot;"
date: 2008-11-15
forum: General Help
---

### Post by andrewthecoder on 2008-11-15
Very little to say on this one, I simply cannot install software. 
Upon clicking "Apply" in Synaptic, the following is displayed (obviously depends on the packages chosen) 

> W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/b/binfmt-support/binfmt-support_1.2.10_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/b/binfmt-support/binfmt-support_1.2.10_all.deb)
  Could not connect to proxy.carnegiecollege.ac.uk:8080 (212.219.195.8), connection timed out


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9.1-1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9.1-1_i386.deb)
  Unable to connect to proxy.carnegiecollege.ac.uk 8080:


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.0.28a-1ubuntu4.5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.0.28a-1ubuntu4.5_i386.deb)
  Unable to connect to proxy.carnegiecollege.ac.uk 8080:


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_1.0.0-1ubuntu4~hardy1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_1.0.0-1ubuntu4~hardy1_i386.deb)
  Unable to connect to proxy.carnegiecollege.ac.uk 8080:


Now, it is obvious to me that the application is attempting to access the repos via my campus proxy, however I am at home, connected via my wifi router.
I have searched through all the gui-available settings and found nothing to show/allow editing of a proxy configuration, and nothing seems to mention that proxy URL.
I can connect to the internet fine, hence this message, the problem seems only with apt or perhaps synaptic itself?
No changes when I connect directly with my ethernet cable either.

My sources list contains only the following:

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


...so nothing unusual there, though I've never seen those repos before (I also have a desktop PC with hardy on)

So I guess my question is somewhere along the lines of, why would apt/synapticuse a proxy but not firefox or any of my other applications? (pidgin, skype for example)

Thanks a lot, and I hope it isnt something stupid which I have missed, though I am modest enough to admit that is likely =)

~Andrew

---

### Post by taurus on 2008-11-15
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and change to another server.  Use the Main Server if you wish.  Then, Reload and see if you can update your machine now.

---

### Post by dcstar on 2008-11-15
> **andrewthecoder said:**
> Very little to say on this one, I simply cannot install software. 
Upon clicking "Apply" in Synaptic, the following is displayed (obviously depends on the packages chosen) 
........

[http://ubuntuforums.org/showpost.php?p=6187694&postcount=4](http://ubuntuforums.org/showpost.php?p=6187694&postcount=4)

---

