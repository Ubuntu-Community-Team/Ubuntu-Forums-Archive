---
title: "Ram Question"
date: 2009-03-24
forum: Hardware
---

### Post by joshh88 on 2009-03-24
I want to upgrade my DDR Ram. I have become confused on the numbers what with the different Mhz and PC2-6400 or what not. This is what I have an XPS M1330 from dell the current ram is DDR2 SDRAM 667Mhz PC2-5300 NON-ECC. Dell's website shows that it can take the 800Mhz and the PC2-6400, but whats the difference and now that I'm running Linux will it still support up to 4gigs?

---

### Post by tad1073 on 2009-03-24
The difference is the mhz's, 667 vs. 800. Also bus speed is a factor. And yes Linux will support up to 4gb on a 32 bit system.

Oh, and # of pins too.

---

### Post by lisati on 2009-03-24
> **tad1073 said:**
> The difference is the mhz's, 667 vs. 800. Also bus speed is a factor. And yes Linux will support up to 4gb on a 32 bit system.

Oh, and # of pins too.

Thanks. I, too, was researching extra RAM for one of my machines, and wasn't sure of some of the niceties.....

---

### Post by mcduck on 2009-03-24
Those are just different ways of telling the same thing:

DDR2-667 is also known as PC-5300, it runs at 166MHz internal frequency and 333MHz I/O bus, and transfers 5333MB/s (or 667 million transfers/s)

DDR2-800, also known as PC-6400, runs at 200MHz internal clock and 400MHz I/O bus, and transfers 6400MB/s (or 800 million transfers per second).

You can usually replace lower speed memory with higher speed one, it will just run at the speed your computer supports. You can also mix different speeds, but all RAM will run at the speed of the slowest memory you have installed.

32-bit Linux, just like any other 32-bit OS, supports up to 4GB of memory. But this also includes other things, like the memory in your graphics card. You will usually get something about 3,2–3,5GB of RAM. If you enable PAE (or use the server kernel) you can use even more than 4GB of RAM. But unless you really need that much memory I wouldn't recommend it, as PAE increases memory latency which would have a negative effect on your systems performance if you aren't really using the extra RAM for anything.

---

### Post by stchman on 2009-03-24
> **joshh88 said:**
> I want to upgrade my DDR Ram. I have become confused on the numbers what with the different Mhz and PC2-6400 or what not. This is what I have an XPS M1330 from dell the current ram is DDR2 SDRAM 667Mhz PC2-5300 NON-ECC. Dell's website shows that it can take the 800Mhz and the PC2-6400, but whats the difference and now that I'm running Linux will it still support up to 4gigs?

Install the proper specified RAM according to the manufacturer of the laptop.

I have a Toshiba laptop that takes PC2-5300 667Mhz DDR2 SO-DIMM.  Make sure that when you buy RAM that you use those as minimum specs.  You can use 800MHz PC2-6400 DDR2 in place of PC2-5300.

As far as ECC and non-ECC, ECC is pretty much for servers and rarely used in desktops and unheard of in use on laptops.

Just make sure to follow the manufacturer specifications.

---

### Post by joshh88 on 2009-03-24
I was just reading about that in another thread. I think I've been swayed to just getting up to 3gigs. I don't really do too much hardcore computing that needs 4gigs,sometimes gaming but now it doesn't work with Linux so no need.

---

### Post by lisati on 2009-03-24
> **stchman said:**
> Install the proper specified RAM according to the manufacturer of the laptop.

I have a Toshiba laptop that takes PC2-5300 667Mhz DDR2 SO-DIMM.  Make sure that when you buy RAM that you use those as minimum specs.  You can use 800MHz PC2-6400 DDR2 in place of PC2-5300.

As far as ECC and non-ECC, ECC is pretty much for servers and rarely used in desktops and unheard of in use on laptops.

Just make sure to follow the manufacturer specifications.

Let's see if I have understood: I have a Toshiba laptop that, according to the instruction book, takes PC2-4200 style memory card. As long as I use that as a guide to *minimum* specification, I should be fine when upgrading and/or replacing mememory modules. Is this a fair comment?

---

### Post by mcduck on 2009-03-24
> **lisati said:**
> Let's see if I have understood: I have a Toshiba laptop that, according to the instruction book, takes PC2-4200 style memory card. As long as I use that as a guide to *minimum* specification, I should be fine when upgrading and/or replacing mememory modules. Is this a fair comment?

Yes, that should work fine.

Although some laptops can be a bit picky about which RAM modules they support and which they don't. If you want to be *absolutely* sure at least Kingston has a very good database on their web site that you can search to check which ones are guaranteed to work with your laptop.

---

### Post by lisati on 2009-03-27
> **mcduck said:**
> Yes, that should work fine.

Although some laptops can be a bit picky about which RAM modules they support and which they don't. If you want to be *absolutely* sure at least Kingston has a very good database on their web site that you can search to check which ones are guaranteed to work with your laptop.

A belated "thank you". I'll look into the Kingston site when I get a chance.

(Amongst other things, distracted by a re-organization of our lounge at home the other day. What should have been a 1-to-2-hour effort turned into an all afternoon effort, and now to get all the computer gear setup properly, including the VOIP adapter that lets me share the normal phone between Skype and the regular phone line.)

---

