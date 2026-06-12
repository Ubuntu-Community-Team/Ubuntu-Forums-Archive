---
title: "KDM and XDMCP problems"
date: 2005-11-24
forum: General Help
---

### Post by pestie on 2005-11-24
I'm beating my head against the wall with this, and I hope someone here can help. I cannot get KDM to allow remote XDMCP requests. I have it working fine with GDM, but since I run KDE as my desktop I'd like KDM as my display manager as well - KDM allows me to easily switch users and start new X sessions on other VT's from the KDE desktop, which is very handy for multi-user environments.

My kdmrc has these lines:
```

[Xdmcp]
Enable=true
Willing=/etc/kde3/kdm/Xwilling

```

And my Xaccess contains this line:
```

*                                       #any host can get a login window

```

When I attempt to connect with a remote X server using something like this:
```
X -terminate -query 1.2.3.4
```
...it fails silently. Now, if I comment out the line above in Xaccess, I get an error about the host being unwilling to manage the remote display, which makes sense, and proves that I am in fact talking to KDM on port 177 (the XDMCP port). I just can't figure out why it's failing when it works fine with GDM. Any ideas?

---

### Post by feathers on 2005-11-25
Try to connect to that machine with kdm's feature remote login or something. It works with me with more than 10 very old computers that run on one machine. I have never tried this on the command line so I can't geive you help there.

---

### Post by pestie on 2005-11-25
Well, I'm not running KDE on the terminal machine, so I can't really do that. It's an old 400 Mhz P-II and while it works great as a remote terminal, it drags ass like nobody's business if I try to run any processor- or memory-intensive desktop on it. I'm sure I'm just missing something fairly trivial, but without any error messages or log files I'm kind of at a loss. It certainly appears that I'm doing everything right but it's just not working.

---

### Post by TheOrangeRider on 2005-11-30
I'm having the exact same problem. It seemed to work fine in Hoary, but ever since I upgraded I haven't been able to get it to work. A clean install of Breezy hasn't worked either. Any ideas anyone?

---

### Post by KermitJr on 2006-03-07
Same problem here....

I'm trying to get it to work with Xnest.  I can Xnest :1 and get a terminal with #xterm -display :1 but no kdm.

---

### Post by patrixl on 2006-03-07
This bug has been encountered many times by people on this forum. I've experienced the same bug, both on Kubuntu and FreeBSD. Additionally on Kubuntu I've seen the same in xdm. 

wdm works fine though (not as pretty as kdm but at least it works!), and it's one apt-get away.

EDIT: I've upgraded to KDE 3.5.1 using the kubuntu packages announced on the main page, and xdmcp works with kdm!!!!!!!!!!!!!!!

---

### Post by KermitJr on 2006-03-07
I finally got it to work.

I opened synaptic and did "Complete removal" of:

kdm
kdebase-bin

Then:
```
apt-get install kubuntu-desktop
```
This uninstalled and re-installed a large amount of programs and one prompted to overwrite the kdmrc file with an updated one.  I said yes and continued.

At the end end, I edited ```
/etc/kde3/kdm/kdmrc
``` to ```
[Xdmcp] enable=true
``` and restarted kdm via: ```
sudo /etc/init.d/kdm restart
```
Voila! now  ```
Xnest -query localhost :1
``` gives me a kdm login screen.

I'm not sure why simply trying to update didn't rewrite that kdmrc file, but the newer version is significantly different from the older version.

(PS: Don't forget to change the /etc/kde3/kdm/Xaccess file line #*     to *   )

---

