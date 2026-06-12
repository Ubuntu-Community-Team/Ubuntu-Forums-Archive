---
title: "Unfortunate loss of data after fsck"
date: 2008-07-15
forum: General Help
---

### Post by tomredant on 2008-07-15
Hi all,

since a couple of days my computer asked me to run an administration shell at boot and suggested me to run fsck on my hda1 without option -p or -a. I ran fsck with the -y option (yes to all questions). Everything worked fine till today:

My Virtualized Windows Vmware installation is missing one crucial file: Windows XP-s001.vmdk. I am pretty sure the fsck screwed this up. Since I am working at some important project in my virtualized windows I am about to do everything to get my data back.

Is there any way to undo the fsck command, or a way to restore this missing file?

thanks

Tom

---

### Post by RealPSL on 2008-07-16
Have you tried examining the lost+found directory for that file system to see if it was placed there. If it is there you might be able to recover it.

[http://www.itworld.com/rescue-lost-found-files-nlsunix-080508]("http://www.itworld.com/rescue-lost-found-files-nlsunix-080508")

---

