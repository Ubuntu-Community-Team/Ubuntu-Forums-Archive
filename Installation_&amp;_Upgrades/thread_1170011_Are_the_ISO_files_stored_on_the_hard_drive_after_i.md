---
title: "Are the ISO files stored on the hard drive after intallation?"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by AnimalCrosser5 on 2009-05-25
I've been using Ubuntu for a while now, and I haven't really touched Windows since I've been using it, and now I want to uninstall Vista altogether, but since I installed Using Wubi and would like a fresh install anyhow, I figured that I'd back up the files I want to keep and then format my hard drive. Then I plan to install Ubuntu from a CD. 

But since I don't want to wait all night to download an ISO or Upgrade from the 8.10 CD I have (somewhwere) I was wondering if the files I need to burn to disc are already on my hard drive somewhwere, or should I start downloading an ISO now?

---

### Post by cariboo on 2009-05-25
If you want to create an exact copy of your wubi installation use something like [Remstersys]("http://www.geekconnection.org/remastersys/remastersystool.html")to create the image, then partition your hard drive and clone your system to your hard drive.

---

### Post by AnimalCrosser5 on 2009-05-25
That's cool, but I want a clean install with all the defaults, could I achieve that with this tool?

---

### Post by AnimalCrosser5 on 2009-05-25
I've added remastersys to the repositories, but there aren't any packages in it. Is there another way to get it, or another program that does the same thing?

---

### Post by VastOne on 2009-05-26
> **AnimalCrosser5 said:**
> I've added remastersys to the repositories, but there aren't any packages in it. Is there another way to get it, or another program that does the same thing?

If you have installed remastersys, it will be under Panel/Administration.

And it works just as Cariboo907 said

---

### Post by AnimalCrosser5 on 2009-05-26
It isn't installed. I added 

deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/

to software sources and it shows up in synaptic, but under it, there aren't any packages.

---

