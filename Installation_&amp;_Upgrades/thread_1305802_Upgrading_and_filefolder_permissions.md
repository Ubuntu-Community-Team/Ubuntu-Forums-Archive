---
title: "Upgrading and file/folder permissions"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Chrus on 2009-10-30
So like most people, I'm getting ready to upgrade to 9.10 (YAY!) Just have one question before I get started.

I've got a 320GB drive with Ubuntu on it, and a 1.5TB drive with all my stuff on it. I'm planning on doing a fresh install on the 320GB drive and leaving the 1.5TB in as is.

Now a fresh install is going to mean a new user, even if I have the same username/password, it will still be seen as a "new user". Right?

Is this going to cause problems? Will I be able to fix ownership with a chown? Can I do the same with my home folder?

Cheers

Chrus

---

### Post by momist on 2009-11-01
> **Chrus said:**
> 
Now a fresh install is going to mean a new user, even if I have the same username/password, it will still be seen as a "new user". Right?

Is this going to cause problems? Will I be able to fix ownership with a chown? Can I do the same with my home folder?
Chrus

Problems, yes.  I've just done a 'clean install' on the same partition my Jaunty was on, and it has not picked up the 'home' partition.  So now I have a new 'home' in the root, and my old 'home' is a drive only available to root!

I have a clonezilla backup of the whole hard disk under Jaunty, so I have a way back, but I'm not happy!  This didn't happen when I moved from Intrepid to Jaunty.

---

### Post by howefield on 2009-11-01
> **momist said:**
> I've just done a 'clean install' on the same partition my Jaunty was on, and it has not picked up the 'home' partition.  So now I have a new 'home' in the root,..

Sounds like you didn't tell the installer where your /home was...

> but I'm not happy!

Well, there you go, part of the learning curve.

---

### Post by SuperSonic4 on 2009-11-01
> **Chrus said:**
> So like most people, I'm getting ready to upgrade to 9.10 (YAY!) Just have one question before I get started.

I've got a 320GB drive with Ubuntu on it, and a 1.5TB drive with all my stuff on it. I'm planning on doing a fresh install on the 320GB drive and leaving the 1.5TB in as is.

Now a fresh install is going to mean a new user, even if I have the same username/password, it will still be seen as a "new user". Right?

Is this going to cause problems? Will I be able to fix ownership with a chown? Can I do the same with my home folder?

Cheers

Chrus

Not if you have a separate /home partition and do not format it. During the install you can point your new home to the existing /home partition. If you select the same username you keep your /home

---

### Post by Chrus on 2009-11-01
> **SuperSonic4 said:**
> Not if you have a separate /home partition and do not format it. During the install you can point your new home to the existing /home partition. If you select the same username you keep your /home

At the moment my home folder is sitting on the 320GB drive, the one I'm going to format. If I copy the folder to the 1.5TB drive, and point to that folder during the install and create a new user with the same name, would that work?

---

### Post by SuperSonic4 on 2009-11-01
It would be better as a separate partition rather than simply a folder. You can create a separate /home by following this guide: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If your home folder is an existing partition on the 320gb drive than yes, you can point it to there with no trouble. 

In both cases you'll have to manually specify /home through the manual partition option.

---

### Post by Chrus on 2009-11-01
> **SuperSonic4 said:**
> It would be better as a separate partition rather than simply a folder. You can create a separate /home by following this guide: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If your home folder is an existing partition on the 320gb drive than yes, you can point it to there with no trouble. 

In both cases you'll have to manually specify /home through the manual partition option.

Awesome. Thanks. I'll get stuck into that tomorrow arvo.

Cheers

---

