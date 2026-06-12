---
title: "I am missing the package installer"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by Unbutu Person on 2009-02-03
I have a problem when ever I try to install something I get an error it is always the same  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have no idea what that means.Then I figured out that I was missing software sources.I am using Ubuntu 8.04 LTS.Synaptic Package Manager doesn't work I get the same error.Same with update manger.

---

### Post by Crafty Kisses on 2009-02-03
Try running the following in Terminal:
```
sudo dpkg --configure -a
```

---

### Post by abn91c on 2009-02-03
open a terminal then type ```
sudo dpkg --configure -a
```followed by```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kostkon on 2009-02-03
Close *Synaptic* or *Add/Remove* (or the Update Manager), if you have them open. Then open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give:
```
sudo dpkg --configure -a
```
it will ask you for a password, give yours.

Then, in the terminal again, give
```
sudo apt-get update
```

You should then be fine.

Hope that helps.

---

### Post by kostkon on 2009-02-03
LOL! 3 replies in under a minute... (well almost)!

---

### Post by Unbutu Person on 2009-02-03
How do you run in Terminal?

---

### Post by kostkon on 2009-02-03
> **Unbutu Person said:**
> How do you run in Terminal?
You'll find it in Applications &#8594; Accessories

---

### Post by Unbutu Person on 2009-02-03
Why won't Terminal let me type in my password?

---

### Post by kostkon on 2009-02-03
> **Unbutu Person said:**
> Why won't Terminal let me type in my password?
Yeah, sometimes it is confusing... Your password does not appear for security reasons. Don't worry, just type it and press enter.

---

### Post by Unbutu Person on 2009-02-03
Thank you for your time and help it worked.

---

### Post by Crafty Kisses on 2009-02-03
We're glad that we can help. :)

---

