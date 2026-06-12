---
title: "Resizing an NTFS partition"
date: 2008-10-02
forum: General Help
---

### Post by PostersandGuitar on 2008-10-02
Is there a way to resize the unused portion of an NTFS partition without disturbing anything stored in it?

---

### Post by danking12 on 2008-10-02
Yes, but I believe it can be dangerous. You would definitely want to do a defragment of the NTFS drive before you attempt this. I haven't run Windows in a while so I don't remeber but if there are settings of the level of defragment I would choose the most aggressive to ensure it is defragged as much as possible.

---

### Post by PostersandGuitar on 2008-10-02
Thank you.

---

### Post by Herman on 2008-10-02
GParted (Gnome Partition Editor) can resize NTFS regardless of whether it has been defragmented, it has been able to do that since quite a long time now. 
For GParted you may need to run CHKDSK /R or CHKDSK /F before resizing and again afterwards. The documentation for GParted in their site recommends running CHKDSK.

The 'Alternate' CD installer with 'Partman' is the one that used to require Windows to be defragmented first. It used to refuse to do anything if the NTFS partition was too fragmented.  I'm not sure if it still behaves that way or not.

I'm not sure about other partition editors.

It won't do any harm to defrag first in any case, except for maybe taking up some of your time.

You should always make a backup of at least your most important files to some other media before doing anything with any partition editing program.

Resizing NTFS doesn't seem to be any more dangerous these days than resizing any other file system. 
I haven't been keeping track especially, but I don't remember a disproportionate number of posts about NTFS corruption here in Ubuntu Web Forums, if that's anything to go by.
There must be hundreds of people per day resizing NTFS here.
But make a backup anyway, to be sure.

---

