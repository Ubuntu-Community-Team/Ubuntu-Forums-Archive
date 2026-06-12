---
title: "Is there a command line to show current ubuntu version?"
date: 2008-11-14
forum: General Help
---

### Post by ProfessionalNewbie on 2008-11-14
Hi All,

I know uname -a shows similar info but I want to know whether it has Ubuntu 8.04 or 8.10, etc.
Is there any way to do this?
Thanks.

pf.

---

### Post by jolx on 2008-11-14
have a look at uname --help

edit: sorry that wont help

maybe 'cat /etc/issue'

---

### Post by adult swim on 2008-11-14
```
cat /etc/issue
```
or for more release info ```
lsb_release -a
```

---

### Post by ProfessionalNewbie on 2008-11-14
Ah, parfait!
Thanks guys.

Btw, would you know if this applies to all linux or just ubuntu/debian?

---

### Post by taurus on 2008-11-14
The "lsb_release -a" applies to Fedora too.

---

### Post by ProfessionalNewbie on 2008-11-14
Awesome thanks taurus!
You're a legend =)

---

### Post by Mardoct909 on 2008-11-14
A less sophisticated answer is see which image you have available for your desktop background.

---

### Post by ProfessionalNewbie on 2009-04-08
Hi all,

I tried running "lsb_release -a" in the latest Fedora 10 but the lsb_release command doesn't appear to exist.
Does a package need to be installed?
Sorry I know that's not ubuntu.

pn.

---

### Post by coffeecat on 2009-04-08
The python script for lsb_release is in /usr/bin in Jaunty. I vaguely remember some odd problem with the default user $PATH in Fedora, so it might be worth checking to see whether it's in the same place, or somewhere else, and then invoking the command with the full path. Or perhaps Fedora will only allow lsb_release to run with root privileges. Try su-ing to root and retry. And su with 'su -' which will give you the root $PATH.

What error do you get when you 'lsb_release'? Have you got python installed? And have you checked the Fedora package manager for lsb_release? I don't use Fedora regularly, but I like to have a quick look at each release (and then come scuttling back to Ubuntu :p) and I see the package manager is still woefully inferior to Synaptic. For that reason, I believe some regular Fedora users like to install yumex, which is a GUI frontend to yum. It might be easier to find lsb_release in yumex (if it exists) rather than in the default Fedora package-manager.

---

