---
title: "Which of these motherboard/CPU combos for under $100 will work with Ubuntu best?"
date: 2012-10-22
forum: Hardware
---

### Post by mark2741 on 2012-10-22
I posted yesterday a similar question but was too vague so no response : (

I live near a MicroCenter but just saw that NewEgg has motherboard specials with 8GB free RAM included so I'm leaning that way.

I have an Antec Nine Hundred case that I bought about 5 or 6 years ago (I see they still sell them!) and in it a Gigabyte motherboard with AMD x2 CPU. Ever since the day I bought it Ubuntu never really ran right on the Gigabyte motherboard so I eventually went back to Windows and now am looking for a PC for my basement that is medium-powered (I mainly use a laptop for my primary work) and not too expensive.

Was looking at these specials:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&Depa=0&Description=ppssmbaatc10161022&nm_mc=EMC-IGNEFL101612&cm_mmc=EMC-IGNEFL101612-_-EMC-101612-Index-_-MB-_-LEB0D](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&Depa=0&Description=ppssmbaatc10161022&nm_mc=EMC-IGNEFL101612&cm_mmc=EMC-IGNEFL101612-_-EMC-101612-Index-_-MB-_-LEB0D)

My limited understanding is that MSI and ASUS are best for compatibility with Ubuntu, but that Biostar motherboards are good too? Any recommendations on the under $100 boards?

---

### Post by pqwoerituytrueiwoq on 2012-10-23
board manf does not matter for comparability look at the chipsets
i have used 2 asus boards, 1 biostar and 1 gigabyte
they all work fine, just hate the bios on the gigabyte board (a55m-ds2) takes 30 seconds to slow the bios splash screen
both asus board have issues with the nic failing (one was a high end (~114 usd, open box at 70+shipping))
The Llano apus are based on the athlon II processors while the trinity ones are based on piledriver

---

### Post by mark2741 on 2012-10-23
I just don't want to get into the situation I was in when I originally put together this Gigabyte system. Unlike back then, I don't really enjoy building systems nor spending hours troubleshooting drivers, etc., so I just simply want an inexpensive motherboard that will work 100% with Ubuntu. Does one exist?

---

### Post by pqwoerituytrueiwoq on 2012-10-23
just noticed you want the cpu and mb for under 100 total which is really low end if possible 120-130 would be much better

as far as finding one 
just look up the sound and NIC chipsets on the board and google [shipset] ubuntu and see what comes up
also the video chipset (if applicable)

if you want a recommendation what are you using now
```
~$ cat /proc/cpuinfo | grep model
```and what will you be using the new system for

---

