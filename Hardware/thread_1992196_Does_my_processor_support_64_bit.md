---
title: "Does my processor support 64 bit?"
date: 2012-05-31
forum: Hardware
---

### Post by soumoks on 2012-05-31
Hey guys a little help here,i have a intel core i3-540 processor on a intel motherboard,i am currently running a dual boot of windows 7 ultimate and ubuntu 12.04,both 32-bit versions,my question is, Does my processor support 64 bit os?
i would like to install 64 bit versions of both windows as well as ubuntu,ur help would be much appreciated,thanks in advance..

---

### Post by gnusci on 2012-05-31
[http://ark.intel.com/products/46473/Intel-Core-i3-540-Processor-%284M-Cache-3_06-GHz%29](http://ark.intel.com/products/46473/Intel-Core-i3-540-Processor-%284M-Cache-3_06-GHz%29)

EDIT: You can try the LiveCD amd64

---

### Post by Megaptera on 2012-05-31
If you are running Linux or have access to Live Linux media, open the terminal prompt and run:

grep --color=always -iw lm /proc/cpuinfo

If this command returns lm (**L**ong **M**ode) as one of the flags, then your processor is capable of 64-bit. 

From: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

Hope that helps?

---

### Post by Sivella on 2012-05-31
Hello,

Google said you intel core i3-540 is a 64bits processor. ;)
So you can run 64bits OS (W$ and Ubuntu) as well.

---

### Post by Dngrsone on 2012-05-31
The i3/i5/i7 series microprocessors are 64-bit; so yes, you can run both Win 7 (64-bit) as well as Ubuntu 12.04-desktop-amd64

---

### Post by soumoks on 2012-05-31
> **gnusci said:**
> [http://ark.intel.com/products/46473/Intel-Core-i3-540-Processor-%284M-Cache-3_06-GHz%29](http://ark.intel.com/products/46473/Intel-Core-i3-540-Processor-%284M-Cache-3_06-GHz%29)

EDIT: You can try the LiveCD amd64

trying out the live cd is the best option in this case i think..but why does it say amd 64(i checked out the ubuntu site as well),does it provide full support on my intel processor?

---

### Post by soumoks on 2012-05-31
> **Dngrsone said:**
> The i3/i5/i7 series microprocessors are 64-bit; so yes, you can run both Win 7 (64-bit) as well as Ubuntu 12.04-desktop-amd64

thank u for such a quick reply..but why does the ubuntu disc say amd 64 bit?does it provide full support for my intel processor?

---

### Post by Dngrsone on 2012-05-31
> **soumoks said:**
> thank u for such a quick reply..but why does the ubuntu disc say amd 64 bit?does it provide full support for my intel processor?

Good question.  I'm sure there is a good answer.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

I did research and ask the question, myself; since I have a dual-core Intel machine myself-- the end-result is that amd64 works perfectly fine on Intel 64-bit processors.  I will continue to look for an answer to that pressing question, though.

[edit]Okay, [this page](https://help.ubuntu.com/community/32bit_and_64bit) seems to imply that it's just plain easier to spell AMD64 over the Intel name for 64-bit implementation.

It could be just that the AMD implementation was first and, rather than make a new name for every processor supported, they just stuck with that one.

---

### Post by soumoks on 2012-05-31
> **Dngrsone said:**
> Good question.  I'm sure there is a good answer.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

I did research and ask the question, myself; since I have a dual-core Intel machine myself-- the end-result is that amd64 works perfectly fine on Intel 64-bit processors.  I will continue to look for an answer to that pressing question, though.

[edit]Okay, [this page](https://help.ubuntu.com/community/32bit_and_64bit) seems to imply that it's just plain easier to spell AMD64 over the Intel name for 64-bit implementation.

It could be just that the AMD implementation was first and, rather than make a new name for every processor supported, they just stuck with that one.
Thanks a lot for clearing my doubt,they could have just named it ubuntu 12.04 64-bit(without the AMD written next to it ;)),it would have avoided a lot of confusion,but thats ok as long it works as its supposed to,gonna switch to 64 bit as soon as the download finishes :)

---

### Post by ahallubuntu on 2012-05-31
"AMD64" is just the name of a standard for 64 bit software.  AMD as a company chose to introduce 64 bit architecture into its processors before Intel some years ago, and Intel was forced to follow suit to stay competitive, even though at that time there was little real benefit to 64 bit processing for most consumers.  Intel calls theirs "EMT64" but the open source industry credits AMD with introducing it and thus they have the name of the standard.  Intel's CPUs run AMD64 versions of Ubuntu just fine.

The biggest benefit by far for the average user of 64 bit OS is the ability to use more RAM.  A 64 bit OS can address more than 4GB of RAM; a 32 bit OS can address only 4GB but in reality slightly less due to some housekeeping issues in some cases.  Even if you have only 4GB of RAM you might get a slight benefit of a 64 bit OS (ability to use a tiny bit more RAM).  If you have only say 2GB of RAM there's really no benefit at all to using a 64 bit OS - in fact you may see a slight performance reduction because there is slightly more overhead to 64 bit software than to 32 bit software.  If you have 8GB of RAM you HAVE to use a 64 bit OS to use it, though.

Most CPUs from both Intel and AMD have been 64 bit compatible for years.  Intel introduced 64 bit architecture into its CPUs with the "Prescott" version of the Pentium 4 back in 2004.  Since then, all of the Core 2 Duo CPUs have been 64 bit and certainly all of the i3/i5/i7 CPUs.

---

### Post by soumoks on 2012-05-31
ok guys now since i got to know,my processor supports 64 bit,i have one more question,is 2gigs of ram enough for ubuntu 12.04 64 bit?

---

### Post by ahallubuntu on 2012-05-31
2GB of RAM is "enough" but there would be no benefit for you to installing a 64 bit Ubuntu with only 2GB of RAM.  You would probably be better off with the 32 bit Ubuntu because certain processes and files will be smaller and you might get a slight performance benefit.

Some people think a 64 bit operating system must be twice as fast as 32 bit operating system, but it doesn't work that way.

---

### Post by soumoks on 2012-06-01
> **ahallubuntu said:**
> 2GB of RAM is "enough" but there would be no benefit for you to installing a 64 bit Ubuntu with only 2GB of RAM.  You would probably be better off with the 32 bit Ubuntu because certain processes and files will be smaller and you might get a slight performance benefit.

Some people think a 64 bit operating system must be twice as fast as 32 bit operating system, but it doesn't work that way.

ya that's what i thought,goin to make the switch to 64 bit as soon as i get 2 more gigs of ram..:)

---

### Post by soumoks on 2012-06-01
Hey guys ,just one more question,i know ubuntu uses a lot less RAM than windows 7,so am eager to try out the 64 bit version of ubuntu 12.04 with the unity interface on my system,am goin to upgrade my RAM as soon as possible,but there would be no issues runnin the 64 bit on my 2 gig pc right?

---

