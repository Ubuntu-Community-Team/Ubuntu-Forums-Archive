---
title: "[SOLVED] Firefox won't save bookmarks"
date: 2008-07-19
forum: General Help
---

### Post by almahtar on 2008-07-19
Hey - I just installed Hardy on my new Macbook Pro.  Firefox won't save bookmarks - I can add as many as I want, but the moment I restart Firefox I've got blank bookmarks again.

I double checked and bookmarks.xml in my .mozilla directory is not write-protected - not sure what the problem is.

Anyone know why FF wouldn't save my bookmarks? I haven't been fiddling in .mozilla, but I did install a few ubuntu extensions from the add-ons section.

---

### Post by almahtar on 2008-07-19
I figured it out - I went to about:config and sorted by status, and looked at any values that were "user set" that had bookmarks in their name.

One of them somehow got tripped, likely while installing extensions.  Changing them to default value and restarting firefox fixed the problem.

---

### Post by CosimoDeMedici on 2009-03-09
OMG!  Thank you so much for posting this!  FF not saving bookmarks was driving me wacko, and I tried all the other suggestions Google could find to no avail (re-create profile, places file, export then import bookmarks), but this was the solution!

Other travelers:  note that this worked, 03-09-09. The solution was:  type about:config in url bar, then right click on any "user set" file with bookmark in name, then click on reset to get it back to default.

---

### Post by renames on 2009-04-02
Thank you again. Worked for me 2/04/2009. Cheers.

---

### Post by nava2 on 2009-05-30
Worked 30/05/09

Thanks a lot, really. :)

---

### Post by kissthesky on 2009-10-29
Worked 10-28-09, thanks!

---

