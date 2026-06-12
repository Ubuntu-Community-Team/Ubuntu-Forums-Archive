---
title: "Compress 3gb of data?"
date: 2008-08-24
forum: General Help
---

### Post by linuxisevolution on 2008-08-24
Thanks you guys for your help.
What i need to do is take a 3gb folder and compress it to fit onto a 700mb CD. It contains mostly PDF files. Is this possible? the tar.gz format only archives it. .. 

If i right click the file in nautilus and select create archive>>zip>>create, after several minutes i get this:



zip I/O error: File too large

zip error: Output file write failure (write error on zip file)


Can someone please tell me how to compress this file to my desires? Thanks!:confused:

---

### Post by mellowd on 2008-08-24
```
tar -zcvf file.tar.gz folder/
```



the -z option compresses it

---

### Post by linuxisevolution on 2008-08-24
Thanks. I had the command wrong. Isn't this the same thing as doing it in the file browser? I'll write back to see how it goes. .. stay around! hehe

---

### Post by linuxisevolution on 2008-08-24
> **mellowd said:**
> ```
tar -zcvf file.tar.gz folder/
```



the -z option compresses it
Okay, I did that and ended up with a 3.0gb tar.gz file . ncaa.tar.gz = 3gb!!! hmm. what else can i do?

---

### Post by linuxisevolution on 2008-08-24
bump

---

### Post by bodhi.zazen on 2008-08-24
You are asking for a lot of compression.

You can split the file into 700 Mb sizes, burn each to a cd.

[http://blog.4rev.net/2007-09/linux-split-large-file/](http://blog.4rev.net/2007-09/linux-split-large-file/)

See also man split

or you can use rar

[http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html](http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html)

---

### Post by mellowd on 2008-08-25
Are you sure those files have not got compression already? -z will definately compress it if they are already not compressed

---

### Post by jespdj on 2008-08-25
There is ofcourse no way to guarantee that you can compress your 3 GB of files to 700 MB. How much the documents can be compressed depends on the contents of the documents. I don't know the details of the PDF format, but maybe those documents already use compression (internally), and if you try to compress them again you'll see that they can't be compressed any further.

Do you really need to put these on one 700 MB CD-ROM? Can you use multiple CDs, or a DVD (which can contain 4.7 GB)?

---

### Post by mellowd on 2008-08-25
Or better yet, a cheap usb stick

---

### Post by tangibleorange on 2008-08-25
you could try using bzip2 compression. i think it compresses more but takes much longer:

```
tar -jcf files.tar.bz2 folder/
```

but all the points above are very valid, so I doubt that will help much..

---

