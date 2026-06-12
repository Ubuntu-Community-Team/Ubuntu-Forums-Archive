---
title: "xgps kills USB GPS ? - a cautionary tale"
date: 2009-03-17
forum: Hardware
---

### Post by overandunder on 2009-03-17
Hi

I recently bought a USB - serial GPS mouse (PL2303 Sirfstar III chipset).  Which I wanted to use with a piece of navigation software called Seafarer from Barcosoft.  At the same time I also installed xgps.  

Eventually I got this to work.  However, after about an hours use (while using xgps) the LED on the GPS unit went out, never to return!

I returned the unit to the vendor, thinking I had a faulty piece of hardware.  

A week goes by and the unit is replaced.  I plug the replacement in, light comes on, xgps is started and all seems ok, I'm reading satellites just fine (light flashing on GPS means I have a satellite fix).

However, five minutes later, xgps hangs, the light goes out and I have another dead USB Mouse!

Can anyone tell me if there is any possibility that xgps is switching the GPS off somehow, or is it just 'killing' it?  Is there anything I can check before throwing mouse number 2 in the garbage?

System is Ubuntu Intrepid Ibex.  Unit was connected to a good USB port /dev/ttyUSB0 (the same port has a digital camera attached to it from time to time without a glitch).

Thanks

---

