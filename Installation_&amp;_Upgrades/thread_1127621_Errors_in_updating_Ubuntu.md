---
title: "Errors in updating Ubuntu"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by tamas305 on 2009-04-16
I have a similar problem as the people on this [thread]("http://ubuntuforums.org/showthread.php?t=1017243") 

When I checked for new updates using dukes archive server because I had the same problem downloading the packages from the main Ubuntu server.

This is what the error message said

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I am fairly new to Ubuntu so help is much appreciated.

Thank you in advance

-tamas

---

### Post by sisco311 on 2009-04-16
Open a terminal (Applications -> Accessories -> Terminal) 
and run:
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```

---

### Post by tamas305 on 2009-04-16
It worked perfectly.

Thank you!

Just wondering, is it safe to download all of the files listed under the update manager? Are they really needed?

-tamas

---

### Post by drs305 on 2009-04-16
> **tamas305 said:**
> 
Just wondering, is it safe to download all of the files listed under the update manager? Are they really needed?

-tamas

If you are using the ubuntu 'official' repositories, they are safe. Of course, *safe* is a relative term. If you search the forums you will find posts by users whose system started misbehaving after updates.

The updates in the official repositories have been tested by the ubuntu team and have shown to work properly on most systems. Updates from third-party repositories, "proposed" or "backports" are either not as well-tested or have not been reviewed by ubuntu package reviewers.

If you open synaptic (System, Administration, Synaptic Update Manager), you can select what you want updated. Go to Settings, Repsositories, Updates. You should definitely select "Important security updates". Most users probably also select "recommended updates". You can also decide which repositories you want to enable in the "Ubuntu Software" tab.

You can review the Ubuntu documentation on Repositories here to learn what each section has to offer. Armed with that knowledge you can make an informed decision on what you allow to update:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

