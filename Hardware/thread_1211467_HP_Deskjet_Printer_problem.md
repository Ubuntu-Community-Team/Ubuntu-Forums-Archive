---
title: "HP Deskjet Printer problem"
date: 2009-07-12
forum: Hardware
---

### Post by Bini_1 on 2009-07-12
I'm having problems with my printer since installing Ubutu.
The printer worked fine under windows but when I try printing the test page under Jaunty
its squished up at one side of the page and the page is all grey.

I've tried removing the printer and re-adding it, and downloading HPLIP without any success.

The printer is HP deskjet 950c

Bini

---

### Post by coffeecat on 2009-07-12
> **Bini_1 said:**
> I've tried removing the printer and re-adding it, and downloading HPLIP without any success.

When you say 'removing the printer and re-adding it', do you mean you deleted the printer in System > Adminstration > Printing and then reinstalled it? Or do you mean that you simply unplugged the printer and plugged it back again. I'm sure you mean the former, but if not, try deleting and reinstalling. It sometimes works.

As far as hplip is concerned, that package should have come in a default install, but what doesn't come and is very useful is hplip-gui. Try installing that with Synaptic - it's a nice GUI frontend. Once installed, you can find it at System > Preferences > HPLIP Toolbox. Have a look in the various options and see if that helps.

Lastly, open firefox and type "localhost:631" (no quotes) in the address bar. That's the CUPS configuration utility. It's much more comprehensive than the standard printing utility. See if anything there helps. As a last resort, use it to delete and then reinstall your HP printer, because that model is reported as working "perfectly" with Linux at the OpenPrinting website. See:

[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_950C](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_950C)

---

### Post by Bini_1 on 2009-07-13
Sorry, it's only now I re-read my post without the aid of beer, I can see there is no useful info there at all.

Yes, I removed the printer and re-installed rather than unplugging it.

I had a lot of problems with some of the HP packages complaining about HPMUDEX not being installed properly.  Several attempts at removing and re-installing haven't solved the problem.

Anyway the problem is now solved, I followed the link you posted and downloaded the ppd file from there.  It is now printing properly.

Thanks for your help

---

### Post by coffeecat on 2009-07-13
I'm glad it's working.

> **Bini_1 said:**
> I re-read my post without the aid of beer

Ooh, don't worry about that! I once managed to restore the Windows mbr to a mono-booting hard drive of Ubuntu on which there wasn't a whiff or hint of Windows - until I restored the mbr that is. Didn't do much for Ubuntu either. That was with the "aid" of a glass too much of red wine. :oops:

:lol:

---

