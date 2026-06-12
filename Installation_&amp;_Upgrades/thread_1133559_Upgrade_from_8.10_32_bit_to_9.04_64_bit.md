---
title: "Upgrade from 8.10 32 bit to 9.04 64 bit ?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by dr_alejandro on 2009-04-23
Hello,

I'm running the 32 bit version of Ubuntu 8.10. I am considering to change to the 64 bit version when in upgrade to 9.04. I know I can upgrade to 9.04 with Alt+F2 and type in “update-manager -d” .....
but that will install the 32 bit version of 9.04. Am I right?

If I want to install the 64 bit version of Ubuntu 9.04, do I have to make a fresh installation (burning the ISO to a CD)? Or can I install the 64 bit version of Ubuntu 9.04 from the version of Ubuntu I'm running (32 bit version)?

---

### Post by Brian_the_King on 2009-04-23
Someone correct me, but you will have to format and start over fresh.

---

### Post by ArsHermetica on 2009-04-23
You'll have to start from scratch unless i'm missing something huge.

---

### Post by MaindotC on 2009-04-23
No you cannot upgrade from 32 to 64 without reinstalling as the others have stated.  That would be an interesting feature in the future, though.  Maybe some way to take your machine from 32 and put it into 64 bit mode...

---

### Post by pbpersson on 2009-04-23
That would be very much like if you had a 10-story office building and you wanted to replace the foundation under the building and the building itself without moving a single piece of office furniture.

It is better just to start from scratch.

---

### Post by andy75180 on 2009-04-23
Yes, you will definitely have to start over fresh to do this. I changed my motherboard/processor to a 64 bit one and had to do a complete reinstall.

Do you really need to change to 64 bit? If you don't have over 4gb of memory I don't see any point.

---

### Post by dr_alejandro on 2009-04-23
Yeah that's what I suspected. I do have 4GB of RAM, I do not have to run the 64-bit version but i might as well use that extra GB I'm not using. It might take me a few 1 or two days to configure the computer like I had it in the 32-bit version (plugins, themes,...) but I'm curious of to use the 64 bit.

---

### Post by MaindotC on 2009-04-23
If you want to use all 4 GB with a 32-bit Ubuntu you need to recompile the kernel with an option that I can't remember.  If you ever find it lemme know.

---

### Post by drs305 on 2009-04-23
> **strAlan said:**
> If you want to use all 4 GB with a 32-bit Ubuntu you need to recompile the kernel with an option that I can't remember.  If you ever find it lemme know.

I believe it's called PAE.

---

### Post by dr_alejandro on 2009-04-24
Thanks! I'll look into that.

---

### Post by andy75180 on 2009-04-25
Yes, PAE (Physical Address Extension) allows up to 64GB of memory on a 32-bit machine. But the memory will be slower.

---

### Post by schettj on 2009-06-17
> **andy75180 said:**
> Yes, PAE (Physical Address Extension) allows up to 64GB of memory on a 32-bit machine. But the memory will be slower.

Or just install the server kernel via synaptic, which includes PAE. I'm running a 4gb and a 6gb dual core machine with the server kernels, and they see all that ram just fine (except for possibly a small hole for the graphics card memory, YMMV depending on your bios)

---

### Post by LepeKaname on 2009-06-17
As far as I know you can use up to 8GB in the 32bit version... but it does not run natively... My general recommendation is to stay in 32bit, 64bits usually is not as stable.

---

