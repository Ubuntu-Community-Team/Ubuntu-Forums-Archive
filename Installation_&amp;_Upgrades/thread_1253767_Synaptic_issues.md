---
title: "Synaptic issues"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by fakinbacon on 2009-08-30
I'm always hesitant to making a new thread fearing I am asking a very common question but I'm frustrated so I'm not so worried about that right now. 

I was installing a couple packages on Hardy and the installation stopped midway. I checked the Details tab and it seemed to be a failed installation. Then without thinking I closed Synaptic and I tried the install in terminal. I got the error message that includes "you must manually run 'dpkg --configure -a' to correct the problem."

Fine

So I did so. I am familiar, but when I run "dpkg, etc, etc" I just get the same thing. It tries to install the package but with the same result of the installation stopping indefinitely midway.

That is how I cannot install anything unless I can find a tarball or deb.

---

### Post by drs305 on 2009-08-30
Assuming you ran "**sudo** dpkg --configure -a" :

I think you have done this, if not: try specifically installing one of the packages via command line and see what other error messages you get:
```

sudo apt-get install <appname>

```

If that is what you are trying, do you get any *other* error messages?

Added: Have you checked in synaptic's lower left pane, Custom Filters, Broken?

---

### Post by fakinbacon on 2009-08-30
> **drs305 said:**
> 
Added: Have you checked in synaptic's lower left pane, Custom Filters, Broken?

Upon my last check synaptic wouldn't even open before displaying the error message then closing. I'll have to check upon returning home.

---

### Post by fakinbacon on 2009-08-30
also, sorry for not clarifying. 'sudo apt-get [pkg_name]' doesn't work. same error message.

---

### Post by drs305 on 2009-08-30
> **fakinbacon said:**
> also, sorry for not clarifying. 'sudo apt-get [pkg_name]' doesn't work. same error message.

Okay, try this then before posting again:
```
sudo apt-get install -f
```
You can read what the "-f" switch does by typing "man apt-get" in terminal.

---

### Post by fakinbacon on 2009-08-30
```
matthew@AnneHog:~$ sudo apt-get install -f
[sudo] password for matthew: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

That was ineffective. :confused: Oh well. Any help or even just ideas are greatly appreciated.

---

### Post by fakinbacon on 2009-08-30
So I returned home and there are no additional error messages. Just the one.

---

