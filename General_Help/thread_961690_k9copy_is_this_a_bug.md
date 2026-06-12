---
title: "k9copy: is this a bug?"
date: 2008-10-28
forum: General Help
---

### Post by megamania on 2008-10-28
When copying a DVD to an .ISO file, if I use spaces in the filename k9copy will not complete the process, without warning me that something is wrong.
This is the output I get when I run it from command line:
```

QPainterPath::arcTo: Adding arc where a parameter is NaN, results are undefined
" /bin/sh -c genisoimage -gui -graft-points -volid PULSE_DVD1 -appid k9copy -volset-size 1 -volset-seqno 1 -no-cache-inodes -udf -iso-level 1 -dvd-video -o /home/gian/Pink Floyd - Pulse 1.iso /home/gian/tmp/dvd" 
"I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Invalid node - 'Floyd'.
" 

```
As you can see, it assumes that the filename is /.../Pink, and that Floyd is a "node" (whatever that means).

What do you think? I'd say it's a bug, especially because the program thinks the copy was correctly completed, but it actually stops and leaves the work-files in /tmp/dvd.

I'm using Ubuntu Intrepid Beta with k9copy 2.02.

---

### Post by beauman on 2008-11-02
Hi! 

I tried to make an iso backup of a dvd twice with k9copy_2.0.2-0ubuntu1,
both times it did rip it to /temp, but didn't generate the iso file.

I can't remember, if I used blanks in the output file name.

I de-installed it and installed k9copy_1.2.3-0ubuntu_i386.deb.
Now it works as perfect as always used to do!

I marked it in synaptics to be a fixed version.

Greetz, beauman

[http://packages.ubuntu.com/de/hardy/kde/k9copy](http://packages.ubuntu.com/de/hardy/kde/k9copy)

---

### Post by rbmorse on 2008-11-02
If the spaces in the file name are important, and you don't need some of the...ah....special things k9copy does, you can use dd to make a sector copy of an optical disk and use spaces in the name of the resulting .iso file if you encase the output path and filename in quotes. 

dd if=/dev/cdrom of="*full path and filename*.iso"  

for example:

dd if=/dev/cdrom of="/media/hold/video/mars 3.iso" 

will make a sector by sector by sector copy of the disk in /dev/cdrom and produce the output file mars 3.iso in the directory /media/hold/video

---

### Post by megamania on 2008-11-03
> **rbmorse said:**
> If the spaces in the file name are important, and you don't need some of the...ah....special things k9copy does
I'm not worried about k9copy not working with filenames containing spaces, I'm worried about the lack of a message when the program doesn't accomplish its task.

If I had not launched it from CLI, I'd still be here banging my head on the wall wondering what was wrong with it...

---

