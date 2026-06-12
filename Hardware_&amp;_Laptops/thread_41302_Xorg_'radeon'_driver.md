---
title: "Xorg 'radeon' driver"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by Strife on 2005-06-12
So I recently discovered the Xorg 'radeon' driver (as opposed to the fglrx and ati drivers), and found that while it does not support 3D acceleration for my card, it does support 2D.

Now, I want to find the web site for this project, because I would like to see if there is any progress on getting 3D acceleration going. I spent a good hour and a half on google, but unfortunately, any search with the word 'radeon' in it will inevitably give me any result but what I want. So does anyone know what the website for this project is?

---

### Post by RastaMahata on 2005-06-12
[QUOTE=Strife]So I recently discovered the Xorg 'radeon' driver (as opposed to the fglrx and ati drivers), and found that while it does not support 3D acceleration for my card, it does support 2D.

Now, I want to find the web site for this project, because I would like to see if there is any progress on getting 3D acceleration going. I spent a good hour and a half on google, but unfortunately, any search with the word 'radeon' in it will inevitably give me any result but what I want. So does anyone know what the website for this project is?[/QUOTE]
 [www.ati.com](www.ati.com) radeon driver for linux. Fast and easy.

[http://www2.ati.com/drivers/linux/ati-driver-installer-8.14.13.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.14.13.run)

Instructions here: [http://www2.ati.com/drivers/linux/linux_8.14.13-inst.html](http://www2.ati.com/drivers/linux/linux_8.14.13-inst.html)

And yes, **This is a graphical installer**, no weird commands or anything. At the end, it tells you to reboot, and you, as a linux user, should reboot your X server (ctrl+alt+backspace).

I'm an Nvidia user, so I havent tested it. Good luck.

---

### Post by Zeroedout on 2005-06-13
if you went to the ati site, you would have gone to the linux section ( [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27) ) and seen the list of projects under [size=2]Getting involved in Linux development[/size]. There, listed, are the utah glx poject ( [http://utah-glx.sourceforge.net/](http://utah-glx.sourceforge.net/) );  the GTAOS  project ( [http://gatos.sourceforge.net/](http://gatos.sourceforge.net/) ); and the Driect Rendering Infrastructure, known on the site as the Direct Rendering Open Source Project ( [http://dri.sourceforge.net/](http://dri.sourceforge.net/) ). Seriously bro, if you had nuff time to dick around google for an hour and a half and not have enough time to actually look at the website of the company on which you are trying to find drivers for........... I mean it didn't occure to you at any point in time that they KNOW their driver support is shitty, so they might just point you to others who are trying to write better support? Sorry if I come off a tad bitter, it just really pisses me off that in a god damned hour and a half, you couldn't find these websites. I mean shit buddy, i'm stoned right now and it only took me 3 mins to find these sites. Anyways tho, if you got that much time, try contributing some to these projects, it would really kick ass to have an opensource driver that could do decent 3d accel, they could use the help; not an easy task to do what they're attempting.[]("http://www.xfree86.org/")

---

### Post by jrhodes on 2005-06-13
The 3D driver that our buddy Strife here is referring to can be found at [http://r300.sourceforge.net/](http://r300.sourceforge.net/). It is terrifically unstable and as such is **not** linked from ati's site, which links only the central dri site. 

However, it does sometimes work, and the warning that it might break your hardware is there only to cover the developers' asses.

---

### Post by Strife on 2005-06-13
Sigh... I wish people would actually read my post before assuming I'm an idiot.

I specifically said the **radeon** driver. I even said, and I quote,

> as opposed to the fglrx and ati drivers

That is, when you specify the driver in xorg.conf, the one I am referring to is called 'radeon' and **not** 'fglrx' or 'ati'. So please, before you insult my intelligence, try reading and understanding my post first. If you don't get it, then don't bother responding. You're not doing anyone good by flaming me.

Anyway, the R300 driver is also not what I was referring to, but that is interesting, and I may at least take a look at it just for fun.

---

### Post by jrhodes on 2005-06-13
The project pages for the radeon and r200 dri drivers can be found at [http://dri.sourceforge.net](http://dri.sourceforge.net)

---

### Post by Strife on 2005-06-13
[QUOTE=jrhodes]The project pages for the radeon and r200 dri drivers can be found at [http://dri.sourceforge.net](http://dri.sourceforge.net)[/QUOTE]

Ahh. I eventually found it. Not exactly the easiest page to navigate. Thanks.

That was also very helpful in that it looks like you're right, what I want is in fact the r300 driver. From what I gathered from the above site is that there isn't really any  more 3D development going on for anything above rv280... But I could be wrong. They were a little bit vague.

Thanks again.

---

### Post by ganatronic on 2005-06-14
[QUOTE=Strife]Sigh... I wish people would actually read my post before assuming I'm an idiot.
[/QUOTE]

in regards to
[QUOTE=Zeroedout] :-P rant

I mean shit buddy, i'm stoned right now and it only took me 3 mins to find these sites. [/QUOTE]


I'm sorry, but I laughed at this.

---

