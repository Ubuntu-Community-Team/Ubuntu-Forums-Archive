---
title: "CPU power supply..."
date: 2010-04-23
forum: Hardware
---

### Post by Moozillaaa on 2010-04-23
My board has an 8-pin power input dedicated for CPU power. Manual says that a 4-pin can be used.

My PSU has only a 4-pin connector for this input.

My new build is not POSTing. Only thing I can think of is not enough power to CPU input.

The PSU has a 6-pin power connector for PCI-express/GPU that supplies 75 extra watts. I'm not going to use it. Can I hack it down to a 4-pin, to supplement the other 4-pin in the CPU power input?

PSU is Thermaltake TR2-430W. 

This is the CPU:

> Model Number Athlon II X3 440
    
Frequency     3.0 GHz

CMOS Technology    45nm SOI

Total Dedicated L2 Cache     1.5MB 

Packaging       socket AM3

Thermal Design Power      95W                      

---

### Post by v1ad on 2010-04-23
would work but u got to make sure the voltages are the same and u plug it in right

---

### Post by cascade9 on 2010-04-23
The 8 Pin plug would be for EPS (extra 12volt power). Do NOT try to ue a PCI-e 6 or 8 pin connector- they are not compatible. (and hacking down to a 4pin  PCIe connector wont help either) 

If you think that its the power that is stopping you from booting up, get a Molex (x2) to EPS converter. I really doubt its the issue, if the manual say you can use a 4pin. 

Check this page for more info- 

[http://www.playtool.com/pages/psuconnectors/connectors.html#eps8](http://www.playtool.com/pages/psuconnectors/connectors.html#eps8)

---

### Post by Moozillaaa on 2010-04-23
More good info cascade!

The manual identified the CMOS pins [COLOR=Red]**IN**[/COLOR]correctly. I was trying to boot in CLR CMOS mode.

But still there's the CPU power issue...

Additionally, I could not find locally the molex 4-pin to ATX 4-pin adapter. So I hacked an old ATX connector, to get the 4 ATX's together that match up with the remaining 4 ATX pins input. I used the pic in the link, to determine the 2 molex connector pins.

I checked voltages, and 12V input is good, as is COM/ground.

Like so:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154130&d=1272046683[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154131&d=1272046683[/IMG]

---

### Post by cascade9 on 2010-04-25
> **Moozillaaa said:**
> More good info cascade!

The manual identified the CMOS pins [COLOR=Red]**IN**[/COLOR]correctly. I was trying to boot in CLR CMOS mode.


Argh! I really, really, Really Hate That. Incorrect manuals are a horrible thing. What foxconn board is that anyway? ;) 

> **Moozillaaa said:**
> 
But still there's the CPU power issue...


H...its only a 95watt TDP CPU, I dont think that should need the full EPS connection. If it was a 125/140watt CPU, maybe. Not that my opnion helps you at all, sorry. 

> **Moozillaaa said:**
> 
Additionally, I could not find locally the molex 4-pin to ATX 4-pin adapter. So I hacked an old ATX connector, to get the 4 ATX's together that match up with the remaining 4 ATX pins input. I used the pic in the link, to determine the 2 molex connector pins.


Not suprised that you couldnt find a molex to ATX4 pin adapter- I dont think I've seen one around for a fea years. I cant recall ever seeing a molex to EPS adapter in any shop. 

BTW, if you are still having issues with your setup, I'd pull the memory out and the try to boot it. If you dont get the beeps of 'omg I haz no memories!' then you've had rare, but possible, damage to the motherboard from trying to boot with the CMOS in 'clear'.

---

### Post by Moozillaaa on 2010-04-25
I found out about incorrect CMOS pin ID by a Foxconn tech - he told me the numbering, and I noticed right away, with the board in front of me. It's a A7DA-S.

If I boost clockspeed, would I *THEN* need the extra power?

I got the everything loaded, multiboot, boot from Linux/Windows on PCI IDE controller card ](*,) , working fine, but the POST screen flashes continually as it boots, until splash screen loads.

And now I think THAT is because I tried to boot with CMOS pins in clear position. I saw THAT warning in the manual next to the schematic. Back to Foxconn for a new board?


edit:
Just noticed - BOARD is wrongly labeled too!!!


2 edit:
not the only one either:

[http://www.google.com/search?q=Foxconn+mislabeled+CMOS&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=Foxconn+mislabeled+CMOS&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

[http://www.pricebat.ca/Foxconn-A7DA-S-AMD790GX-ATX-AM2-DDR2-2PCIE-CrossFireX-SATA2-RAID-Audio-Video.p_10081419/](http://www.pricebat.ca/Foxconn-A7DA-S-AMD790GX-ATX-AM2-DDR2-2PCIE-CrossFireX-SATA2-RAID-Audio-Video.p_10081419/)

---

### Post by cascade9 on 2010-04-25
> **Moozillaaa said:**
> I found out about incorrect CMOS pin ID by a Foxconn tech - he told me the numbering, and I noticed right away, with the board in front of me. It's a A7DA-S.

If I boost clockspeed, would I *THEN* need the extra power?

I would say 'no', even with some pretty majr overclocking. The 4pin ATX power has the (theoritical) max of aprox 190watts, and there is also the normal ATX power as well. 

IMO, the reason why a lot of the AM3 boards have EPS if for the upcoming 6-core Phenom II (X6 10XX series) They probably wouldnt need the extra power as well, but it might be part of the specification,  AMD might have some reason for the 8-pin EPS if it is.   


> **Moozillaaa said:**
> 
I got the everything loaded, multiboot, boot from Linux/Windows on PCI IDE controller card ](*,) , working fine, but the POST screen flashes continually as it boots, until splash screen loads.

And now I think THAT is because I tried to boot with CMOS pins in clear position. I saw THAT warning in the manual next to the schematic. Back to Foxconn for a new board?

'flashing' POST screen? Hmm.... I wonder if there is a 'show fullscren logo' or some similar setting in the BIOS, I know I had an older MSI board (forgotten which one) that flashed if you didnt use 'full logo'. 

As long as its booting, its probably not a problem, but yeah, I would worry me if it was my board. 

> **Moozillaaa said:**
> 
edit:
Just noticed - BOARD is wrongly labeled too!!!


They must have changed the CMOS clear arrangement between revisions and the techies forgot to tell the screenprinters and the manual writers (OK, manual manglers if my recall of foxconn manuals is correct). Happened before, with ECS and others IIRC. 

Not good though.

---

### Post by Moozillaaa on 2010-04-25
There is a Foxconn logo screen that can be opted for instead of 'Quiet boot', and 'Quick boot' options , and it flashes also.

Seems that MANY others who had the same problem did not mention flashing BIOS/POSTing screens, so if it's not a BIOS setting that needs adjusting (that I have to 'trial and error'), then perhaps it's a need for BIOS flash.

I can't imagine that hardware is cooked. I never heard crackling or buzzing that electronics does, just before the magic smoke leaves an electronic device :lolflag: . 

Still, we'll have to get the lowdown from Fox tech support on this.

---

