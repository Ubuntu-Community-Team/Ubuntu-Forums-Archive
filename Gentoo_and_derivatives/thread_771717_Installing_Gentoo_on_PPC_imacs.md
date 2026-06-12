---
title: "Installing Gentoo on PPC imacs"
date: 2008-04-27
forum: Gentoo and derivatives
---

### Post by shgadwa on 2008-04-27
I have a lt of older imacs as well as G3s and 6500s....the specs are nto that great, usually around 300Mhz and the memory is not too good either. I want to isntall linux and sell them. I already did it to one that had 96MB ram. I installed xubuntu 6.06 and solt it for $30.00. It was a 333mhz imac. That was a little low on memory though.

I wanted to install xubutnu 8.04 on these so that it will be current, as well as having bug fixes and a recent version of firefox. However, that does not work as I get this blank screen that most have and I seem to not be able to get around it.

So, my question is, would Gentoo work good for these computers? Secondly, how does it compare to kubuntu which I really like? Third, I tried to isntall it but the whole thing is manual install and seems very complicated. No idea AT ALL as to how to isntal it. They do have handbooks but they are long, and they expect you to print the whole thing out and to know what they do not tell you.

Also, keep in mind that one or two of these computers, I will use, the others I want it to be one that people will buy for a good price.

Thanks,

Shawn

---

### Post by regomodo on 2008-04-28
if you don't want to properly follow the lengthy guides expect a lot of problems. I thought i could skim-read the handbook. I learned the hard way.

If you try to compile things on the imacs, expect long waits. It'd be better to get the initial part (stage3,portage download, kernel) done on the imac then later use it's hard-drive as a chroot environment on a much faster computer. It'll save you a lot of waiting around.

---

### Post by shgadwa on 2008-04-28
Is the stage three install the minimum install???? How long does that take to install...how hard is it??

---

### Post by regomodo on 2008-04-28
stage3 refers to a tarball of precompiled packages necessary to have a base system. If you follow the [handbook]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml") practically word for word you should do ok.

One thing to note is that when it tells you to download the stage3 tarball, don't go to where it says. Instead go to [funtoo]("http://www.funtoo.org/linux/") for the correct package. Reason i say this is that these are much more up to date (last time i installed) which will save you a lot of time when updating the system (read as: lots of compiling just to get a base system).

If you follow the guide you'll also know what i mean by "chrooting".

Time wise, i couldn't really say. Depends on if you have a bad habit of skim-reading (i do. I'm an engineering student) which means you'll end up having to do things over-and-over again. Just don't expect to be done in an afternoon. Being a quick-learner helps too.

---

### Post by shgadwa on 2008-04-28
OK...I tried to install it, I am working on the partitions right now. EVERY TIME I try to do anything with the hard drive as to make a partition or anything like that, It says, "reguested base and length is not within an existing free partition. I did initialize the disk...or I think I did...what is the deal?

---

### Post by shgadwa on 2008-04-28
ok...I figured it out, it was because there where not hardly any blocks set to the hard drive when I initialized it....I set it to the amount of blocks it had before, which was a lot. Now, when I wrote the partitions to the disk, it says that the fourth partition is too large. I looked into it, and it made the fourth partition almost 60GB when this is only a 6GB hard drive. Not knowing how or why it did that(as it was supposed to use available space, I wrote them to the disk anyway. There was a lot of errors in installing the filesystem...it jsut said error on hda4???

I cannot mount the gentoo isntall either, I think because of this hard drive problem???

---

### Post by shgadwa on 2008-04-28
ok...I initialized it again and this time it did it correctly. Only when tryng to install teh filesystem, I still get the same errors and it says Warning, had trouble writing superdrives.

---

### Post by shgadwa on 2008-04-28
It also says when mounting it, that I msut specify the filesystem type???

Also though, do I need to isntall the file system on the swap partition and the other one which is the largest one???

Shawn

---

### Post by shgadwa on 2008-04-28
Well, I restarted it and it worked...now this is what I am ahving problems with.

tar xvjpf /mnt/cdrom/stages/stage3-<subarch>-2008.0.tar.bz2

Getting the stage three from the universal CD. I did substitute the 2008 for 2007 as I have an older C
release. It says no such file or directory....??

---

### Post by regomodo on 2008-04-28
> **shgadwa said:**
> It also says when mounting it, that I msut specify the filesystem type???

Also though, do I need to isntall the file system on the swap partition and the other one which is the largest one???

Shawn

have you formatted the partitions correctly? i.e mke2fs .....


If creating,formatting and mounting them correctly is hard now you are going to have a Whale of a time trying to install Gentoo. Sorry for being blunt. I would suggest Arch but afaik not possible on ppc

---

### Post by shgadwa on 2008-04-28
Never mind again...I was supposed to incert PPC, it worked now. I'm getting it.

---

### Post by regomodo on 2008-04-28
> **shgadwa said:**
> Well, I restarted it and it worked...now this is what I am ahving problems with.

tar xvjpf /mnt/cdrom/stages/stage3-<subarch>-2008.0.tar.bz2

Getting the stage three from the universal CD. I did substitute the 2008 for 2007 as I have an older C
release. It says no such file or directory....??

you get it from funtoo. don't bother with cd

---

### Post by shgadwa on 2008-04-28
I'll Get it.....It seems like every question I had, I figured out on my own in due time...this is all just very new to me.

---

