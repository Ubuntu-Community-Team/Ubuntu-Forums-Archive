---
title: "Hardware advice for dev laptop upgrade"
date: 2019-08-02
forum: Hardware
---

### Post by jurito on 2019-08-02
Hello, I am considering an hardware upgrade and I'd like to have some competent opinions about it.

I am currently working on a Dell XPS17 701x, a pretty old machine with a fair amount of age problems but still doing its job, even if slowly and at brown dwarf temps.

Lately I had the chance to try a Huawei Matebook D ( with Win10 ) and I found it pretty sweet, especially for the price.

Considering I'd use it only for development on Ubuntu desktop, would the Matebook D actually be a decent upgrade or should i look for something more expensive/powerful when I have more budget?


A bit of specs:

**Current:**

[LIST]
[*]Intel Core i7-740
[*]16gb 1333Mhz
[*]Nvidia gt 445m
[*]sata SSD
[/LIST]


**Matebook:**

[LIST]
[*]AMD Ryzen 5 R5-2500
[*]8gb 2400Mhz
[*]AMD Vega 8
[*]NVMe SSD (extra)
[/LIST]


Thanks in advance.

---

### Post by TheFu on 2019-08-02
Listing  your top 5 needs from the system will  get you the best answers.

What do you need to do with this laptop?  You say "dev", but there area all sorts of different types of development.  
Perl, Python, Rust, C, Java, Php, Android, C#, any specific development tools or IDE, assuming you don't just use the Unix IDE?

Core i7-740 has a passmark less than 3200.  A mid-range chromebook is faster than that.
Discrete GPUs eat battery, so if you don't specifically need that and do want a longer battery - say 8-12 hrs, going with Intel onboard GPUs is more than good enough.
A SATA SSD is much slower than an NVMe SSD - usually 8x slower.

Ryzen 5 R5-2500 has a passmark of about 7300.

I have a used Asus 15 inch 1080p laptop w/ an  i5-8250U  passmark 7600. It was $305 on ebay, but $599 new. 

Might want to prioritize things important to you in the laptop too - screen resolution, size, battery, CPU, RAM, discreet GPU, storage, external ports, replacement RAM, disk, keyboard?

---

### Post by jurito on 2019-08-03
Thanks for the info!


Well with 'development' i meant mostly web, python and android/flutter. 
For sure i won't use it for gaming, but i would like to go back to Unity3d before or after, so a bit of a gpu might be needed. Battery life is not an issue atm, as I'd almost always use it plugged.


My biggest concern with the Matebook D is the soldered RAM though, even if now 8g might be ok precluding future upgrades feels a bit meh.

---

### Post by TheFu on 2019-08-03
If you want to do Android development, then you need 32G of RAM and the latest Core i7 CPU - look for 20,000+ passmarks.
Android development environments are total hogs.  And you'll need a huge HDD.

Python development can be done on a 2G RAM chromebook.

I have no idea what Unity3d is.

If I where in your situation, I couldn't spend the cash on a laptop to do Android development, but I could get a fairly powerful desktop for it AND a cheap-ish laptop that would let me remote back to my powerful desktop and do the development almost like being there.  Powerful, fast, laptops cost 4x what a similar powered desktop would cost.

---

