---
title: "3D accel on GeForce 420 go (te2100)"
date: 2008-05-25
forum: Hardware
---

### Post by biszkopt on 2008-05-25
Hello. It's known problem with nvidia geForce 420 go on toshiba and sony laptops, the problem is that the only linux drivers available for geForce 4 is desktop drivers, and when you install this drivers on the laptop you will see blank screen [it'll work only when you plug in external display(tested)]. What we can do is install the Nvidia 7185 drivers (dedicated to geForce 1 and 2) in this case your screen will have bad aspect ratio (black strip on the right) it can be fix by adding to device section in xorg.conf line ("option Ignore EDID" "1") but this'll only remove accel from desktop (so it'll be good aspect ratio) but if you turn on the game the black strip will appear so you cant get 3d accel on desktop.:lolflag:


So here is my conclusion: all it is about to change the right geForce 4 linux drivers or xorg.conf  so the drivers use laptop DFP (i think that it must be doable)and i get to the point(the question):
Do anyone have ANY ideas how to do it??

---

### Post by Zeppstar on 2008-07-15
After some hunting, I have been able to get 3d support running without the black strip on the right on the Toshiba TE2100 using 8.04 Hardy 

Following page has the methods and details I used. Please note that I used the hex editor method on the EDID.bin file. I didn't download the supplied .bin file on the following page so I cannot verify it will work.

[http://www.edwiget.name/content/view/144/26/](http://www.edwiget.name/content/view/144/26/)

Although the page specifies Toshiba Satelite Pro 6100, it worked great on the TE2100. And I think its the most elegant solution I have found.

I still need to work out how to get Movie Player working when desktop effects are enabled. Any comments or help here would be appreciated.

 

Zepp

---

