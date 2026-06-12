---
title: "Linux Compatibility of Sony SR Series vs. MacBook Pro"
date: 2009-12-27
forum: Hardware
---

### Post by Magnesium on 2009-12-27
Hi folks,

I'm looking at buying a new laptop soon, and I've narrowed the field down to 2 laptops: the Apple MacBook Pro 13" and Sony SR590. Here's the specs:

**MacBook Pro** (full specs at [http://tinyurl.com/mexhhm](http://tinyurl.com/mexhhm))

[LIST]
[*]Intel Core 2 Duo
[*]250 GB SATA HDD
[*]NVIDIA GeForce 9400M
[/LIST]

**Sony SR590** (full specs at [http://tinyurl.com/yhptvhz](http://tinyurl.com/yhptvhz))

[LIST]
[*]Intel Core 2 Duo
[*]320 GB SATA HDD
[*]ATI Mobility Radeon HD 4570
[*]Intel High Definition Audio
[*]Intel WiFi
[/LIST]

On the Ubuntu Community Help pages the Mactel Team has provided wonderful how-to's for the MBP, and it looks like everything basically works perfectly. Anybody with a MBP and Ubuntu have that experience?

The Sony SR has probably the same or more for the money, but that ATI graphics card scares me a little. Anyone have a Sony SR series laptop here? How Linux friendly is it?

And if anyone has any comments on a hardware comparison of these two laptops, I'd love to hear that as well. Thanks everyone. :)

Mg

---

### Post by Magnesium on 2009-12-28
Bump...

Anyone here with at Sony SR series laptop?

Mg

---

### Post by Magnesium on 2009-12-28
Bumpity bump...:redface:

---

### Post by Magnesium on 2009-12-29
One more bump before I buy the MBP...... :-\"

---

### Post by t_tovenaar on 2010-01-03
> **Magnesium said:**
> One more bump before I buy the MBP...... :-\"

Go for the MBP is works like a charm :)

---

### Post by Magnesium on 2010-01-03
> **t_tovenaar said:**
> Go for the MBP is works like a charm :)
 
Thanks t_tovenaar, I think that's what I'm going to do. I am assuming you have a MBP with Ubuntu? How is the battery life in Linux?

---

### Post by mkoehler on 2010-01-04
I second the vote for the MBP.

I have no experience with the Sony SR Series laptop, but I do have a MBP that I run xubuntu on with virtualbox.  I have yet to run into any real issues, and nothing to do with compatibility issues.  Sure you get a little more bang for your buck with a non-apple branded computer, but as far as I'm concerned, the construction and quality of apple's products is unsurpassed.  FYI, I do most of my work that could potentially break things on a separate laptop though (I also have a Dell Latitude D820 that's in good shape after 3.5 years or so).

Go for the MBP, you won't be disappointed.

---

### Post by Magnesium on 2010-01-04
> **mkoehler said:**
> I second the vote for the MBP.
 
I have no experience with the Sony SR Series laptop, but I do have a MBP that I run xubuntu on with virtualbox.  I have yet to run into any real issues, and nothing to do with compatibility issues.  Sure you get a little more bang for your buck with a non-apple branded computer, but as far as I'm concerned, the construction and quality of apple's products is unsurpassed.  FYI, I do most of my work that could potentially break things on a separate laptop though (I also have a Dell Latitude D820 that's in good shape after 3.5 years or so).
 
Go for the MBP, you won't be disappointed.
 

Thanks mkoehler, everyone I've talked to about the MBP has said the same thing, that Apple's build quality is super...I am going to go with it. You said you run Xubuntu in VirtualBox...is that on a Linux host, or in OS X?

---

### Post by mkoehler on 2010-01-04
It's on OS X.  It works perfectly well for basically all purposes.

---

### Post by Magnesium on 2010-01-04
> **mkoehler said:**
> It's on OS X.  It works perfectly well for basically all purposes.

Alrighty, well I was planning on installing Linux as my primary OS, so I can get better performance, hardware accelerated graphics (Compiz), etc., etc....but it is good to know that the performance of VirtualBox is good. The processor in the new MBPs doesn't have Virtualization Technology, according to Intel...but if you look at the flags the processor reports, VT is there! So there has been some confusion in that regard. When you are running Xubuntu, is your CPU usage extremely high? (Like, 30-40% at idle.) Also, mkoehler, could you run (in an OS X terminal) these commands? Thanks a lot :)

```
sysctl machdep.cpu.features
```
```
sysctl machdep.cpu.brand_string
```

Mg

---

