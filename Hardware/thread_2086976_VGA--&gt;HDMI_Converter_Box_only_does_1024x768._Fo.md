---
title: "VGA--&gt;HDMI Converter Box only does 1024x768. Force 1360x768?"
date: 2012-11-22
forum: Hardware
---

### Post by kendoori on 2012-11-22
I purchased a [Monoprice VGA-->HDMI adapter]("http://www.monoprice.com/products/product.asp?c_id=101&cp_id=10114&cs_id=1011404&p_id=6191&seq=1&format=3#specification")  (my Thinkpad X201 laptop only has VGA out). 12.04 displays via the box,  but only gives me the option of 800 x 600, or 1024 x 768. Straight VGA  cable to an external monitor would give me 1360 x 768.  I am sometimes at locations that just have HDMI in for a large screen LCD/TV.

The Thinkpad has an onboard Intel 3000 VGA adapter:  00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

Since my install isn't properly identifying the external monitor resolution because of the converter box (in spite of the display being able to handle it, and the box supporting it), Is there a way  for me to force the external connected HDMI (through the converter box)  to display at higher resolution? the box is capable of running at this  resolution.

I have tried (not in this order):

xrandr --newmode "1360x768" $(cvt 1360 768 60 | grep Mode | sed -e 's/.*"/1360x768/')

xrandr --output VGA1 --mode 1360x768
xrandr --addmode VGA1 1360x768
xrandr --addmode VGA1 1360x768

None of these work...

---

