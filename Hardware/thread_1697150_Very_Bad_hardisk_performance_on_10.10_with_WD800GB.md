---
title: "Very Bad hardisk performance on 10.10 with WD800GB AARS"
date: 2011-02-28
forum: Hardware
---

### Post by imblack on 2011-02-28
Please take a look at picture below, these are my harddisk specs:

[[IMG]http://img840.imageshack.us/img840/2130/screenshotwc.png[/IMG]](http://img840.imageshack.us/i/screenshotwc.png/)

The problem Is I just installed ubuntu on it and I am experiencing very laggy and slow reads from Hardisk. I also have another 160GB WDC disk and ubuntu runs perfect on this, however that one is like 2 years old and this one brand new, I can't figure it out.

Please help me, any one with similar hard disk?

---

### Post by fjgaude on 2011-02-28
Try seeing what the SMART of Disk Utility has to say about the bad sectors of the drive. You may have a bad one, especially if it is having to move bad sectors out of the way, constantly.

---

### Post by imblack on 2011-02-28
I have viewed SMART data, there are few bad sectors and The thing is I have installed Windows 7 alongside ubuntu on same disk and it's working fine. 

Or is it that window is also running slow but I am assuming that its normal? :O

---

### Post by fjgaude on 2011-02-28
Slow, fast, such relative terms... without have a standard there's no way to say what you are experiencing. <smile>

---

### Post by imblack on 2011-02-28
Lol I can't disagree with you :D

Well tell me if this helps:

When I compare Ubuntu on my 160GB in terms of speed, with one on 800GB its twice as fast. It starts fast it fires apps fast. 

While on 800GB Win7 runs perfectly fine, as I have seen it run on all other computers with same specs.

Now all I want to know that is there a common problem with my specific harddisk when ubuntu is used?

Also I forgot to mention, there is a jumper on it which converts the sector size to standard, or Large, the upcoming fashion. I couldn't use it when it was set to large setting, the performance was literally horrible!! I guess maybe due to drivers not implemented or missing support back 7months ago.

So its on the small setting.

Thanks,

---

### Post by fjgaude on 2011-02-28
Gosh, I'm not sure what to suggest next. In your BIOS you have the option to have the drives running as IDE or something else, the one that permits NCQ features. Try changing to whatever you are not presently on.

---

### Post by imblack on 2011-03-01
Okay I will give it a try and tell you, thank you very much mate :)

---

### Post by imblack on 2011-03-05
I have been through bios and cant find any such option, my bios is simple. Its Intel's board, DG31PR

I just wish some one with same hard-disk comes here :(

---

### Post by fjgaude on 2011-03-05
Try running this command and see what you get:

```
sudo hdparm -tT /dev/sda
```

Change the drive name to what they are; test both.

---

### Post by imblack on 2011-03-08
Here you are my friend:

```
/dev/sda:
 Timing cached reads:   2102 MB in  2.00 seconds = 1050.43 MB/sec
 Timing buffered disk reads:  108 MB in  7.12 seconds =  15.16 MB/sec

```

---

### Post by fjgaude on 2011-03-08
The cached reads indicate your CPU and memory are slow. What computer do you have, what is it called?

The buffered drive reads are very slow, for sure. Without knowing more of your setup I don't know what to suggest.

---

### Post by imblack on 2011-03-09
LoL I dont have slow computer, its Core 2 Duo 2.8 Ghz, 2GB RAM, Intel DG31PR Board.

The problem is my 160GB WD performs very well, here is the output for same command for 160GB Disk:

```
/dev/sda:
 Timing cached reads:   3016 MB in  2.00 seconds = 1507.59 MB/sec
 Timing buffered disk reads:  214 MB in  3.01 seconds =  71.18 MB/sec
```


But the Same Ubuntu on 800GB WD performs slow as you have seen, although Win7 is installed on the same drive but it works quite well, faster than Ubuntu. Now can you Believe that? :P

Tell me whatever more info you need and I'll be very happy to provide it :)

---

