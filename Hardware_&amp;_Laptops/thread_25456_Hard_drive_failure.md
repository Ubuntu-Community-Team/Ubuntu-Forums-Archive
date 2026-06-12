---
title: "Hard drive failure"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by willis on 2005-04-10
Just as I was transfering my tarballed home directory from my laptop to a safe place in preperation for installing a clean hoary, my hard drive started getting bad blocks galore.

i have this drive now: [old drive](http://www.newegg.com/app/ViewProductDesc.asp?description=22-149-009&depa=0) 

i'm thinking of getting this drive: [new drive](http://www.newegg.com/app/viewProductDesc.asp?description=22-149-026&depa=0) 

my question is the old drive is IDE ULTRA ATA-5 and the new drive is IDE ULTRA ATA-6, i'm not much of a hardware guy, is my laptop (a sony pcg-v505ex) able to support that interface.

I tried looking up those terms in various glossarys and google, without much success.

You'll find the specifications of my laptop [here](http://esupport.sony.com/perl/model-documents.pl?mdl=PCGV505EX) but they've never been much help.

thanks in advance, it's probably a pretty simple question.

---

### Post by skoal on 2005-04-10
Is your hard drive portable?

What does 'lspci -v | grep -i ide' give you?

Worst case, if you buy the newer ATA133 drive and you can't use UDMA6, then you will still be able to use the UDMA5 (compatibility) ATA100 the newer drive is capable of as well.

---

