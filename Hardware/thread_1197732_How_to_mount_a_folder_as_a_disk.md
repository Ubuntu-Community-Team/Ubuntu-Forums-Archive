---
title: "How to mount a folder as a disk?"
date: 2009-06-26
forum: Hardware
---

### Post by dsavi on 2009-06-26
Long story short, I'm looking for the Linux equivalent of this:
[http://lifehacker.com/262214/mount-any-folder-as-a-hard-drive-with-visual-subst](http://lifehacker.com/262214/mount-any-folder-as-a-hard-drive-with-visual-subst)
> Windows only: Freeware application Visual Subst lets you mount any file on your hard drive as a virtual hard drive.

That means that you've got quick access to your most oft-used folders—no matter where they're located—through a simple virtual drive.
Or, alternatively, if there is a read/write version of something like Squashfs (Which can be mounted) that would work too.

Thank you.

---

### Post by kidders on 2009-06-27
Hi there,

Linux has no concept of a "drive", so you won't find what you're looking for, I'm afraid.

What are you trying to achieve?

---

### Post by philcamlin on 2009-06-27
i dont think you can :(

---

### Post by garikaib on 2009-06-27
You can always bookmark the folder.

---

### Post by jward3010 on 2009-06-27
Yes, exactly what is it you're trying to do, how would mounting a "file" be of benefit, mounting a folder I can understand but a file - is it an empty file?

Odd thing about that program is that within Windows you can do that kind of stuff anyway, it's a little hidden and I can't exactly remember where I saw it before (somewhere possibly in disk management or some exe in system32) but it's possible without that program.

Like people are saying above you don't don't mount things to drives in Linux full stop, no such thing as drive letters, you mount them to folders and as far as I know mounting files is completely possible, but I think they then become filesystems and hence some weird **** thats strange applies and..eh... I can't really remember. The mount command would connect a teapot to your system if you wanted it to, it's one of the most complexicated commands in Linux.

---

