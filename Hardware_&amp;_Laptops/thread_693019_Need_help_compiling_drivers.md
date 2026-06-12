---
title: "Need help compiling drivers"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by Battie on 2008-02-10
Hello again!

I've been using Ubuntu for a while, but always switched into Windows for the art-y stuff.  But now I am trying to get my ancient Microtek ScanMaker 4800 scanner working in 7.10 and have run into a wall.

I am getting the error described in the bug report here [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/115898](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/115898)

Since I am in the scanner group and scanimage -L correctly identifies my scanner, I figure I should try to replace the drivers like this person did.  Unfortunately, I don't know how to do that.

I downloaded the drivers at [http://www.ziplabel.com/sm3840/](http://www.ziplabel.com/sm3840/), but they are only a bunch of .c and .h files, and I don't know what to do with them.  How to I properly compile them?

Also, do I need that kernel patch above?  Will anything scary happen if I try it?

Thanks for any help.  This immediate problem is annoying (but totally my fault; I know it's an older-than-dirt device), but I figure I should know how to compile these things anyway.

---

### Post by Yellow Pasque on 2008-02-11
I don't know what packages you'll need to do this. I know you'll at least need build-essential
```
sudo apt-get install build-essential
```

1. Download this to your desktop and extract it: [ftp://ftp.sane-project.org/pub/sane/old-versions/sane-backends-1.0.15/sane-backends-1.0.15.tar.gz](ftp://ftp.sane-project.org/pub/sane/old-versions/sane-backends-1.0.15/sane-backends-1.0.15.tar.gz)
2. You should now have a folder on your Desktop called sane-backends-1.0.15
3. Download the sm3840_patch2.txt file attached to this post and place it in the sane-backends-1.0.15 folder.
4. Open up a terminal and run:
```
cd ~/Desktop/sane-backends-1.0.15
mv sm3840_patch2.txt sm3840_patch2
patch -p1 sm3840_patch2
```
5. Download the sm3840_source5.tar.gz file attached to this post and place it on your Desktop. Now:
```
cd ~/Desktop
tar zvxf sm3840_source5.tar.gz
```
6. Run:
```
./configure --prefix=/usr
make clean
make
sudo make install
```

I did a test run and had no problems building on 7.10-amd64 with 2.6.24 custom vanilla kernel
Good luck. Let me know how it works.

---

### Post by Yellow Pasque on 2008-02-11
> **Battie said:**
> 
I downloaded the drivers at [http://www.ziplabel.com/sm3840/](http://www.ziplabel.com/sm3840/), but they are only a bunch of .c and .h files, and I don't know what to do with them.  How to I properly compile them?
As you see, those files are meant to replace some of the files in the sane-1.0.15 source package. There's a makefile in that package.

> Also, do I need that kernel patch above?  Will anything scary happen if I try it?
It's not a kernel patch. No, nothing scary will happen. :)

---

### Post by Battie on 2008-02-11
Thank you so much for taking the time to write those instructions!

I will try this and test the scanner again when I get home tonight.

Edit: Forgot to ask -- Do I need to remove the newer backends I already have (I think they're 1.0.19)?  I'll do it this time since it won't hurt, but it would be nice to know for future reference how finicky these things are.  Thank you again!

---

