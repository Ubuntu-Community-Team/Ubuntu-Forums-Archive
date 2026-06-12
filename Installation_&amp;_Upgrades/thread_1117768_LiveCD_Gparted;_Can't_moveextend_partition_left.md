---
title: "LiveCD Gparted; Can't move/extend partition left"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by yc2 on 2009-04-06
Running Gparted from a LiveCD, I wish to use the unpartitioned area between hda5 and hda6. I wish to include it into hda6.

However this does not seem possible.

I cannot move hda6 to the left and I cannot resize hda6 to include the unpartitioned area.

It only seems I can extend partitions to the right ?

---

### Post by Pasdar on 2009-04-06
How about you backup your data and delete the partition hda6 and then make a new larger one (together with the unpartitioned space)? What do you have on hda6?

---

### Post by Mark Phelps on 2009-04-06
Can't tell from the screenshot how much unallocated space you have, but if it's not much, and you have Round to Cylinder Boundary checked in GParted, it won't resize it.  I know that it DOES allow you to resize to the left because I've done that.

Don't know what version of GParted you're using, but if it's not 4.4, you should download and burn the image from distrowatch.com and use that.

---

### Post by bernardfrancois on 2009-04-06
I just had the same problem, and found the answer in the following thread:
[http://ubuntuforums.org/showthread.php?t=346615](http://ubuntuforums.org/showthread.php?t=346615)

I'm running the 7.04 live cd, so I first changed my /etc/apt/sources.list according to the info on the following page:
[https://help.ubuntu.com/community/EOLUpgrades#7.04%20to%207.10](https://help.ubuntu.com/community/EOLUpgrades#7.04%20to%207.10)

After that, I just upgraded gparted using synaptic.
Then I could finally extend my partition to the left (I also had some unallocated space to the left of the partition I wanted to extend).

FYI: I had to extend my /boot partition because upgrading my 7.10 installation to 8.04 failed because this partition was a few megabytes too small.

---

### Post by yc2 on 2009-04-06
Thanks everyone, especially BernardFrancois for the explanation. I downloaded the latest Ubuntu LiveCD and Gparted works now. (I was not very smart previously and used an older version.)

EDIT: Should I mark this as "solved" now? Sorry for my ignorance, I can't find that link.

---

### Post by bernardfrancois on 2009-04-13
I searched for it, and apparently marking a thread as solved is no longer possible:
[http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

However, you can add a tag 'solved' (use the tag editor at the bottom of the page, or theck the info from the link if you can't find it).

[edit] I noticed I could do it myself, so I just did [/edit]

---

