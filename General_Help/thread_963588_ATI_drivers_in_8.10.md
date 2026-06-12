---
title: "ATI drivers in 8.10"
date: 2008-10-30
forum: General Help
---

### Post by ericmtnbkr on 2008-10-30
Does anyone know if the display drivers in 8.10 have improved support for ATI graphics cards?  What's the best driver to use an ATI graphics card to its fullest in Ubuntu?

Thanks.

Eric :-D

---

### Post by carpex on 2008-10-30
Right now, the only way to get proprietary drivers that work in 8.10 is to use the ones in the repos. The drivers on the ATI website will not work yet with the new kernel. The proprietary drivers would give you more features and they are relatively stable. Otherwise, you can use radeonhd or radeon drivers in the repos, which are constantly improving. 

My suggestion is: try the open source ones, if they work for you, then stick with them. If not, install then proprietary ones.

---

### Post by Yellow Pasque on 2008-10-30
Most people prefer the proprietary fglrx/Catalyst driver because it contains the latest features. However, it isn't exactly known for being stable or bug-free. AMD/ATI still hasn't released the needed docs for the open-source devs to implement hardware acceleration on Radeon HD 2000-series cards and later.

If you have a Radeon X1k or AMD 690G integrated graphics, you can use the radeonhd driver, but the repos contain an old version of this driver and you'll need to build it yourself. See [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by Slug71 on 2008-10-30
Im just using the stock driver that comes with 8.10. Not the proprietary driver and it's all good here. Using the 64bit version of Ibex too.

---

### Post by meindian523 on 2008-10-30
Read the Release Notes.Some ATi Radeon cards are not supported in the new fglrx(proprietary) driver.

---

### Post by ericmtnbkr on 2008-10-30
Thanks for the quick replies.  I have a Readon X1300, I'll see what happens...

Eric

---

