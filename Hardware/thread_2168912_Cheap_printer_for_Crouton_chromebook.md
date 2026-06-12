---
title: "Cheap printer for Crouton chromebook?"
date: 2013-08-19
forum: Hardware
---

### Post by HenryHall on 2013-08-19
Hi,
I have a new Samsung Chromebook, the one with the exnos processor.

I have installed Crouton with Ubuntu 12.04 LTS (Precise Pangolin) and it runs LibreOffice just fine.
However, it appears that it does not want to know my Brother HL2270DW laser printer.
Although Brother claims to have a linux driver (forgive the naive question) I am guessing that it is compiled for i386 (the name includes i386) and so won't run on the exnos.
I'm not sure I'm up to compiling it down from source (unless there is no other way), just because of the work of getting a development environment up. I'm sure I could do it, but not in any reasonable timescale.

So my question - has anyone got a _cheap_ _current production_ monochrome laser printer working in that environment that I can just go out and buy from Walmart or wherever?
It wouldn't really help me if the printer were expensive, or no longer available new, or won't work on current production Samsung Chromebook with Ubuntu.

I have not found even one printer that meets those needs, yet if I still had a LaserJet 4 it would probably work (can't get them today and never were cheap until worn out).

Thanks for a lively interesting forum, I hope my future writings ill be less trivial and boring. Right now I just need to print some essay thingies without having to email it to a windows machine :-(
Getting rid of intel and windows is what this exercise was all about after all.

Oh, as an aside, if I do end up having to compile a driver is this machine up to development work or is something else recommended?

---

### Post by newb85 on 2013-08-19
I don't know anything about Crouton, but on my regular installs of 64-bit 12.04, I installed the drivers for my MFC-3360C from the Brother support site, which were 32-bit.  Following the prescribed pre-installation procedures made everything work just fine.

---

### Post by HenryHall on 2013-08-20
> **newb85 said:**
> I don't know anything about Crouton, but on my regular installs of 64-bit 12.04, I installed the drivers for my MFC-3360C from the Brother support site, which were 32-bit.  Following the prescribed pre-installation procedures made everything work just fine.
Yes but were the drivers 32bit i386 instruction set or 32bit ARM code?
Or are they source that gets compiled at installation so it doesn't matter?

---

### Post by Vladlenin5000 on 2013-08-20
You're running an armel or armhf architecture due to the Exynos (ARM) CPU instead of the "traditional" 32-bit or 64-bit x86 desktop architectures. You're correct about the available package being i386 only and as such it's supposed to be installed in that architecture only. 

[http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/download_index.html?reg=us&c=us&lang=en&prod=hl2270dw_all&dlid=&flang=English&os=128&type2=-1](http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/download_index.html?reg=us&c=us&lang=en&prod=hl2270dw_all&dlid=&flang=English&os=128&type2=-1)  Here you have _both deb packages and source code_ and here [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004) are the instructions/requirements for Debian/Ubuntu 64-bit that must be fulfilled before attempting to install the drivers with the same 32-bit deb with the "recommended" force-all argument:

```
**dpkg -i --force-all  (lpr-drivername)**
```

It may or may not work for ARM. If not you can use the source code and compile for your machine.

---

### Post by Vladlenin5000 on 2013-08-20
> **HenryHall said:**
> So my question - has anyone got a _cheap_ _current production_ monochrome laser printer working in that environment that I can just go out and buy from Walmart or wherever?

Here's an idea: Use the "add printer" wizard in order to simulate the process and check which models are already supported. There are many Brother models already there.

---

### Post by HenryHall on 2013-08-20
> **Vladlenin5000 said:**
> Here's an idea: Use the "add printer" wizard in order to simulate the process and check which models are already supported. There are many Brother models already there.

Thank you for both of the responses, truly appreciated.

Yes, it looks like I will have to compile from source, however that is something I need to relearn (any guidance as to the most efficient place to do the "lots of reading" would be welcome) after a 20 year absence from doing any serious software development. Not exactly the happiest news to a newbie.

It makes sense to get a cheap laser printer going first of course.

The problem with "add printer" is that it lists, literally, thousands of printers, but I can't find any of the dozen or two presently for sale at my local Target store etc. That is of course because in the modern world no model stays in production for longer than a few months before they move on to the next new thing.  However I will try again.

So I am still hoping to find someone with one of these toys who has bought a cheap printer for it that works with it.

Oh if anyone else knows where else the topic of printers for the exnos chromebook is being discussed it would be great to have a pointer to it (thanks).

But let me say, Vladlenin (love that name), that I truly appreciate your popping in to help a newbie. Not that I'm new to computers you understand, I'm retired in Florida and first cut my programming teeth on an IBM-1401, punched cards and all. 6 bit byes we had back then, and walked to school barefoot (only the last part is an exaggeration).

---

### Post by HenryHall on 2013-08-20
Well, slight progress, to encourage anyone else plying the same path.
1. HP DeskJet 3511 is a $40 printer that is not yet compatible but has  IP wireless, so it can be used for hp eprint (which is email hp and they  print what is sent by email on your own networked printer).
Cheesy but it's a start.

Now, how does one build from source a printer driver on this thing?

---

### Post by kurt18947 on 2013-08-21
> Now, how does one build from source a printer driver on this thing?

Building a printer driver for an ARM based machine?  I'm not certain but at least on this forum I think you might be a pioneer.  Good luck

---

