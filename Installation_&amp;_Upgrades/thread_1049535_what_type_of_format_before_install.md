---
title: "what type of format before install"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by jlillywh on 2009-01-24
I just formatted my hard drive for preparation to install Ubuntu. I used GParted and formatted to linix-something. Ubuntu does not seem to install properly now. What is the format I should use? FAT, or something else?

Thanks!

---

### Post by taurus on 2009-01-24
Did you tell the installer to use the whole disk or did you partition the harddrive yourself and used the Manual option?  The filesystem for Ubuntu should be ext3, NOT fat32/vfat nor ntfs.

---

### Post by Copitox on 2009-01-24
Does ubuntu work in ReiserFS too?

---

### Post by taurus on 2009-01-24
Yes.  However, ext3 is the default filesystem.

---

### Post by jlillywh on 2009-01-24
well I tried using just the Ubuntu 8.10 ISO installer but part way into the install it just hangs up with the Ubuntu background wallpaper and nothing else. The CD stops and it just sits there. That is why I thought I should try formatting the hard drive as a separate process. So I used GParted and set up the whole drive with ext3 filesystem. I tried installing the Ubuntu again and it got hung up again and will not proceed.

I did a check on the CD and it appears to not have any errors. Ideas?

---

### Post by taurus on 2009-01-24
What's the spec of your machine?

You can always use the alternate CD to install Ubuntu on your machine.  Even though it's a text based, it should be real easy to follow.

---

### Post by jlillywh on 2009-01-24
specs for my dell b130 laptop:
proc:   Intel Pentium M 1.7 GHz  
ram: 512 mb
stor: 40 gb

---

### Post by jlillywh on 2009-01-24
I will give the alternate CD a try. Thank you.

---

### Post by jlillywh on 2009-01-24
Is there an alternative CD download that is not bittorrent? I have a software install restriction on bittorrent. I cannot find a normal install of the alternate available.

---

### Post by hansdown on 2009-01-24
Hi  jlillywh.

Go here.  [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by ugm6hr on 2009-01-24
> **jlillywh said:**
> I did a check on the CD and it appears to not have any errors. Ideas?

Did you try the install option (i.e. not the "Try without making changes")?

It sounds like Ubuntu loads, but is struggling for RAM.

Potential alternative solutions:
1. Alternate CD
2. Use a smaller Linux Live CD to create a swap partition, then try again
3. Direct install in Live CD (as above)
4. Xubuntu Live CD

---

### Post by jlillywh on 2009-01-26
Thank you. The alternate install worked like a charm.

Once installed, configuration was easier than Windows XP. That was surprising! I haven't noticed any difference in performance between Windows and Ubuntu. So far, I think I would choose the free product over the expensive one! amazing...

---

