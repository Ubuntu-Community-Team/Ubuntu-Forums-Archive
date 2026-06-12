---
title: "Computer turned off during upgrade, now doesn't work"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by jsdieorksw on 2009-05-18
I was in the process of upgrading to jaunty on my desktop and someone in my house turned off the computer without finishing the upgrade and now it won't boot properly.  I can't do anything now. This is my desktop so I'm not able to access the internet from home so I can't give a detailed verbatim transcript of the error but I can provide one if need be.  Maybe I need to re-install but I can't seem to do anything after I boot up and get the error.  Can anyone help me fix this?

---

### Post by kstuart101 on 2009-05-18
Can you boot into single user mode?

If so, make sure the network is up and see if running 'do-release-upgrade' completes the upgrade.

BTW: Disclaimer, I'm fairly new to Ubuntu so this may not be the best solution.

---

### Post by jsdieorksw on 2009-05-18
Yes, I believe so

---

### Post by cariboo on 2009-05-18
You could also start in recovery mode, and once at the menu choose drop to root prompt, once at the prompt type:

```
dhclient eth0 
```

substitute your network device for eth0 if it is diffrent. The aboce command should get you an ip address and allow the computer to connect to the internet. Once you have an ip address, at the prompt type:

```
apt-get -f install
```

This should install any missing packages, then once that has run and finished, at the prompt type:

```
apt-get update && apt-get dist-upgrade
```

---

### Post by jsdieorksw on 2009-05-18
Great! Thanks, I'll try this in a little bit when i get home and post the results, thanks again!

---

### Post by jsdieorksw on 2009-05-18
It worked, I'm on my desktop now, thanks guys!

---

