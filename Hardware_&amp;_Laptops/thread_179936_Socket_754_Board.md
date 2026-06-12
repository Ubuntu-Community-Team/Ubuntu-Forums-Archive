---
title: "Socket 754 Board?"
date: 2006-05-21
forum: Hardware &amp; Laptops
---

### Post by flyingbrass on 2006-05-21
I'm selecting parts to assemble a budget browsing/e-mail/office/light gaming computer for a relative.  I plan to use a socket 754 board and a Sempron (probably 3100+).  It doesn't have to be wonderfully overclocking friendly, but I intend to crank it up a few notches.  She'll be running Dapper.

I haven't decided whether to go with onboard video or a cheap AGP card.  I'm disgusted with ATI's Linux support, so I'm planning on an nVidia something or other.  While not into heavy gaming, she was impressed with compiz/XGL and will likely use it later.

Does the integrated GeForce 6100 work well in Dapper?  Or would I be better off with an AGP board and an inexpensive card like a Ti4200 (8x, DVI and video out, still available new for ~$30)?  Are there any non-ATI PCIe cards as good for this intended application for about the same price?

Do you recommend any specific 754 boards?  If you're using one, what issues if any have you encountered?  Compatible onboard NIC and sound are important due to budget constraints. 

Also, how well does Dapper install to SATA drives? A year or two ago SATA installations in Linux weren't always smooth sailing.  Maybe that has been sorted in more recent kernels.  I'll probably use a PATA drive, but I'm keeping an eye out for sales and wouldn't want to needlessly pass up a good deal.

Some of the boards I've been considering are: Asus K8N-E, Biostar TForce6100, Abit NV8.  Fry's/Outpost has had some cheap combo deals with ECS boards, but I'm wary.

Suggestions?  I have searched, but most issues I've found for various motherboards (no DRI for 6100, unsupported or flaky NIC and sound drivers) were older and may no longer exist.

---

### Post by bigken on 2006-05-21
Hi would take a look at this board 
[http://www.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=1950&ProductName=GA-K8N51GMF]("http://www.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=1950&ProductName=GA-K8N51GMF")

---

### Post by flyingbrass on 2006-06-24
Because I get disgusted when posters asking questions don't follow up with results or resolutions:

I went with the Biostar Tforce6100.  Video (with the nvidia driver -- it's only that or vesa), works fine with Dapper.  Onboard sound does too.  

I haven't tried onboard LAN.  I stuck in a network card I had handy.  

The 3100 Sempron (palermo) is running at 2574 MHz stably with only a slight voltage boost, and that may not even be necessary.  It ran the mprime torture test overnight without a hitch and topped out at a cool 42 degrees C.

---

