---
title: "Hp printers and HPLIP"
date: 2013-02-18
forum: Hardware
---

### Post by grizdog on 2013-02-18
Hello

I need a new printer.  I hardly ever use it, so I just want a cheap all-in-one, with wireless capability.  I don't need high speed or anything fancy.

And of course, it has to work with Ubuntu.  It looks like an HP is the best bet in that department, so I went to the local big box store, bought an HP deskjet 3510, and tried to install it.  I brought up the cups interface for HPLIP, it found the printer, asked my what it was and I said hp deskjet 3500 series, and it said it was done and the printer was ready.  Of course, nothing would print (except the test page).  When I went to the HPLIP site, 

[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3510_series.html]("http://http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3510_series.html")

and discovered that it was not recommended.  So I took the printer back.  I want to be more careful with the next one.  I have found some models that are for sale, and recommended on the HP:IP site, like the photosmart 6520, but I wonder if the 3510 was really incompatible.

Is HPLIP all you have to run ? not the printer tool in ubuntu?  I worry about defining the same thing twice.  Does anyone have any recommendations ?  I relly long for the days when you didn't have all these fancy interfaces and had to make unintelligible entries in a configuration file by hand.  Now everything is so opaque.

Thanks for any help.

---

### Post by lyni on 2013-02-18
if you go to this link [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)
it allows you to check your ubuntu system to the various printer models so you can buy the model that matches.

hope that helps
lyn

---

### Post by Bucky Ball on 2013-02-19
*Thread moved to **Hardware**.*

---

### Post by Javelin Dan on 2013-02-20
grizdog – 
   
   
  I just went through all this with a 3510 Deskjet. I’m actually using this on an old powerpc Mac so I would THINK it would be easier in your case, but of course I don’t really know. In my case, Ubuntu would install the printer which would print OK, but it wouldn’t recognize the scanner. 
   
   
  I called the support people at HP and was told that all the support for Linux is on the HPLIP website, so you got to the right place. They also told me that Ubuntu probably installed a “generic” driver that would allow the machine to print but not scan. They said if I found the right driver, everything should work. CAUTION: if you search just for supported printers, you won’t see this model listed. But if you follow the wiki and fill in the fields, when it comes time to select the model of printer, you’ll find it in the list. 
   
  After filling out all the required fields you are instructed to download an HPLIP “run” file. Do this and save it to your desktop. You then start the installation wizard and are given a choice of “manual” or “automatic”. I’ve done it both ways, and suggest just going with “automatic”. It ended up making all the same choices I did in “manual” and for some reason ran faster. Now pay attention here; at one point you will be asked if you want to use the “run” file you already downloaded or use an updated one. I wrongly assumed the updated one would be better, but could never make it work. I went back and restarted the whole process and used the “run” file on my desktop and didn’t have any problem. After all the command line installation script, you will be taken to a GUI installer for your printer (you MAY have to install the HPLIP GUI frontend out of Synaptic -I did this in advance and don’t know if it’s automatically installed out of the HPLIP website). One more word of CAUTION: you still have to go into the “Printing” manager in “System Tools”, right click on the printer icon, and make it your default printer. I actually had two icons when done: Deskjet 3510, and Deskjet 3510-2. I chose Deskjet 3510-2 and everything worked fine. I can’t tell you if it makes any difference if you pick the first one. 
   
  I know you said you already returned your printer, but I hope this helps you or someone else in case you decide to pick up another HP printer. Yeah, they’re cheap and junky, but they work pretty well and I think you’ll get as much or more support for Linux from them as anybody.

---

### Post by oldfred on 2013-02-20
I recently bought the HP 3520 and while only printing a few pages am very happy.

It did install a default printer as soon as I connected but it was very limited and  could not easily reconfigure wireless to use my already set up wireless. 

But once I downloaded the hplip driver every thing has worked. I used the software to connect/setup  my wireless, scanning worked and my wife was happy, she could print from ipad (most important :) ). 

Printer only comes with starter print cartridges so I do not know about cost/use. But I use it very little so it is not a big criteria for me.

---

