---
title: "mandatory updates ?  + 9.10 beta"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by eric489 on 2009-10-11
Hi !

1) I've recently installed ubuntu 9.04 on an "old" pc.

Just after installing I got the update window stating that more than 200 updates were available. 

As I scrolled down the list, I noticed most were kinda useless, or unnecessary for my pc. ( some server stuff, firefox extensions...)

So do I really need all these updates or is it just optional ?

 
2) As the 9.10 release gets closer and closer, I wondered the following :

Is the Ubuntu 9.10 latest beta better than the 9.04 stable April released version ? 

If I decide to install the 9.10 beta, is it possible to upgrade the whole system to stable 9.10 (once it's released) without having to pass through a cd install process ?

Or can even pass from my current 9.04 to stable 9.10 via apt-get once it comes out ?

Thanks in advance !

---

### Post by mikewhatever on 2009-10-11
> **eric489 said:**
> Hi !

Is the Ubuntu 9.10 latest beta better than the 9.04 stable April released version ?

I don't think better is the word. 9.10 is newer, should boot faster, it looks differently and is not yet finished. 

> If I decide to install the 9.10 beta, is it possible to upgrade the whole system to stable 9.10 (once it's released) without having to pass through a cd install process ?

Nothing special here, just keep installing updates as they come. That said, expect quite a lot of updates.

> Or can even pass from my current 9.04 to stable 9.10 via apt-get once it comes out ?

Thanks in advance !

You'll get a notification that the new release is available in the update manager. I don't know if upgrading will work from an unupdated installation though.

---

### Post by eric489 on 2009-10-24
> **mikewhatever said:**
> I don't think better is the word. 9.10 is newer, should boot faster, it looks differently and is not yet finished. 



Nothing special here, just keep installing updates as they come. That said, expect quite a lot of updates.



You'll get a notification that the new release is available in the update manager. I don't know if upgrading will work from an unupdated installation though.

Thanks a lot !

But what about my first question ?

" Just after installing I got the update window stating that more than 200 updates were available. 

As I scrolled down the list, I noticed most were kinda useless, or unnecessary for my pc. ( some server stuff, firefox extensions...)

So do I really need all these updates or is it just optional ? "

---

### Post by slakkie on 2009-10-24
All upgrades are optional. You don't have to upgrade packages, but most, if not all of the updates you receive are bugfixes/security fixes for your installed packages. So it is advised to do so.

If you think you don't need a particular package, remove it. You will not get update notifications for those packages.

Upgrading from 9.04 to 9.10 without having updated all of the packages should be possible, although I've trained myself always to upgrade the current packages and then to the upgrade to a different release. But it is not needed per se, to my knowledge. The upgrade to another release will upgrade all packages you already have.

---

