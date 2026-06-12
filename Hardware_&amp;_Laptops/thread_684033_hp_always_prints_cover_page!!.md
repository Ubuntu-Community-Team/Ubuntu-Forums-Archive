---
title: "hp always prints cover page!!"
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by GlennW on 2008-01-31
I have an HP C4180 printer that I am very happy with. However, it has a very annoyed habit of always printing a "cover page" (that's what it says on the page along with the document title) before every document. I have looked through every thing I can find to see if there's a button that needs clicking/unclicking so that only my doc gets printed. It's also an incredible waste of paper!

Any help would be appreciated. Thanks.

---

### Post by smurphy_it on 2008-02-01
Sounds like you have a watermark turned on.  Goto System, administration, printing, click on your installed printer, then goto the tab marked Printer option, and scroll down the page to the Watermark/Overlay option and see if one is enabled.  If so, disable it.  That should fix the problem.

---

### Post by GlennW on 2008-02-02
> **smurphy_it said:**
> Sounds like you have a watermark turned on.  Goto System, administration, printing, click on your installed printer, then goto the tab marked Printer option, and scroll down the page to the Watermark/Overlay option and see if one is enabled.  If so, disable it.  That should fix the problem.

Thanks smurphy for the response. However, there is no "Watermark/Overlay" option. I checked in the "printing" options and also under the HPLIP options (System>Preferences>HPLIP) and there is nothing that corresponds to anything like this. I've subsequently googled this issue and have had no success. 

I'm still quite the Gutsy noob. I wonder, is there a printer config file I could edit or something similar?

---

### Post by smurphy_it on 2008-02-04
Did you try cups ?

In a web browser type localhost:631 and hit enter

That will bring up your web interface.  Then try the "Printers" tab, and see if there is any kind of Banner or Watermark enabled in there.  Otherwise, try surfing around the "administration" tab.

---

### Post by Bubba64 on 2008-02-05
You shouldn't have to do this but when you hit print in file you can choose pages and just put in the pages you want printed like 2-10 while your trying to figure out how to fix this.

---

### Post by GlennW on 2008-02-05
Thanks guys for your time and effort on this. My only option is to now contact HP and see what they have to say. CUPS was a wealth of info but I couldn't find anything. The only thing possibly related is the banner issue and it is currently set to "none." 

Thanks again.

---

### Post by Il Capitano on 2008-02-06
I had the exact same problem (also with an HP printer), and although it seems you didn't find your solution here, it worked for me. So i'll explain step by step what i did, and let's hope it works also for you:

First, start the cups manager by going to localhost:631 in your browser as smurphy_it pointed out.

Then, under welcome, click on "manage printers".

Then click on "set printer options'.

Then, under "PSC_1400_series: Banners", set both startbanner and endbanner to "none" and click on "set printer options" to confirm this choice (you probably need to enter your user name and sudo password for this).

This did the trick for me. Hope it helps.

---

### Post by GlennW on 2008-02-07
> **Il Capitano said:**
> I had the exact same problem (also with an HP printer), and although it seems you didn't find your solution here, it worked for me. So i'll explain step by step what i did, and let's hope it works also for you:

First, start the cups manager by going to localhost:631 in your browser as smurphy_it pointed out.

Then, under welcome, click on "manage printers".

Then click on "set printer options'.

Then, under "PSC_1400_series: Banners", set both startbanner and endbanner to "none" and click on "set printer options" to confirm this choice (you probably need to enter your user name and sudo password for this).

This did the trick for me. Hope it helps.

Thanks cap! I did as you suggested and discovered that all the banner options were already set to "none." I also checked under System>Preferences>HPLIP Toolbox and found the same thing. So, I've consigned myself to the fact that I need to buy paper and ink more often...

Thanks again.

---

