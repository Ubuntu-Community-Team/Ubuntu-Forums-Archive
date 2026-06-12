---
title: "Samsung ML-2525 W Printer on Ubuntu Gnome"
date: 2017-08-20
forum: Hardware
---

### Post by k-bosike on 2017-08-20
Dears
how can I get my printer working Samsung ML-2525 W on Ubuntu Gnome latest version.

When I choose printer installation and add the printer which was found by the Ubuntu system it seems everything ok.

But when I send a task to the printer (print job) than nothing happens. Even I do not see a print job waitin in the quew ?

Am I really that stupid that I did not get it work ? 

BR  and thx a lot
Y
kbo

---

### Post by kurt18947 on 2017-08-20
This is odd. I have a Samsung Multi-function device and it uses Samsung's linux driver. My machine is also supported by open printing but not all features seem to work using the open driver. When I check your printer - ML2525W - I see only a Windows driver. Samsung offers - or at least used to offer - a **U**nified **L**inux **D**river (ULD) I'm looking for it on Samsung's site and it isn't coming up. Now I'm curious, I'll post back if I find an answer.

Edit:  Here's something. It says your printer is supported. I generally prefer to download directly from the manufacturer's site but Samsung has hidden their linux drivers very well.

[http://www.bchemnet.com/suldr/supported.html](http://www.bchemnet.com/suldr/supported.html)

---

### Post by kurt18947 on 2017-08-20
Okay, here's the linux driver from Samsung. The model is different from yours but there is only one linux driver for all Samsung printers as far as I know.

[http://www.samsung.com/us/support/owners/product/wireless-mono-laser-w-duplex-m2820](http://www.samsung.com/us/support/owners/product/wireless-mono-laser-w-duplex-m2820)

The driver I've used is the 7th from the top, 
[LEFT][COLOR=#000000][FONT=SamsungOneLatinWeb][COLOR=#636363][FONT=SamsungOneLatinWeb]OCT 28,2015[/FONT][/COLOR]
[COLOR=#000000][FONT=inherit][FONT=inherit]Print Driver[/FONT] ver. V1.00.36_00.91, MULTI LANGUAGE 14.66 MB          
[/FONT][/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=SamsungOneLatinWeb][/FONT][/COLOR]I can't promise this will work but this is what I'd try, or the repository in the previous post. You could also check Samsung's site for your country if not the U.S, your model doesn't seem to be sold in the U.S. 
[/LEFT]

---

