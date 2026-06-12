---
title: "Canon pixma mp250"
date: 2009-12-18
forum: Hardware
---

### Post by jzmati on 2009-12-18
I have a canon printer all in one ( printer & scanner ) , it's : CANON PIXMA MP250 and I don't know how to make it work on my kubuntu amd64 9.10 , I have checked [http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP250%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP250%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&)
but it does NOT work because it's for 32 bit (i386) , any solution???

---

### Post by jzmati on 2009-12-19
Is it possible to change that i386 packages to amd64 ??
Or what should I do ??

---

### Post by Menthu_Rae on 2009-12-19
> **jzmati said:**
> Is it possible to change that i386 packages to amd64 ??
Or what should I do ??

You may have to do something **similar** to what I've done here for my MX700:

[http://ubuntuforums.org/showthread.php?t=1273363](http://ubuntuforums.org/showthread.php?t=1273363)

Note that this is pretty overwhelming for someone who is new to Ubuntu or computers in general (editing files from archives, repackaging them, etc).

---

### Post by jzmati on 2009-12-19
> **Menthu_Rae said:**
> You may have to do something **similar** to what I've done here for my MX700:

[http://ubuntuforums.org/showthread.php?t=1273363](http://ubuntuforums.org/showthread.php?t=1273363)

Note that this is pretty overwhelming for someone who is new to Ubuntu or computers in general (editing files from archives, repackaging them, etc).

Is there an easier solution?? it seems hard and for i386

---

### Post by Menthu_Rae on 2009-12-19
> **jzmati said:**
> Is there an easier solution?? it seems hard and for i386

Unless **Canon** fix their drivers, then no, there's no "easier" solution. We could post the fixed .deb files up - but it may technically be breaking Canon's licensing terms/copyright. So the best bet is to modify them yourself.

Also - the fix is not just for "i386" - I wrote the thread and take note that I said I did it **"under Ubuntu 9.04 and 9.10 Alpha 6 (both 64-bit/AMD64)".**

Sorry to be the bearer of bad news - you shouldn't let it put you off Ubuntu - you should use it as a point to push manufacturers (such as Canon) to better support their products, which you paid good money for.

---

### Post by jzmati on 2009-12-19
> **Menthu_Rae said:**
> Unless **Canon** fix their drivers, then no, there's no "easier" solution. We could post the fixed .deb files up - but it may technically be breaking Canon's licensing terms/copyright. So the best bet is to modify them yourself.

Also - the fix is not just for "i386" - I wrote the thread and take note that I said I did it **"under Ubuntu 9.04 and 9.10 Alpha 6 (both 64-bit/AMD64)".**

Sorry to be the bearer of bad news - you shouldn't let it put you off Ubuntu - you should use it as a point to push manufacturers (such as Canon) to better support their products, which you paid good money for.


I'm having a problem with your solution , it's NOT working with me...

---

### Post by Menthu_Rae on 2009-12-19
> **jzmati said:**
> I'm having a problem with your solution , it's NOT working with me...

That's because it's for the MX700. I'd need to look at the .deb's for the MP250 to see what's different and what needs to be changed.

**BTW** this thread here may help you - it's listed as solved... although I think it's for 9.04. It may be worth contacting the thread author to see if he's upgraded to 9.10 and can give you a hand!

[http://ubuntuforums.org/showthread.php?t=1314209&highlight=canon+MP250](http://ubuntuforums.org/showthread.php?t=1314209&highlight=canon+MP250)

Good luck! :)

---

### Post by jzmati on 2009-12-21
> **Menthu_Rae said:**
> That's because it's for the MX700. I'd need to look at the .deb's for the MP250 to see what's different and what needs to be changed.

**BTW** this thread here may help you - it's listed as solved... although I think it's for 9.04. It may be worth contacting the thread author to see if he's upgraded to 9.10 and can give you a hand!

[http://ubuntuforums.org/showthread.php?t=1314209&highlight=canon+MP250](http://ubuntuforums.org/showthread.php?t=1314209&highlight=canon+MP250)

Good luck! :)


I read that post , and the problem there was solved by canon providing i386 packages , and i tried them on my amd64 and it keep saying : "WRONG ARCHIVE i386"

---

### Post by jzmati on 2009-12-24
Up...

---

### Post by jzmati on 2009-12-24
plz help. :(

---

### Post by jzmati on 2009-12-26
Is it impossible to work with my ubuntu amd64 or not??

---

### Post by spyderpride on 2009-12-26
See next post.

---

### Post by spyderpride on 2009-12-29
I think I figured it out...

First, and not sure if this is entirely relevant or not, unplug printer from the USB port and delete the improperly configured printer from System--Administration--Printing.  Just right click on it and delete it.

Install ia32-libs. Note that you need to have the box checked for the canonical partner repository in Software Sources.

```
sudo apt-get install ia32-libs
```


Install the i386 debs as such:
```

sudo dpkg --force-architecture -i cnijfilter-common_3.20-1_i386.deb
sudo dpkg --force-architecture -i cnijfilter-mp250series_3.20-1_i386.deb

```

I did this and it worked.  I hate to say this, but if it would have been a snake it would have bit us in the face.  

This gets the printing working, scanning will take more work (compiling from latest sane-backends source). [http://ubuntuforums.org/showthread.php?t=1314209&page=2](http://ubuntuforums.org/showthread.php?t=1314209&page=2)

---

### Post by Menthu_Rae on 2010-01-01
> **jzmati said:**
> plz help. :(

**[EDIT]** Didn't see the post above by spyderpride, but yes, that's what you need to do!
[COLOR="Silver"]
You can get around the "i386" issue by running:

```
sudo dpkg --force-architecture -i <packagenameshere>
```[/COLOR]

---

### Post by arpidez on 2010-01-11
hello 

i tried what you suggest without success.
sudo aptitude install ia32-libs   <-- this ok

 sudo dpkg --force-architecture -i cnijfilter-common_3.20-1_i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package cnijfilter-common.
(Reading database ... 190690 files and directories currently installed.)
Unpacking cnijfilter-common (from cnijfilter-common_3.20-1_i386.deb) ...
Setting up cnijfilter-common (3.20-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

did i forget something??

@ karmic64

Thks for your help.

---

### Post by spyderpride on 2010-01-18
> **arpidez said:**
> hello 

i tried what you suggest without success.
sudo aptitude install ia32-libs   <-- this ok

 sudo dpkg --force-architecture -i cnijfilter-common_3.20-1_i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package cnijfilter-common.
(Reading database ... 190690 files and directories currently installed.)
Unpacking cnijfilter-common (from cnijfilter-common_3.20-1_i386.deb) ...
Setting up cnijfilter-common (3.20-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

did i forget something??

@ karmic64

Thks for your help.

Nope, looks correct so far.  Now you just have to do the same thing with the cnijfilter-mp250series_3.20-1_i386.deb package, which is the actual driver. 

There is a way to edit the install script that comes in the tar archive such that it will work on a 64-bit machine.  You basically have to search (ctrl+f) through it and find the lines that have the ***dpkg*** command which install the debs and add ***--force-architecture*** to them (in the correct place).  This isn't necessarily easier or works better but... you get to use the script :).

---

### Post by cisforcookie on 2010-04-28
all of this works up until i install the cnijfilter-mp250series
-3.20-1_i386.deb 

not sure why, but it tells me that no such file or directory exists. i can see it right there on my desktop, so whats going on?

---

### Post by cisforcookie on 2010-04-28
ignore previous post, i just had to move that file around. printing is go =)

---

### Post by abu.umar on 2010-07-17
I manage to work out the printer and also the scanner. thanks for all the help. 

But does the scanner really sounds that loud? Is it because of the 64 bit? I used the '--force-architecture -i' command
I'm afraid that it will damage my mp250..is it possible?

thanks in advance :D

---

### Post by BoomZLolicon on 2010-08-22
[SIZE=3]Thank you very much.

I've same problem! and now solved >//<
[/SIZE]

---

### Post by nechus on 2010-10-18
I'm in heaven!! I plugged the printer and got the message "Printer added!".

---

