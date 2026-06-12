---
title: "Upgrading the builds. Need a sticky how to written."
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by oldsoundguy on 2009-07-23
Here it is in a nutshell.  Many are now using a form of Linux, be it Fedora or Ubuntu or whatever and they like using it.
BUT there is the issue of UPGRADING to a newer version and being able to save all that work that has been devoted to tweaking their system to their own personal needs.

IMO, it is time for a guide to be compiled telling just HOW to save the home file, bookmarks, addy book,  and installed programs and anything else of importance (data, pictures, docs etc) .. all in one and all ON one device (be it a thumb drive, as second hard drive, or burn it to a disk).
First list the things to check for saving AND their location.
Then HOW to save them (drag and drop, use a burning program etc .. the OPTIONS available)
And FINALLY, how to bring them into the new build and get them operational.

I know there are various threads all over this forum about doing this .. some are very good and some are really written poorly and are far more complicated than need be .. but, just like the basic install thread or book (the Keir Thomas pocket reference,for instance), It sure would be nice if it was all compiled into ONE place.  ESPECIALLY for someone new or newer to the system that is updating for the first time!

---

### Post by snowpine on 2009-07-23
Let me tell you a secret:

```
sudo do-release-upgrade
```

---

### Post by oldsoundguy on 2009-07-23
> **snowpine said:**
> Let me tell you a secret:

```
sudo do-release-upgrade
```


And that saves and re-installs all of your PERSONAL files?

What if you want to do a NEW CLEAN install of a new version for reasons such as borked video or audio in the older version?  How about THAT instance?

A GUIDE would sure be nice.  And I am assuming that it would be even better for a newbie.  NOT EVERYONE is a tech and spends hours immersed in learning the ins and outs of the system.  Many just want to USE the system because of it's stability and security.  They really do NOT care WHY such and such line of code does what it does.

Why learn how to rebuild a transmission when all you want to do is drive the car?

---

### Post by snowpine on 2009-07-23
> **oldsoundguy said:**
> And that saves and re-installs all of your PERSONAL files?


It will upgrade your system to the next Ubuntu release, with all applications, personal files, settings, and tweaks intact. 

You're of course welcome to write a more detailed guide--I'm sure some users would appreciate it--but *my* work here is done. ;)

---

### Post by oldsoundguy on 2009-07-23
> **snowpine said:**
> It will upgrade your system to the next Ubuntu release, with all applications, personal files, settings, and tweaks intact. 

You're of course welcome to write a more detailed guide--I'm sure some users would appreciate it--but *my* work here is done. ;)

Thanks!  Good tip.

Now what if you install a build and find it is kludged beyond recognition and have to backtrack? hmmmmm

---

### Post by Mark Phelps on 2009-07-23
> **oldsoundguy said:**
> ... and anything else of importance ... 

That little phrase is what makes such a guide nearly impossible to write.

OK, so I've seen people say backup /home and everything under it.  That's just the tip of the iceberg!!

To get "anything else of importance" you would have to be able to identify and save off EVERY single customization a person did.  And, in the case of Ubuntu, every one of those would most likely be resident in a different place and file.

Just to name a few: boot menu changes, boot screens, startup settings, account settings, run-level customizations, driver customizations, desktop themes, font changes, installed applications -- with all their config settings (default and custom), all their runtime files, and all their account-related files and data files -- anything build from source (regardless of where the make scripts ended up putting the intermediate and final components).  Lets not forget anything they installed or customized with Wine or Crossover, or Play4Linux, or ... or ...

And every one of these different things has the potential to have a myriad of files scattered all over the file system.  Sure, most things are in "bin" directories -- but which ones? user/bin? user/local/bin? user/sbin?

The end result of attempting to save "anything of importance" of a well-customized install could easily ramp up to hundreds and hundreds if not thousands of files.

And you know how this will work ... even if such a "backup" feature was available, the few times it missed a handful of minor things are the times that folks will be yelling and screaming the loudest about how an upgrade "trashed their system"!!

I do agree, however, that a simpler mechanism for saving off the current installation (along the same lines as "windows.old" in some MS upgrades) would be a useful recovery mechanism in the case that an upgrade really trashed the current install.  This approach would create an archive of the current installation and save it into a single file, and create an entry in the menu.lst file such that you could choose that and restore your current installation from the backup.  Despite all the heated bashing we read of MS on these forums, they do have this mechanism already in place for major OS upgrades.  It would be really great if Canonical could do something along the same lines for Ubuntu -- instead of messing around with wallpapers and boot screens.

But .. that's just my opinion ... for what it's worth (not much).

---

