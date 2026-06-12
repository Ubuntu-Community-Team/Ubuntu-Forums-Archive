---
title: "DVDROM mounting"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by vaskark on 2005-03-29
I am currently dualbooting WinXP and Hoary and have hit a snag regarding my dvd drive. I'll start by saying I have 2 CD drives: a) CDROM/DVDROM and b) CD-RW. When I insert a dvd into my dvd drive the appropriate icon appears on my desktop, called DVD-ROM Disc. Yet it opens to a Nautilus burner window -- i.e. I can't play it in Totem-xine. I then ran a command I found in the Ubuntu Starter Guide:

$ sudo mount /media/cdrom/ -o unhide

Now an icon called **DVD-ROM Disc (2)** appears on my desktop, which Totem recognizes as a dvd and plays it fine. At least I got dvd's to work!

I guess I need to know why this is happening and how I can remedy the situation. In my /media folder there are 3 entries:

cdrom -> /media/cdrom0
cdrom0
cdrom1

Not sure what else I can add to explain the situation. Can someone offer assistance? I'm so close to getting hoary set up perfectly.

Thanks.

---

### Post by jdong on 2005-03-29
So somehow, all your media is being recognized as blank, when indeed they are not. Does this happen with many different CD's/DVD's?

---

### Post by vaskark on 2005-03-29
[QUOTE=jdong]So somehow, all your media is being recognized as blank, when indeed they are not. Does this happen with many different CD's/DVD's?[/QUOTE]

I placed a data cd into my CD/DVD combo drive, and it immediately mounted fine and was identified as */media/cdrom0*. So data cd's are fine.

I placed a music cd into my CD/DVD combo drive and likewise it mounted fine. So my cd/dvd drive is mounted at */media/cdrom0*.

I placed a cd-rw into my CD-RW drive and it mounted fine, at */media/cdrom1*. So my CD-RW drive is */media/cdrom1*.

So the problem only has to do with dvd's.

I tried linking /dev/dvd to /media/cdrom0 with:

 ```
$ sudo ln -s /dev/dvd /media/cdrom0
``` 

but it resulted in:

 ```
lrwxrwxrwx  1 root root 3 2005-03-29 18:26 /dev/dvd -> hdd
```

So CD/DVD drive is hdd, and CD-RW drive is hdc. Is this correct?

After all this, I still have the same problem. Inserting a dvd gets it placed on my desktop, but that's it. I did notice that double-clicking the dvd icon produced a nautilus window titled 'CD/DVD Creator'. So it thinks it's a blank cd. Argh!

Any ideas??
](*,)

---

### Post by XDevHald on 2005-10-19
Did we ever get this resolved? 

Please reply back

---

### Post by valheru on 2005-11-12
I am curious as well. I see TONS of posts of similar issues. You would think that when people find an answer they would post the solution.....

---

### Post by gentooruwest on 2006-01-06
OK ... we should seriously get some feedback on this issue.  Cause now I have the problem, and there are like 8 threads on this, and NOOOO answers.  It was suggested in one of the threads that this may be because of certain types of dvd hardware.  I have a plextor, if this helps anyone else.

---

### Post by jedilord on 2006-02-02
Okay guys...I am having the same problem. I have a Plexotr PX-716A and tried reading my Quake 4 DVD. It makes the icon on the desktop but nothing inside and the sys. recognizes it as blank media. CD,CDR,CDRW, and DVD-R, DVD-RW all works...oddly enough. I don't have DVD+ media so I couldn't test. So...now I'm even more puzzled as to why my burnt DVD-R/W media reads yet pressed DVD (Quake 4) doesn't.  I don't want to get up and find other pressed DVDs because I'm lazy. Anyways, your attention to this would be appreciated. BTW...I'm starting to like linux more and more...just figured out apt-get ...hot stuff. The dude that made the Nvidia how to, good job dude...rock on.

---

### Post by jedilord on 2006-02-02
Okay that's retarded. After testing out other media which all worked, I put the Quake 4 DVD back in and it read....wtf? Let me know if you need some dumps of specs...go to work guys! hehe

---

### Post by gentooruwest on 2006-02-02
So, jedi dude ... you say you just put the pressed dvd back in and it worked?  What if you stick in a dvd movie? ... does it think it's blank media?

---

