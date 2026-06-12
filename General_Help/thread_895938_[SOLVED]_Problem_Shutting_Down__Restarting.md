---
title: "[SOLVED] Problem Shutting Down / Restarting"
date: 2008-08-20
forum: General Help
---

### Post by robelliott2125 on 2008-08-20
When I click my shutdown button, to either restart or shutdown, I used to be shown a full list of options:

Log Out | Lock Screen | Switch User
Hibernate | Shutdown | Restart etc

Now all I'm getting is:

Log Out | Lock Screen | Switch User
           Hibernate

I have already spoken to people on IRC, which have tried to help, so here is what has been tried so far:

Groups

```
robert@robert-desktop:~$ groups
robert adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin vboxusers

```

Killall

```
robert@robert-desktop:~$ killall kwin
kwin: no process killed
```

To try and help further, I have installed Kubuntu alongside Ubuntu, using Synaptic, moreso to use as seperate environments, but I have never managed to solve this, and it instead loads as a mixed desktop.
This is having freshly installed Hardy, and I have had this problem on both Gutsy and Hardy now (with the Kubuntu / Ubuntu mixed).

To restart / Shutdown at the minute, I have to chose logout, for it to goto the login screen, for me to chose what to do from there.

Its nothing major or important, but I would like to solve this problem.

Thanks in advance!

---

### Post by robelliott2125 on 2008-08-22
Anyone?

Anything anyone can suggest, i'm willing to try.

Thanks,

---

### Post by aloshbennett on 2008-08-22
hmm.. shutdown and restart requires more previlages. A shot in the dark, do you still have admin rights on your machine?

---

### Post by robelliott2125 on 2008-08-22
I'd believe so.

I can still Sudo bash, and I am the only user on the pc (apart from Root).

---

### Post by showcaser on 2008-09-08
I had the same problem as a result of having installed KDE4 alongside Gnome. Then my restart and shutdown buttons disappeared in Gnome. The fix was to restore GDM as my default display manger.

You can do that by running  

```
sudo dpkg-reconfigure gdm
```

and selecting "gdm".

If that's not your problem have you tried:

[http://ubuntuforums.org/showthread.php?t=901072&highlight=restart+shutdown](http://ubuntuforums.org/showthread.php?t=901072&highlight=restart+shutdown)

Good luck!

---

### Post by robelliott2125 on 2008-09-08
> **showcaser said:**
> I had the same problem as a result of having installed KDE4 alongside Gnome. Then my restart and shutdown buttons disappeared in Gnome. The fix was to restore GDM as my default display manger.

You can do that by running  

```
sudo dpkg-reconfigure gdm
```

and selecting "gdm".

If that's not your problem have you tried:

[http://ubuntuforums.org/showthread.php?t=901072&highlight=restart+shutdown](http://ubuntuforums.org/showthread.php?t=901072&highlight=restart+shutdown)

Good luck!

Hi,

Thanks for the reply, i did eventually get this solved, and then removed KDE.  This is solved.

---

### Post by wvtienen on 2008-09-08
=> in System/Management/LoginScreen/ Tab Local you can toggle this behavior by ticking 'Show action Menu' (this was a translation from Dutch).

Personaly I like this option for the kids; so they cannot shutdown the computer, but only hibernate.

Walter

notice: I hate solution in Linux require the use of shell scripts.

---

