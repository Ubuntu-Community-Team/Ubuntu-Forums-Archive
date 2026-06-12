---
title: "canon pixma mp980"
date: 2021-09-08
forum: Hardware
---

### Post by jgw on 2021-09-08
I have a canon pixma mp980   I used to be able to assign it a driver out of the pirinter list of drivers but, now, no longer.  I used to be able to print on both sides of the paper - no longer.  

Thoughts?

---

### Post by linuux on 2021-09-08
Maybe a file became corrupted or got deleted?

Is sane-pixma package installed?

[https://linux.die.net/man/5/sane-pixma](https://linux.die.net/man/5/sane-pixma)

These steps are options to install....but, you should be able to find the related canon driver in the non-free repository section, I would guess....

[https://www.ubuntupit.com/how-to-install-canon-printer-driver-in-ubuntu-linux/](https://www.ubuntupit.com/how-to-install-canon-printer-driver-in-ubuntu-linux/)

[https://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mp_series/mp980.html?type=drivers&language=en&os=linux%20(64-bit)](https://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mp_series/mp980.html?type=drivers&language=en&os=linux%20(64-bit))

It's possible (direct) support was dropped so more generic drivers have to be used....that's what I found with 2 websites.  I don't know if it's accurate but maybe that's what happened?

---

### Post by jgw on 2021-09-08
Thanks for the response!

I was installing my printers on a new system install.  When doing this ubuntu provides with a list of existing printer drivers.  In the one I had, however, it didn't have any canon pixma drivers at all which it used to have.  I also went to canon and they said that they had no linux drivers for this particular printer.  The old list did have the printer listed and the driver they had, for the printer was a driver with the word "gutenburg" in it (probably spelled wrong).  But I couldn't find that either.  

The sane-pixma package seems to be for the scanner on the printer.  I use vuescan which has software for my printer and most others too.  (bought that in 2001)

---

### Post by him610 on 2021-09-08
> It's possible (direct) support was dropped so more generic drivers have to be used
Yes, I believe that to be true. The particular generic PCL driver I used for my Dell 1700N for more than ten years was not included in the list of drivers in LTS 20.04. I initially installed the wrong one, but I wound up using one literally called, "Generic PCL Laser Printer" which works great.

---

### Post by linuux on 2021-09-08
> **jgw said:**
> Thanks for the response!

I was installing my printers on a new system install.  When doing this ubuntu provides with a list of existing printer drivers.  In the one I had, however, it didn't have any canon pixma drivers at all which it used to have.  I also went to canon and they said that they had no linux drivers for this particular printer.  The old list did have the printer listed and the driver they had, for the printer was a driver with the word "gutenburg" in it (probably spelled wrong).  But I couldn't find that either.  

The sane-pixma package seems to be for the scanner on the printer.  I use vuescan which has software for my printer and most others too.  (bought that in 2001)

> **him610 said:**
> Yes, I believe that to be true. The particular generic PCL driver I used for my Dell 1700N for more than ten years was not included in the list of drivers in LTS 20.04. I initially installed the wrong one, but I wound up using one literally called, "Generic PCL Laser Printer" which works great.

Yeah, that really sucks when a company withdraws support.  Canon is usually okay as printers go but when I buy a printer, I will check if they have linux drivers.  Canon, Epson and Brother are usually okay but I dunno how long Canon and Epson will support their printers in Linux for.   HP allegedly have dirty tricks with their ink cartridges but the support is usually decent.

I think Brother and HP are probably the best for Linux support but Canon has a lot of choices with their inkjet and multifunction machines - kinda difficult to bypass that.  

This might be interesting?:

[https://sourceforge.net/projects/cups-bjnp/](https://sourceforge.net/projects/cups-bjnp/)

---

### Post by deadflowr on 2021-09-08
You need the gutenprint driver package.
```
sudo apt install printer-driver-gutenprint
```
The packages was part of the recommends for the cups package and thus installed with cups automatically, but newer releases have seem to change that.

That should at least list the drivers in the driver setup page.
(whether or not the drivers work is another matter)

---

### Post by brian_p on 2021-09-10
```
apt install printer-driver-gutenprint
```

(And then I read **all** the posts).

---

### Post by jgw on 2021-09-12
thanks for all the help!

I installed the printer-driver-gutenprint   I then deleted the printer and re-installed it.  When I did that it automatically found the driver and assigned it to the printer!  Magic!

Thanks again!  

I will mark this as solved............

---

