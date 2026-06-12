---
title: "How to Remove Hundreds of Random Icons on KDE4 Desktop?"
date: 2008-08-04
forum: General Help
---

### Post by bunnyfly on 2008-08-04
Hello. I have been upgrading Kubuntu's KDE4 as it's been coming out. However, I hadn't logged into KDE for awhile, but tried it again now that 4.1 is out. Everything seems to work except my desktop is absolutely covered in random icons! (maybe 100+ or so?) This is sort of a reversal to the common "how do I get icons on my KDE4 desktop" because I want them OFF!

They're not there in Gnome. Some of the filenames I recognize as things I had downloaded up to a year ago but deleted...it would appear as though KDE has chosen a trash, cache, or temp folder to display as my desktop folder...I completely emptied my Gnome trash, but no effect. Right clicking and looking at their properties shows that they're located on the desktop, but a quick look in Dolphin shows there's nothing there! (And yes, I've turned on display hidden files)

I looked in the widget add/remove dialog, but the folderview and icon widgets aren't saying they're in use or offering me to remove them. I would just delete each icon individually, but want to see if there is a way to fix this at a lower level to avoid future problems or lost files.

I have the latest Hardy Gnome and KDE4.1 version from the (k)Ubuntu repos. I have nothing, not even libraries for KDE3. Thanks SO much!!
[bunnyfly]

---

### Post by knutschr on 2008-08-04
When you in your file browser look in Desktop folder: are they there?

---

### Post by bunnyfly on 2008-08-04
> **bunnyfly said:**
> but a quick look in Dolphin shows there's nothing there! (And yes, I've turned on display hidden files)

Thanks for the reply : )

---

### Post by bunnyfly on 2008-08-05
Anybody?

---

### Post by aciel on 2008-10-31
Bump! Same problem here. I can remove them one at a time if I go to konsole and touch filename then rm filename (does not work if I do touch filename && rm filename). But I'd rather not. I could write a Perl script if I could figure out where KDE stores all the Desktop filenames that no longer exist...but then again, if I knew where KDE stored that info, I could just delete it. Argh.

---

