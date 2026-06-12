---
title: "Samsung ML-1520 Ubuntu 9.10"
date: 2010-03-05
forum: Hardware
---

### Post by sharemind on 2010-03-05
Hello,

I have just install ubuntu 9.10 but I am having problems with my laser printer 
[B]
Samsung ML-1520[/B]

The system reconise it, but when it print a pdf it** mess up all the layout** and it doen not print the images in the pdf. 

To solve the problem, I have tryed to install the **linux driver **from the samsung main web site. But I havent be able to install it correctly.

During the intrallation it does not reconise the printer. So I need to continue with a **manual installation**.
It ask me the **USB Port for the printer**, option are: ( /dev/mfp4, /dev/mfp5 ... /dev/mfp11 )

None looks to work :-(

It does not find the printer in the selected port.

Any advices ?

Thanks

---

### Post by coffeecat on 2010-03-05
According to [the OpenPrinting]("http://www.openprinting.org/printer/Samsung/Samsung-ML-1520") site, this printer works "perfectly" in Linux. The fact that it was printing at all before you downloaded the driver from Samsung suggests that the driver that came with Ubuntu is just fine.

The problem was more likely to have been in the app you were using - or possibly the PDF itself. I had a similar problem with a PDF. It displayed fine on screen, but was corrupted when I printed it. I tried a different PDF reader and was able to get a good print.

Instead of using Evince, you could install Okular - an excellent PDF reader. Or, open Synaptic, go to Settings > Repositories > Other Software Tab and tick the first line (partner). Do a 'reload' and you'll be able to install acroread, which is the Adobe reader.

As far as your printer is concerned, go to System > Administration > Printing and delete any reference to the Samsung printer. Now plug it in, switch it on and hope that the system autodetects it and reinstalls it with the default driver rather than anything you downloaded.

---

