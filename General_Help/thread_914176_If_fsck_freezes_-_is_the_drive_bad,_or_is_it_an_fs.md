---
title: "If fsck freezes - is the drive bad, or is it an fsck bug?"
date: 2008-09-08
forum: General Help
---

### Post by skullmunky on 2008-09-08
This is on Kubuntu Hardy.

During the usual boot-time fsck, my home drive freezes every time, at 8%, and just sits there, all day if I let it.  I can skip the fsck, log in normally, and manually fsck the drive, which also freezes without saying anything useful or dire.  Nothing remarkable happened beforehand, like a bad shutdown or physical injury.  The drive is about a year old, 500GB western digital sata, formatted ext3.

I'm planning to yank it, dd it, and replace it, but then I found a bunch of posts related to earlier versions of fsck reporting problems with fsck itself freezing.  So, I'm wondering if this is a possibility, and if there are some other utilities for testing drive and filesystem health...?

incidentally, when I skipped the fsck, it autologged me in to an account on the questionabe drive and everything loaded up just fine, which was nice.  though that might have been all on that first 8% :)


EDIT: 

I don't know, but it's fixed, apparently by zeroing a few half-written blocks that were somehow in a very bad or at least confused state.  Many thanks to the kind folks on the smartmontools list.

---

