---
title: "Compatibility issues?"
date: 2009-08-13
forum: Hardware
---

### Post by ThAt0n36Uy on 2009-08-13
OK, a quick summary of my issue before I give all the information. I just bought a Hanns G 21.5 Widescreen HDMI LCD off of newegg the other day. Shipped here, and set it up for my Xbox 360. Which all was fine and great, until now when I decide to hook it up to my Desktop.

It does display the desktop, but I'm having resolution, font rendering, wallpaper, etc issues. The last one isn't an issue I just need some understanding with it. OK so, now on to the info.

[LIST]
[*][Dell Dimension 2350](http://support.dell.com/support/edocs/systems/dim2350/specs.htm#1101572)
[*][Sapphire Radeon 9250 256MB GFX]("http://www1.sapphiretech.com/en/products/graphics_overview.php?gpid=59")
[*][21.5in Hanns G HDMI Widescreen LCD](http://www.newegg.com/Product/Product.aspx?Item=N82E16824254039)
[*][17in MAG Innovision LCD](http://www.maginnovision.com/Products/Product.aspx?sn=465&pi=1459)
[/LIST]

So my issue is the resolution on the new widescreen. There are no 16:10 resolutions, the max is like 1440x900, which isn't near the max on the LCD(1920x1080), and doesn't look good at all. The LCD came with some install disc, but because I don't use windows I didn't pay much attention to it. I assumed really that it would just be plug and play. 

I also thought that it might be because my gfx card is so old. That maybe it can't support that size resolution. I really would like to see my Linux install in full living color.

---

### Post by sergiom99 on 2009-08-14
Maybe some of these might help:
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=SAPPHIRE+9250+&sa=Search&cof=FORID:9#941](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=SAPPHIRE+9250+&sa=Search&cof=FORID:9#941)

---

### Post by Bucky Ball on 2009-08-14
Old card could be the problem. See if you can get the specs on the card and that will nail it immediately if it can't achieve that resolution.

---

### Post by Yellow Pasque on 2009-08-14
The Radeon 9250 should do up to 2048x1536. Maybe post your /var/log/Xorg.0.log

---

