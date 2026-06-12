---
title: "looking for sugestions for a better upgrade expereince."
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by everytimeref on 2009-10-23
It's generally accepted that a fresh install is the best way of upgrading Ubuntu, however I find this a pain.

We've all got lots of non-standard software running on our systems that is time consuming and frustrating to reinstall, not to mention fiddly things like fonts, themes, codecs, addons, non-free stuff.

No matter how organised I am, there is always something I forget usually something belonging to my wife.:(

What is the solution to this?

If Ubuntu is going to be serious OS rather than a "hobby OS" for enthusiasts this is something we need to solve.

I think Ubuntu is fantastic, my favourite OS by far and I want to be using the latest shiniest version **but** I also have 3 kids a life and a job and don't want the stress of reinstalling every 6 months.

---

### Post by MelDJ on 2009-10-23
then upgrade and dont do a fresh install:)
now i get what you mean. the internet cuts, etc.

---

### Post by Terrycymru on 2009-10-23
I have upgraded through several versions of Ubuntu without significant problems. When I bought a new computer earlier this year with Windows pre-loaded I opted for a WUBI install and have been very pleased with it. It seems to have no disadvantages over a conventional dual boot and has proved remarkably stable. Some commentators have suggested that a WUBI install runs the risk of being corrupted by a power cut but mine has survived 2 power cuts without a problem. However, I always keep a backup of the \ubuntu folder just in case.

As for Ubuntu's upgrade schedule of 6 months, I agree that this is probably too frequent for the average user. The LTS versions have support for 3 years and I may consider going with LTS versions when the next is released.

---

### Post by Mark Phelps on 2009-10-23
While a fresh install is generally considered better because you start off with a "clean slate", I believe that the recent spate of problems with just updating was due to a lot of folks having ATI restricted drivers installed and 9.04 not being able to either handle those drivers, or automatically remove them and install the open source drivers instead.

My own solution to this is different from what others do.  I maintain two versions of Ubuntu at all times -- the current and the previous.  When a new version comes out, I wipe the (old) previous and install the (new) current in its place. This has the advantage that ALL my customizations are still present in the (now) old version such that, in many cases, all I have to do is copy over config files to restore the customizations.

Also, I can take my time customizing the new version while still having the old working version in place. So, if something goes terribly wrong (like no display due to no longer supported restricted drivers), I sill have a working version I can boot into to fix the other.

When done, I simply change the default boot selection in GRUB and use the now fully customized new version by default.

Also, I have other machines on which I simply do an in-place upgrade, and since they don't have ATI cards, I've not encountered any problems in doing that -- all the way back to upgrading from 7.04.

Finally, it's ALWAYS a good idea to do full image backups.  There are several ways to do this, but I find using P.I.N.G is quick and easy.  This way, if an in-place upgrade goes bad, I can simply reboot and restore the image.

Sorry for the long response ... but you DID ask for suggestions.

---

### Post by donato roque on 2009-10-23
The fresh install solution is still the best.  I have a separate HOME partition which contains my config files and data.  Download the iso of the new version.  Burn it to a cd.  Install the os and mount my HOME partition back.  

Use Synaptic to save a file of your installed software and save it to your home directory.  Use this file to download the programs you have before.  Just make sure the file is updated before you install the new os. This method is not perfect because program names might change but then you'll be getting a message that a program is not found in the current repository.  No harm. Just download it separately using the new name.

---

### Post by everytimeref on 2009-10-23
Thanks for all the suggestions guys.

Donato, I didn't even know you could Use Synaptic to save a file of your installed software, I'll certainly be looking into that, atleast then it will mainly be my Wine stuff that will require manual installing. Can I save my repositories in this way?

The last Time I upgraded from 8.10-9.04 it worked flawlessly however the time before that I had some sort of HAL problem that resulted in none of my USB devices working, in the end I did a fresh install. 

9.10 seems to be  a more significant upgrade than 9.04: Ext4 as standard Grub2, neither of which I will get if I upgrade.

I wonder whether canonical would be better served with aiming alternate versions as Upgrade Versions with a once a Year- reinstall is best solution.

But I guess I've just answered my own question. Upgrade and reinstall on alternate versions.

Which brings me full circle to my original point, with the full flexibility of Linux can Ubuntu be user-friendly enough in it's upgrade policy for a casual user...

---

### Post by Mark Phelps on 2009-10-24
> **everytimeref said:**
> Donato, I didn't even know you could Use Synaptic to save a file of your installed software,
That's only true of stuff you installed through Synaptic.  Anything you downloaded and installed from source is NOT known to Synaptic.

> Which brings me full circle to my original point, with the full flexibility of Linux can Ubuntu be user-friendly enough in it's upgrade policy for a casual user...

Have no idea what "user-friendly enough" means -- probably something quite different to every user -- and THERE is the problem.

Given the huge flexibility of customizations available to Ubuntu users, there's simply NO WAY that Canonical can guarantee that an in-place upgrade will go perfectly for everyone.

Which is why I use the method I documented in a prior post.

---

