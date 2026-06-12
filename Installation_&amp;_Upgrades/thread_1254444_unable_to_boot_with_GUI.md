---
title: "unable to boot with GUI"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by GriZzlEnLS on 2009-08-31
Hey for some reason I am unable to boot with the GUI on 9.04 after installing the nvidia restricted drivers gives me an error about not being able to run in a certain res then goes to another default res that looks like it just runs in terminal. I have installed this before and just wanted to try it on this new system I built. Any thoughts? I am using a nvidia 260 216 core in SLI if that helps. Thanks

---

### Post by shredder12 on 2009-08-31
Try running
```

sudo /etc/init.d/gdm restart
```

---

### Post by GriZzlEnLS on 2009-08-31
Yea just tried it it showed it stopped and restarted but still on the same window. Is it maybe x11? and if so how would I restart that?

---

### Post by shredder12 on 2009-08-31
So, you mean after getting the error you were shifted to text mode..??? 
or did you mean something else??

---

### Post by donpedrodos on 2009-08-31
Try to startup in the recovery mode and there will be an option to [repair your xserver settings]("http://ramonecung.com/blog/2008/07/13/fix-x-server-problems/").

---

### Post by GriZzlEnLS on 2009-09-01
Yes it shifted me to text mode I have tried to reinstall and I get the GUI until I use the restriced drivers. Never seen it before.

---

### Post by shredder12 on 2009-09-01
> **donpedrodos said:**
> Try to startup in the recovery mode and there will be an option to [repair your xserver settings]("http://ramonecung.com/blog/2008/07/13/fix-x-server-problems/").

Have you tried this??

---

### Post by shredder12 on 2009-09-01
> **GriZzlEnLS said:**
> Yes it shifted me to text mode I have tried to reinstall and I get the GUI until I use the restriced drivers. Never seen it before.

Hey sorry i didn't see this at first..
so you mean that  you are able to get the gui but when you shift to restricted drivers you are thrown to text mode..
if this is the problem then we can try installing the graphic drivers another way..

---

### Post by GriZzlEnLS on 2009-09-03
So I have tried the above set unfortunately it did not work. The exact message I am getting when I boot is:

Ubuntu 9.04 FrankeII tty1

Frankie login: 

not sure if that will help

---

### Post by shredder12 on 2009-09-03
> **GriZzlEnLS said:**
> The exact message I am getting when I boot is:

Ubuntu 9.04 FrankeII tty1

Frankie login: 



So, you are booted directly to the text mode..
You have already tried restarting gdm so i don't think "startx" would help..
But still give it a try
```
startx
```

If there is some configuration problem that is not letting you to shift to gui even in low graphics mode then probably I won't be abe to help you
          You might have to uninstall the restricted drivers in order to change the configuration

---

