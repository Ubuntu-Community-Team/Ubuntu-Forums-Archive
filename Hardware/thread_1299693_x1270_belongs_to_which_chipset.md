---
title: "x1270 belongs to which chipset?"
date: 2009-10-24
forum: Hardware
---

### Post by dE_logics on 2009-10-24
Here in this source - 

[http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon)

It says - 

R100/R200 (Radeon 7000 – Radeon 9250) and R300/R400/R500 (Radeon 9500 – Radeon X1950) class chips: 

and

R600/R700 class chips (Radeon HD 2300 – Radeon HD 4890): 



Which means that R300/R400/R500 has the graphs chips Radeon 9500 to Radeon X1950

and R600/R700 has chips Radeon HD 2300 – Radeon HD 4890

I have RS690 chipset which must belong to R600/R700 category and has x1270 card...which is strictly against what that page states.

It also states that R300/R400/R500 contains all chips till x1950 which is also wrong.


Now the official wiki page about AMD GPU - 

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units)

Confirms that RS690 has x1200 graphs chip which is supposed to be related to x1270 (but the drivers don't work)

We also have a separate page for the 690 series chipsets - 

[http://en.wikipedia.org/wiki/AMD_690_chipset_series](http://en.wikipedia.org/wiki/AMD_690_chipset_series)

Which confirms that RS690M has x1270 graphs chip.

Now...I've realized that no drivers except the opensource radeon drivers work; I wanna know if my 3-d is stable in accordance to the developers or not... cause I really don't know which category my chip belong to following all this.

I even have a feeling that R600 is very different from RS690; and I think the developers do not know about this...or do they?

---

### Post by dE_logics on 2009-10-26
Ubuntu has turn into a completely newbie forum...glad I'll be switching to Gentoo.

---

### Post by Yellow Pasque on 2009-10-27
> I have RS690 chipset which must belong to R600/R700 category and has x1270 card.
The RS690 is a mutant. In terms of basic fabrication/modesetting, the 690 resembles low-end R600 hardware. The 2d programming model is close to the R500 (Radeon X1k) series. The 3D hardware is actually derived from the Radeon X700 (R400) family. Basically, Catalyst/fglrx is a no go on this chip with X server >= 1.6 (i.e. Jaunty)

---

