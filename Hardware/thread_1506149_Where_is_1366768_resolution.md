---
title: "Where is 1366*768 resolution?"
date: 2010-06-10
forum: Hardware
---

### Post by Kdar on 2010-06-10
I have put together a media PC few weeks ago. Today I tried to connect it to my 46" LCD TV by HDMI cable.

When I had it connected by HDMI, I could not set correct resolution in Nvidia settings (correct one is 1366*768, and I can only set on 1360*768 ). Additionally this resolution looked "zoomed in" and all screen edges were cut off, so I wasn't able to see both panels and sides were cut off as well.

Than, I tried to connect PC and TV by VGA cable. When I did that, I got correct resolution, 1366*768, and it looked perfect, nothing was cut off. But of course I want to use HDMI.

After that I discovered something else. I was back using HDMI again. In Nvidia settings I found option for overscan compensation. When I selected this, I was able to "zoom out" resolution, so that there will not be any cut offs on any sides. It worked, but not 100%, since resolution was still different (1360 and not 1366). Because of this, when I did overscan compensation, there was a small black line (of several pixels) on very top.

How can I enable 1366*768? so make it work 100% correctly.

---

### Post by Kdar on 2010-06-10
anyone?

---

### Post by Darris on 2012-09-21
Are you using a TV instead of a monitor? 
Some TVs only work with 1366x768. That's not possible, at least with Nvidia cards because they need resolution to be divisible by 8. That's why you don't have the problem on HDMI.
I don't know how to help you get it, but on Nvidia driver configuration GUIs there SHOULD be an overscan compensation slider.
There's not one on mine. I'm probably going to make a post soon lol

---

### Post by prstine on 2013-03-04
I have had the same problem with my 8400 GS Nvidia card. When connected via VGA the screen resolution is correct, 1366 X 768. When connected via HDMI with a DVI to HDMI connector the screen resolution defaults to 1280 X 720. When using HDMI I don't think the TV is able to transmit display size information back to the video card. I have heard you can manually edit the x.org config file. Not sure how to do this though.

---

