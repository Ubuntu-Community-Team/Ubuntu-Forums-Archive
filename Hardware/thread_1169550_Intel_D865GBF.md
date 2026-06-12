---
title: "Intel D865GBF"
date: 2009-05-25
forum: Hardware
---

### Post by Uncas on 2009-05-25
Hello,
 
I'm starting to like Ubuntu too much.  So much that it's now the default option for booting :D.
 
I have a question on my motherboard.  I have a Intel D865GBF board with 1 G RAM and a 2.4 HT processor.  The videos I can see on the web seem choppy, even if it's already streamed, as in waiting for a youtube video to download and afterwards hit play.
 
The drivers I saw on the Intel Website, don't include ubuntu.  There are drivers for RedHat, but I really think that would't work.  Any ideas?  Do I have to buy a graphic card?
 
Thanks.

---

### Post by overdrank on 2009-05-25
> **Uncas said:**
> Hello,
 
I'm starting to like Ubuntu too much.  So much that it's now the default option for booting :D.
 
I have a question on my motherboard.  I have a Intel D865GBF board with 1 G RAM and a 2.4 HT processor.  The videos I can see on the web seem choppy, even if it's already streamed, as in waiting for a youtube video to download and afterwards hit play.
 
The drivers I saw on the Intel Website, don't include ubuntu.  There are drivers for RedHat, but I really think that would't work.  Any ideas?  Do I have to buy a graphic card?
 
Thanks.

Hi and what is the graphics chipset on the motherboard? You may use the command in the terminal located under applications, accessories. ```
lspci | grep VGA
```
This will identify your graphics and you may also look to see how much memory is being shared with the graphics in bios.

---

### Post by Uncas on 2009-05-25
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

I have 256 Mb of memory taken from the 1 Gb of RAM.

Thanks for your support.

---

### Post by overdrank on 2009-05-25
> **Uncas said:**
> [[COLOR=Black]00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)[/COLOR]]("http://youporn.com/watch/298942/sex-education-the-eros-technique/?from=featured2")

I have 256 Mb of memory taken from the 1 Gb of RAM.

Thanks for your support.
[]("http://youporn.com/")

Ok if you are using Jaunty 9.04 you may look at the link in my signature. :)

---

### Post by Uncas on 2009-05-30
overdrank,

Thanks a lot on your explanation.  It works perfect.  I used the safe option, since I don't know to much linux as of yet.

There's still an issue though.  I tried the normal visual effects but it says "Desktop effects could not be enabled".  Do you have any ideas?

Thanks.

---

