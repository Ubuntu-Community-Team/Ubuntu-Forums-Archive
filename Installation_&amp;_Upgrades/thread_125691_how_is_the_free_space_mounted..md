---
title: "how is the free space mounted.?"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by John.Michael.Kane on 2006-02-04
how is the free space mounted.? heres how i have mine set up.
2 gig for /
800mb for swap
40gig for home
10gig freespace how would this be mounted as usable space?

---

### Post by krusbjorn on 2006-02-04
Is the "free space" unallocated space on the hard drive? You need to make a partition before you can mount it.

---

### Post by John.Michael.Kane on 2006-02-04
ok i understand the whole format the space thing. im just wonder how do you mount the space after you format it.. i tried it once and the space was never shown anywhere.

---

### Post by krusbjorn on 2006-02-04
You mount a partition using the "mount" command. If the partition is called "hda4", enter:

"mount /dev/hda4 /where/to/mount/the/partition/" in a terminal. Change the second directory in the command to where you wanna mount it. You could for example create a directory in your home folder ("mkdir ~/mount/") and then mount the partition there.

You can also enter a line for the partition in /etc/mtab to make it automount every time the computer boots.

---

### Post by John.Michael.Kane on 2006-02-04
Thanks i will look in to trying this method..

---

