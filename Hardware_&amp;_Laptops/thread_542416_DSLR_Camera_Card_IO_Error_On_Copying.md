---
title: "DSLR Camera Card IO Error On Copying"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by dilizent on 2007-09-03
Whether I format my Sandisk Extreme IV 8G card with my Sigma SD14 camera or:

mkdosfs -F32 -nSAN8G -R2 -h1 /dev/sda1
dosfsck -r /dev/sda1

some files are seen by the camera but will not copy by cp or dd. There is an io error. Konqueror will list the files as having a size.

[ -f file ] && [ -s file ] && echo Yes
Yes

But io error on copy, and zero length target files result.

Then if I don't mess up with dosfsck, I can move the card back to camera and camera sees the problem files. I try rotating the file to make a write happen but that does not make the file show up.

The last file that copies alright is actually truncated, and all the succeeding files give io error on copy with cp and dd.

Any ideas?

---

### Post by dilizent on 2007-09-03
Do I need to use parted first?

---

### Post by dilizent on 2007-09-03
I think it fills to 512MB and then problems begin.

---

### Post by dilizent on 2007-09-03
Every utility now thinks it's a 512MB card but it's 8G.

---

