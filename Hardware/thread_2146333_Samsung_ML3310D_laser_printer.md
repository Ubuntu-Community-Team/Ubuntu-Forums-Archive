---
title: "Samsung ML3310D laser printer"
date: 2013-05-18
forum: Hardware
---

### Post by sayofethos on 2013-05-18
Hi,

Yesterday I was trying to set up a Samsung ML3310D monochrome laser printer to work with my Lubuntu, but surprisingly, though the product has been advertised as highly compatible with linux, Lubuntu Printer Setup was unable to find the proper drivers for it to function.

Is there anything else that can be done? How to tell whether a printer will work on a certain distro before purchasing it?

---

### Post by deadite66 on 2013-05-18
I had similar problems with a Dell printer i bought, distro should have pretty much the same support as they probably all use [cups]("http://www.cups.org/").
i noticed they do have drivers here [http://www.samsung.com/uk/support/model/ML-3310D/SEE-downloads](http://www.samsung.com/uk/support/model/ML-3310D/SEE-downloads).

it may be enough to extract the .ppd driver and install that.

---

### Post by sayofethos on 2013-05-18
> **deadite66 said:**
> I had similar problems with a Dell printer i bought, distro should have pretty much the same support as they probably all use [cups]("http://www.cups.org/").
i noticed they do have drivers here [http://www.samsung.com/uk/support/model/ML-3310D/SEE-downloads](http://www.samsung.com/uk/support/model/ML-3310D/SEE-downloads).

it may be enough to extract the .ppd driver and install that.

I got the files from the support page, but how do I extract the .ppd from the tar.gz folders?

I tried using the printer set up utility in Lubuntu and tried both the generic GDI as well as the text-only drivers, neither of which worked satisfactorily.

---

### Post by deadite66 on 2013-05-18
you can likely right click on the file and select unzup/extract
or in a terminal run: tar xvf UnifiedLinuxDriver_0.99.tar.gz

in the cdroot/Linux folder at the archive made there is an install.sh script.
you can try from the terminal: sudo ./install.sh
or
i don't know how lubuntu handles adding a printer, if it has an option for just using a .ppd file they are in cdroot/Linux/noarch/at_opt/share/ppd/

---

### Post by sayofethos on 2013-05-19
Gotcha.

It seems that the .ppd file for the ML3310D is not to be found in the folder downloaded from the support page. I am wondering if the Lubuntu library is up to date at all with drivers, since it seems like all the printers listed on the "popular" section in amazon are missing drivers from Lubuntu, which seems extremely odd since there are so many available from the manufacturers nevertheless.

Is there a list anywhere where one can check whether a printer works with Lubuntu or not?

---

### Post by rolmul on 2013-06-13
Hello,
the ppd for the ML-3310D should be [FONT=courier new]ML-331xspl2.ppd[/FONT].

-Roland

---

