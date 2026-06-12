---
title: "Use external HD with preformatted NTFS or reformat to other format?"
date: 2018-06-09
forum: Hardware
---

### Post by jimmiejohnsson84 on 2018-06-09
Hi All,

I got a western elements usb external HD. It comes pre-formated with a NTFS partition, which seems to work out of the box in Ubuntu (I was a bit surprised).
The question is - does it make sense to reformat it to something else anyway? Would it be faster to write/read from it if it has another format or it dose'nt matter?
If anyone could shed some light on the subject that would be great.
Im running ubuntu 16.04

/Jimmie

---

### Post by Autodave on 2018-06-09
Leaving it as NTFS allows you to move it to a Windows computer to copy or paste files to.  As far as speed, you are talking small increments by formatting it to something else. I leave all of my externals to NTFS since I can readily use them on anything.

---

### Post by oldfred on 2018-06-09
Large copies may be a bit slower, but if you want or need compatibility like Autodave leave as NTFS.
But be sure to have a Windows repair disk, so you can run chkdsk or make other repairs to the NTFS. 
Abnormal shutdown will cause issues and chkdsk will be required. And users often forget to unmount (even with Windows) and that can cause file corruption and then you need Windows repair tools.

---

