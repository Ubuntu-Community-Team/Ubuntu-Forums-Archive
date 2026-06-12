---
title: "Problems after fresh installation"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by _jj on 2009-01-09
Just tried a fresh installation of Kubuntu 8.10
I partitioned my hard drive in the following way

3 Primary partitions
2Gb /dev/sda1 Swap
15Gb /dev/sda2  mount as /
15Gb /dev/sda3 left for use with other distros

2 Logical partitions
35Gb /dev/sda5 mount as /home
10Gb /dev/sda6 mount as /data for back up

Installation seemed fine and I had checked that the liveCD worked.

However on 'restarting' to finish installation, I get the login screen, attempt to login and the login screen doesn't get past the picture of the hard drive.  It also won't start in failsafe mode, giving me and error regarding the x-server.

Any ideas I should try before just restarting, especially if it is something I did wrong the first time round?

---

### Post by _jj on 2009-01-09
Update:
the error message I am getting when trying failsafe mode is
"
Xsession: unable to launch failsafe X session --- x-terminal-emulator not found; aborting.
"

I have tried console login, which works but "startx" then produces a lovely though not very helpful purple screen

---

### Post by _jj on 2009-01-09
I have started again with ubuntu 8.04 rather than kubuntu 8.10 which seems to work so I think maybe it is a problem with KDE 4.1

---

### Post by _jj on 2009-01-16
I think the problem may be to do with poor use of the onboard intel graphics card, I am attempting to fix this in ubuntu and then will retry the KDE desktop.  Has anyone else been having similar problems?

---

### Post by abn91c on 2009-01-16
compiz dont work with some intel 845/945 series cards due to a bug in the driver, only solution is to remove compiz

---

### Post by _jj on 2009-01-17
Is it safe to just remove compiz? if it is not enabled I assume I simply get the same as when desktop effects is set to none?

---

### Post by abn91c on 2009-01-17
> **_jj said:**
> Is it safe to just remove compiz? if it is not enabled I assume I simply get the same as when desktop effects is set to none?
completely safe, compiz is just "eye candy",  on some PC's you may also have to do in a terminal ```
kwin --replace
``` after removing compiz, dont forget to reboot :-)

---

### Post by Truefire on 2009-01-17
That's all un-needed. he just needs to reburn the disk, kde probably lost a library file, that's all.

---

### Post by abn91c on 2009-01-17
with kubuntu 8.10 and Intel 845 video compiz/desktop effects have to be disabled or he will never log in.

---

### Post by _jj on 2009-01-20
Is there any known way to get and 845 video card to work well with ubuntu/linux (I have looked and it seems like there is a bit of a problem/it is tricky) or am I better to cut my losses and buy a supported card?

---

### Post by channingmoore on 2009-03-04
> **_jj said:**
> I think the problem may be to do with poor use of the onboard intel graphics card, I am attempting to fix this in ubuntu and then will retry the KDE desktop.  Has anyone else been having similar problems?

I'm having the same problems right now; I've just done a clean install on an older box at home that definitely has the 845 onboard graphics. I'll update this if I figure out better what's going on; right now, I can't do much of anything except through a console logon because failsafe is also broken.

---

### Post by channingmoore on 2009-03-04
> **abn91c said:**
> compiz dont work with some intel 845/945 series cards due to a bug in the driver, only solution is to remove compiz

... aaaannnnd, sure enough,

```
sudo aptitude remove compiz-wrapper
```

gets the job done. Fine for my case, because I'm using this for a home server where the graphics are nice but don't need to be pretty.

---

### Post by _jj on 2009-12-07
In the end I opted for a new cheap nvidia card which solved my graphics problems and gave me a reasonable performance boost, so it was probably worth it.

---

