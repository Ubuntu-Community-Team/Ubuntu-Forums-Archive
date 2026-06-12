---
title: "Too Many Updates"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by dgoddard1 on 2008-12-11
I am kind of new at Ubuntu but
I have just reinstalled 
-- Ubuntu 8.04
-- Kernel 2.5.24-16-generic
-- Gnome2.22.1
On my Dell Studio 1535 laptop.

I ran Update manager and after it did some internet accessing it came back and told me it had found 1049 updates for me.  It preselected all of them, most of them look like they have nothing to do with my interests. (e.g. a vast number of language pack items for languages most I have not even heard of before) 

I can only seem to deselect them one at a time so I figured I would install all of them.  After it got my password, it caqme back with a dire warning:
--- 
"You are about to install software that can't be authenticated!
Doing this  could allow a malicious individual to damage or take control of your system."
---
the two that were listed under "NOT AUTHENTICATED" were
  linux-ubuntu-moules-2.6.24-16-generic
  linux-ubuntu-modules-2.6.24-22-generic
There were 12 listed under "To be installed"
The rest were listed under "To be upgraded"

It is impractical is to try to go through the list and pick and choose because the brief explanations are mostly meaningless to me

What is the real risk of just installing all of of them.

Is this going to tie up my computer for hours?  Because the only broad band available to me is at the public library where they have wireless available to the patrons.

Is there some way to deslect them in a more efficient manner than  one at a time for 1049 individual decisions

---

### Post by 2hot6ft2 on 2008-12-11
> **dgoddard1 said:**
> I am kind of new at Ubuntu but
I have just reinstalled 
-- Ubuntu 8.04
-- Kernel 2.5.24-16-generic
-- Gnome2.22.1
On my Dell Studio 1535 laptop.

I ran Update manager and after it did some internet accessing it came back and told me it had found 1049 updates for me.  It preselected all of them, most of them look like they have nothing to do with my interests. (e.g. a vast number of language pack items for languages most I have not even heard of before) 

I can only seem to deselect them one at a time so I figured I would install all of them.  After it got my password, it caqme back with a dire warning:
--- 
"You are about to install software that can't be authenticated!
Doing this  could allow a malicious individual to damage or take control of your system."
---
the two that were listed under "NOT AUTHENTICATED" were
  linux-ubuntu-moules-2.6.24-16-generic
  linux-ubuntu-modules-2.6.24-22-generic
There were 12 listed under "To be installed"
The rest were listed under "To be upgraded"

It is impractical is to try to go through the list and pick and choose because the brief explanations are mostly meaningless to me

What is the real risk of just installing all of of them.

Is this going to tie up my computer for hours?  Because the only broad band available to me is at the public library where they have wireless available to the patrons.

Is there some way to deslect them in a more efficient manner than  one at a time for 1049 individual decisions
Strange that the kernel updates would be "NOT AUTHENTICATED" but if you want to see what they are (a better description of each) close Update Manager and go to Synaptic.

System>Administration>Synaptic Package Manager click on reload, then click on "Mark All Upgrades".

Once it's marked them all, on the left side select "Custom Filters" then above that select "Marked Changes" now they will all show up in the right pane and selecting one will give you a better description of it.

You can choose to unmark some if you want and do them at another time. Unmarking one may cause the de-selection of others. Mainly you want the security updates.

The rest will still show up as needing updated but you can do them whenever you want to.

---

### Post by dgoddard1 on 2008-12-12
Thankyou 2hot6ft2
I followed your instructions to get more information on the packages, and looked into those two that were not authenticated that you identified as kernel upgrades.  on both of those I got the following description and comment.  
-------
This package contains modules supplied by Ubuntu for Linux Kerne 2.6.24 on x86/x86_64

You likely do not want to install this package directly.  Instead, install the linux-generic meta-package, which will ensure that the upgrades work correctly, and that supporting packages are also installed.
-------

That sounded like a helpful piece of advice, however I did not find anything explicitly labeled "linux-generic meta-package"  So now I am left wondering just exactly what the name of the package is that I am looking for, or how I would recognize the package in question.

I did find a package called 
Package..........linux-generic
--Installed Verision .... 2.6.24.16.18   (I had a typo in my original post)
-- Latest Version ....... 2.6.24.22.24
-- Description .......... Complete Generic Linux kernel

Would that be the update I am looking for and should install instead of the unauthenticated ones?  There was no mention of "meta-package" :confused:

---

### Post by 2hot6ft2 on 2008-12-12
If your pc is booting up and running ok with the kernel you're using now I would just skip them for now since those are usually a bit time consuming on a slow connection.

---

### Post by Partyboi2 on 2008-12-12
> Is this going to tie up my computer for hours? Because the only broad band available to me is at the public library where they have wireless available to the patrons.
When you run update manager it should tell you how many mb your updates are to download. I would say for 1049 you would have a few mb to download so will probably take a bit of time.

---

