---
title: "Broken packages?"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by Lukeman on 2008-12-24
Ok, I am new to the whole Ubuntu experience.  I have always been attracted to it, and am now trying it out for the first time.

I am on a laptop, therefore I have a 250GB external HD that I am putting the whole Ubuntu on, my internal is only 80GB and I have already used around 60GB.  So I installed Ubuntu fine on the external and it booted up just fine.  Everything worked on it.  Then I get the message "322 updates found". So I downloaded them all, then started installing all of them.  Every time I would try to install them, it would come up "1 package is broken, use the Broken filter to find it".  Well, I didn't know how to do that, so I just kept trying, and it finally installed some of them.  But I looked for help, and found the interface of Package something.  So I find the thing that says, fix broken packages, so I try that, and just keep getting an error.  So I tried to restart it, so some of the updates would work, and now I can't even log in anymore.  I failed, epically.  If anyone has some suggestions of what I can do, start from scratch, etc, that would be greatly appreciated.

Thanks,
Luke

---

### Post by zvacet on 2008-12-24
On the start when you see grub select recovery mode and boot in it.After you are loged in type

```
apt-get -f install
```

---

### Post by Lukeman on 2008-12-24
> **zvacet said:**
> On the start when you see grub select recovery mode and boot in it.After you are loged in type

```
apt-get -f install
```

Where do I type that at?

---

### Post by StOoZ on 2008-12-24
in the terminal

---

### Post by zvacet on 2008-12-24
> Where do I type that at?

When you boot in recovery mode it will be obvious where to type.

---

