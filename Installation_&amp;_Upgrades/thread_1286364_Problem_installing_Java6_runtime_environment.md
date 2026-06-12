---
title: "Problem installing Java6 runtime environment"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by wasi_deer on 2009-10-08
I am trying to install Sun Java runtime envoirenment in my operating system but it is giving me this error,
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Can someone help to figure it out???

---

### Post by jeremyswalker on 2009-10-08
How exactly did you try to install it?

---

### Post by wasi_deer on 2009-10-08
I tried it from "Applications>Add Remove Program>internet"

---

### Post by jeremyswalker on 2009-10-08
Try to install this way:
```
sudo aptitude install sun-java6-jre
```

Or if you would rather: Go to "System > Administration > Synaptic Package Manager" and search for "sun-java6-jre". Select it and click apply.

Let me know if it works.

---

### Post by wasi_deer on 2009-10-08
Its not working.
Synaptic Package Manager turns off showing the same error message

---

### Post by jeremyswalker on 2009-10-08
First of all, I made a mistake in the previous command. I don't know what I was thinking, but it should be 'sun-java6-jre' not 'flashplugin-installer'. I fixed my post to reflect this.

However, it doesn't sound like that will help you at the moment. I think that you should open up a terminal (Applications > Accessories > Terminal) and execute:
```
sudo dpkg --configure -a
```
It sounds like you have packages that weren't configured all the way.

---

### Post by wasi_deer on 2009-10-09
Its still not working, this is shown in the terminal window.
"sudo: dpkg--configure-a: command not found"

---

### Post by wasi_deer on 2009-10-12
It is working dear, thanks a lot...

---

### Post by inkisbetter on 2009-10-13
I am having a similar problem.  running the "configure" command recommended helped and allowed me to run the "aptitude install" command (prior to the "configure" command, I couldn't run an install at all).  But now I'm hitting the same roadblock that got me into this mess.  It starts installing then I get to the Blue license screen and I can't do anything.  I hit enter to signify "ok" but nothing happens. 

Any help?

---

### Post by Mighty_Joe on 2009-10-13
> **inkisbetter said:**
>  I hit enter to signify "ok" but nothing happens. 

If you look at the screen, you'll see that the sidebar is red, indicating that it is selected.  Hit "tab" until the "OK" button is selected and hit "enter".

---

### Post by inkisbetter on 2009-10-13
Mighty-Joe, 

Thanks, that worked.  I'd actually just found the same answer here: 

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/378126](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/378126) 

I found this after I tried to install it via kpackagekit & got an error. 

Thanks!  Love getting solutions w/in minutes of posting the problem!  You guys rock!

---

