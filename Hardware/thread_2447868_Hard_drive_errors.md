---
title: "Hard drive errors?"
date: 2020-07-27
forum: Hardware
---

### Post by jbutlin on 2020-07-27
Hi folks, apologies if I'm asking lots of stupid questions; I'm completely new to Linux... 
I've installed Ubuntu on an old Dell Inspiron - it was fantastic at first but a few weeks in I'm getting constant crashing, freezing and lots of I/O errors. The hard drive is a brand new SSD from Silicon Power A55. 
I don't even know where to begin with checking these problems.... Can anyone give me some advice?

thanks a lot,

---

### Post by Autodave on 2020-07-27
Fitsy thing: did you check all of your connections again to make sure that nothing came loose?

---

### Post by CatKiller on 2020-07-27
Drives can test themselves through a mechanism called SMART. You can access the results (and tell the drive to run its tests) by installing **smartmontools**.

You should also test your RAM. Data going to and from the SSD needs to go through the RAM, and issues with either can cause very similar symptoms.

---

### Post by jbutlin on 2020-07-28
Thanks a lot folks, I appreciate your answers - I am going to give smartmontools a go this evening!

---

### Post by jbutlin on 2020-07-28
I did - thanks. Nothing seems to be loose - it's all a bit strange considering this is a brand new hard drive.

---

### Post by CatKiller on 2020-07-28
> **jbutlin said:**
> I did - thanks. Nothing seems to be loose - it's all a bit strange considering this is a brand new hard drive.

FWIW, many things - including hard drives and SSDs - have failures that follow a "bathtub curve." There will be some number that fail very early, then the remainder will live long and productive lives till they start failing from old age.

---

### Post by Autodave on 2020-07-28
Unfortunately, new doesn't always = good.

---

### Post by jbutlin on 2020-07-31
That is certainly true, as my long experience with Windows systems has taught me! Thanks for all the advice folks, since I've run various diskchecking routines - I've not had a single freeze strangely - even though no errors were found on the disk. I don't know anything about the make of SSD I have (it was a present) but I suspect it's not a high quality make.
Thanks again all

---

### Post by guiverc on 2020-07-31
This is just a thought.  As you mentioned *old*, don't completely discount your box.  The new SSD may take more power (esp. when writing) than the original hdd, and older PSUs (power supply units) provide less power than when new/young, which can cause perfectly good devices to *misbehave*.

When an old box gives me trouble I can't explain, I try running it from a *live* system (ie. not using my default setup/configuration) to see if it occurs there, after memtests & checking disk status (SMART etc) that has already been covered.  Next I'd likely open the case & look for swollen capacitors etc especially for random freezing (the IO errors make me think more of PSU/power already mentioned..).  

Just my thoughts..

---

### Post by MartyBuntu on 2020-07-31
This sounds like a failing power supply...

---

### Post by kurt18947 on 2020-08-01
> **jbutlin said:**
> I did - thanks. Nothing seems to be loose - it's all a bit strange considering this is a brand new hard drive.

It's not unheard of for brand new electronic gadgets to fail very early in their lives - some refer to it as infant mortality. It's also possible that the manufacturer's quality control people were off their games when your device was manufactured. Good advice offered here, SMART tools and memtest.

---

