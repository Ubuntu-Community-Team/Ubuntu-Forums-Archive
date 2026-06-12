---
title: "ATI graphic card on a laptop"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by gunnimar on 2009-11-06
Hi, I'm a relatively new ubuntu user and so far.... LOVING IT. I was stuck on using windows because of my school internet but i figured out a way to use that internet on my ubuntu and now i spend all my computer time on ubuntu.

However there is one thing bugging me. I installed the ati drivers from the package manager and yeah that was a big mistake since the system froze at login screen. So I removed the xorg-driver-fglrx and now im back in my gui. Is there any way to update my video drivers without suffering these kind of crashes? Basicly im trying to run heroes of new earth and eve online and it doesnt seem to work with my current video drivers?

I apologize about my english, not a natural speaker.

Again loving ubuntu.

---

### Post by Mark Phelps on 2009-11-06
Whether or not there is a driver update depends on the make and model video car/chip in your laptop.  Need to do an "lspic" and look for information on your video hardware -- and report back here.

We need more specifics to answer the question about video drivers.

---

### Post by gunnimar on 2009-11-07
Sorry about being unspecific, realized that now. I just did lspci and my graphic card is:

"01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400"

---

### Post by Mark Phelps on 2009-11-07
> **gunnimar said:**
> Sorry about being unspecific, realized that now. I just did lspci and my graphic card is:

"01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400"

OK ... there is no ATI restricted driver that works with your card and Ubuntu 9.04 or newer.  You will have to use the open source driver -- which is installed by default.

Since you removed the restricted drivers and installed the open source drivers, what you have is all there is.

---

