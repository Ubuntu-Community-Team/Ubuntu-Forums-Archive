---
title: "How to get hardware acceleration for Radeon 7500"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by UrbenLegend on 2007-11-14
I recently upgraded from Feisty to Gutsy, doing a clean install. However, I was dismayed by the fact that I can no longer get hardware acceleration for my radeon 7500 card. This card used to work in Feisty. I've tried setting the device driver in the Screens and Graphics dialog to radeon and even ati, but they all gave me a blank screen. The only choice that works is Vesa which has no acceleration at all. How do I fix this?

---

### Post by UrbenLegend on 2007-11-16
Anyone?

---

### Post by shad0w_walker on 2007-11-16
You have installed the right drivers I assume? Just making sure.

---

### Post by Vadi on 2007-11-19
Delete your xorg.conf.

X will then reconfigure the card, and Compiz will work okay :) (I'm on a radeon 7500 too)

---

