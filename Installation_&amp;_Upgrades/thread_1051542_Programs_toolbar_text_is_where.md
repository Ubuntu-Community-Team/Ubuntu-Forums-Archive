---
title: "Programs toolbar text is where?"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by Matt_Rapp on 2009-01-26
I have  Ubuntu 8.10  running on my old C51G-M754 motherboard, [http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?CategoryID=1&TypeID=22&DetailID=581&DetailName=Feature&MenuID=48&LanID=0]("http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?CategoryID=1&TypeID=22&DetailID=581&DetailName=Feature&MenuID=48&LanID=0"), with integrated C51G [GeForce 6100] graphics.

When I run Open Office and some other programs the text on the toolbars and dialogue boxes does not show up. Sometimes if I move my mouse over it it will briefly flash then disappear again. The text of a document that I'm typing shows up just fine.It's always happened in Open Office and happens randomly in other programs. 

I've been forced to use the NVIDA accelerated graphics driver version 96 because versions 173 and 177 both boot to a blank screen after I see the ubuntu boot progress bar and then hear the start up sound. I've also tried using EnvyNG to install version 71 of the driver, but got the same results as before.

What should I do to get my graphics working?

---

### Post by gettinoriginal on 2009-01-26
System > Pref > Appearance > Fonts set rendering to "subpixel smoothing" then go to details set smoothing to "subpixel" and hinting to full. 

That should fix the problem  :p

---

### Post by Matt_Rapp on 2009-01-26
That took care of it!

Thanks a bunch, I thought I was going to have to monkey around forever with the graphics drivers but the  font setting was super easy!!

---

### Post by gettinoriginal on 2009-01-26
You're welcome, and welcome to ubuntu :p

---

