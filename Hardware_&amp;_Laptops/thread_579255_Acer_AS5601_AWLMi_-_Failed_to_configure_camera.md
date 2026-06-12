---
title: "Acer AS5601 AWLMi - Failed to configure camera"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by alexpds on 2007-10-18
Hey everyone.

Recently installed Gutsy on my Acer AS5601 AWLMi.
Pretty much easy stuff...

The thing is boot hangs for a while (4-6 minutes) and then proceeds successfully.
The message during the temporary hand is:

media/gspcav1/gspca_core.c "Failed to configure camera"

As,

1. I don't really make use of it;
2. and couldn't find in the forums a way to install it

I would like, for the time being, to disable it or at least make ubuntu not try to configure it thus improving my boot time.

Would appreciate any help.

Thanks

---

### Post by clotet on 2007-10-19
I have the same problem. On Ubuntu 7.04 it happened but it used to boot normally :S

Let's see if anyone can help us ;)

---

### Post by Skatchoo on 2007-10-20
Same problem here.  I have an Acer Travelmate 4230.  Any help is appreciated.

Thanks.

---

### Post by nikdc5 on 2007-10-20
I'm also having this problem with an acer aspire 5633wlmi.

---

### Post by nibbles on 2007-10-20
I have the same problem on 5602Wlmi (Gutsy).

However, it doesn't happen all the time, and I have been able to some times start up my webcam with camorama, and it works (but not always). Sometimes, the boottime is also shorter than the 4-5 minutes.

It would be really helpful to get a solution, as I use my webcam quite often.

Thanks

---

### Post by helver on 2007-10-21
I've got the same problem on an Acer Travelmate 8200.  Under feisty I didn't notice it, but I just upgraded to gutsy and it's become much more of a problem...

---

### Post by nibbles on 2007-10-21
I also came to realize that my other usb ports don't work (tried external hard disk and usb mouse).

I've found this bug by someone:

[https://answers.launchpad.net/ubuntu/+question/15074](https://answers.launchpad.net/ubuntu/+question/15074)

Other people have reported similar problems on this forum.

It would be great to have a solution for it.

Thanks

---

### Post by nibbles on 2007-10-22
bump

---

### Post by erktrek on 2007-10-22
I am experiencing the exact same issue with an Acer 5670.. 

Have not been able to find a workaround yet. Maybe a kernel param at bootup?

This started after the latest round of updates for Feisty (new kernel etc)..




E.

---

### Post by erktrek on 2007-10-22
As an aside I was able to get around the issue by blacklisting gspca..

I added this entry:

```

# Disable auto-loading of gspca module
blacklist gspca

```

to

> /etc/modprobe.d/blacklist

Hope this helps?

E.

---

### Post by nibbles on 2007-10-22
That definitely helps if you don't use the webcam, but I was quite eager to start using the webcam now it worked (well, for a coupe of times).

It would be nice to see a real solution to this problem.

Best

---

### Post by Unforsaken92 on 2008-01-27
I believe I have found a fix for the problem.  It involves editing the Kernel.  I'm a total linux newb so I think recompiling the kernel is a bit over my head.  Here is a link to the blog describing the fix. 
[http://advhertz.altervista.org/install-debian-gnulinux-on-acer-aspire-9113-wlmi/#Video3]("http://advhertz.altervista.org/install-debian-gnulinux-on-acer-aspire-9113-wlmi/#Video3") 
Hopefully someone can make use of this and post a fix or give information on how to recompile the kernel.

---

### Post by mcarni on 2008-07-22
In my case simply rotating the camera solved the problem.

have a check at this

[http://ubuntuforums.org/showpost.php?p=5290635&postcount=1026](http://ubuntuforums.org/showpost.php?p=5290635&postcount=1026)

hope it helps

M

---

