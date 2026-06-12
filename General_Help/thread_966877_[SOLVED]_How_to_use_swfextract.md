---
title: "[SOLVED] How to use swfextract?"
date: 2008-11-01
forum: General Help
---

### Post by crazyfuturamanoob on 2008-11-01
I got an swf file containing a nice soundtrack I'd like to get.

For extracting the soundtrack, I tried swfextract, from swftools.

Ran the command **swfextract file.swf -m** but I get no output.
Can't find anywhere any audio files. Maybe somebody knows how to do it?

Thanks.

Edit: That swf file turned out to be invalid.

---

### Post by Phantoome on 2009-10-31
Let's rack up an old thread. 
I almost have the same question,
How to axtract a file?
i use this as a code:
```
swfextract -i ~/file.swf
```
And this is my result:
```
You must supply a filename
```

Can somebody explain what i'm doing wrong? been using Ubuntu for a week now

---

### Post by cabetza1 on 2010-02-16
From [http://www.swftools.org/faq.html:](http://www.swftools.org/faq.html:)
 First list all extractable items:

swfextract myfile.swf

The result is something like:

Objects in file myfile.swf:
[-i] 3 Shapes: ID(s) 1-3
[-i] 5 MovieClips: ID(s) 4, 5, 8, 10, 12
[-j] 3 JPEGs: ID(s) 69, 116, 447
[-p] 1 PNG: ID(s) 318
[-s] 3 Sounds: ID(s) 28-30
[-f] 10 Frames: ID(s) 0-10

Now you can extract a shape using

swfextract -i 2 myfile.swf -o shape.swf

a sound using

swfextract -s 28 myfile.swf -o sound.wav

a PNG image file using

swfextract -p 318 myfile.swf -o file.png

etc.

---

