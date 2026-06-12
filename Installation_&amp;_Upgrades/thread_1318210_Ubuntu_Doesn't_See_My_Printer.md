---
title: "Ubuntu Doesn't See My Printer"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by claypigeon on 2009-11-07
[SIZE=3]This past week I installed Virtual Box and then installed Ubuntu 9.04. In Ubuntu I tried to see my printer. It wasn't there and Ubuntu was unable to locate it. I was able to get on the Internet okay and the browser is working fb. I just want to be able to print from Ubuntu.

I removed Ubuntu 9.04 from Virtual Box and installed Ubuntu 9.10 and had exactly the same results. I am a complete Novice with Linux and feel like a fish out of water. I'm getting ready to scrap Virtual Box and forget the entire experiment. Anybody has any ideas why I can't see my printer within Ubuntu, I'd appreciate hearing from them.

My host system is Microsoft Windows XP, with Service Pack 3. I'd like to experiment with Linux but I use Amateur Radio programs like Qsonet's CQ100, EchoLink, and HamSpere. These programs are not available to me in Linux so there's no way I can leave MS Windows. Before I junk the whole project I'd like to hear from those using VB with an XP Host and Ubuntu Guest. 
[/SIZE]

---

### Post by Dimarchi on 2009-11-07
You don't mention the maker and model of your printer...

One thing you could try is having your printer on before you start your Virtual Box. For what it is worth, 9.04 could see my printer but 9.10 does not no matter what I have tried so far (Okidata Okipage 8iM). To my knowledge this is due to the specific version of CUPS used in 9.10 (1.4.1) - if it were some other version my printer would be there for me to use. :D

---

### Post by claypigeon on 2009-11-07
> **Dimarchi said:**
> You don't mention the maker and model of your printer...

One thing you could try is having your printer on before you start your Virtual Box. For what it is worth, 9.04 could see my printer but 9.10 does not no matter what I have tried so far (Okidata Okipage 8iM). To my knowledge this is due to the specific version of CUPS used in 9.10 (1.4.1) - if it were some other version my printer would be there for me to use. :D
My printer was on and its an HP 1200S Laser Printer.

---

### Post by Dimarchi on 2009-11-10
Well, that's the end of my expertise in the area. Time for other HP 1200S owners to reply. :p

---

### Post by Bucky Ball on 2009-11-10
Yep, HP are very well supported but I don't see a HP 1200S anywhere here:

[http://h20180.www2.hp.com/apps/Nav?h_pagetype=s-001&h_lang=en&h_cc=us&h_product=236252&h_client=S-A-R163-1&h_page=hpcom&lang=en&cc=us](http://h20180.www2.hp.com/apps/Nav?h_pagetype=s-001&h_lang=en&h_cc=us&h_product=236252&h_client=S-A-R163-1&h_page=hpcom&lang=en&cc=us)

You sure there's not more to the model number or name? I can definitely point you in the right direction if I could find the device.

* PS: there is TONS of amateur radio apps in Ubuntu. The idea is to think about native open-source alternatives to what you are currently using in Windows. There are plenty but sometimes no replacement for the Windows app you just can't do without. Go to Applications->Add/Remove.

---

### Post by Bucky Ball on 2009-11-10
Now I have it. There is a listing for a 1200 or a 1200se here:

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

Put in the correct details, choose your printer and follow your nose. Any problems get back to us. The HPLip set-up uses a terminal like a GUI and you just read carefully and follow what you are told to do. Easy. According to this page your printer should work perfectly:

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1200](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1200)

---

