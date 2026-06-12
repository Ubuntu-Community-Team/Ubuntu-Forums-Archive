---
title: "Upgrading screen panels on Dell Latitude 7490 - need part number"
date: 2019-02-22
forum: Hardware
---

### Post by AnotherBrian on 2019-02-22
I picked up a i5 Latitude system 7490 on the cheap.  Unfortunately the laptop came with a rather poor FHD matte screen. The part number (not really a dell part number) is NV140FHM-N47.   There does appear to be other screens that dell sells with this system but their sales literature does not indicate the parts number nor can you figure out the quality.  The panel was easy to remove and uses a 30 pin eDp connector. The back cover to the 7490 clearly is designed to support other screens (e.g., 4 and 2 screw panels). 

I prefer gloss but looks like dell markets this one in matte only unless its touchscreen.  I'd be open to throwing in touchscreen but I think it uses different backcover and hinges.   (I changed out a cheap matte on e7270 with a touchscreen assembly before and that ran just fine.)  

I see ebay china products claiming to be dell products for qhd touch for e7480 line.  I'd be open to getting that but I suspect dell changes their hinges for each generation so as to make it difficult to interchange parts.  

So upgraded FHD matte will suffice but I'd be open to better upgrades.   Any suggestions on figuring out candidate upgrades and assessing quality?  It looks like many panels can be used. 

panelook.com seems like one of the best websites to see photos of some panels. 

I'm not concerned about lost of warrantee on this product - just want a decent screen.  I'm thinking I'm just to early in the product cycle on this laptop and have to wait a bit for a used parts market to develop for this laptop.

---

### Post by AnotherBrian on 2019-03-16
success! very easy install. huge improvement. 

to remove panel, use guitar pick type of device to remove bezel on the display assembly.  remove 2 screws that hold panel to display assembly,  finally disconnect edp connector from panel. 

the old FHD panel is matte nv140fhm-n47 with 262k colors using 30 pin edp connector. 
the new FHD panel is glossy  b140han03.3 with 16.2m colors on ebay for $60. 

upgrading to qhd non-touch may be possible all in the same display assembly but it was to much of a leap for me to try this.  candidate panel is  b140qan01.2 which uses 40 pin edp for $85.  qhd cables are available for $20 on ebay. 

i think but am not certain that 7480 and 7490 use the same parts for their displays, that being hinges, cables, cameras, antennas. 
the touch screens use different lid covers compared to my fhd.  it would be more involved to upgrade to touch since lid cover change out will require moving camera and antennas over to new lid.  

oops i probably broke the warrantee

2 separate issues are: 

ISSUE 1:  7490 does not allow booting from a non efi (secure) internal drive.  this means legacy bios doesn't work for internal ssd.  it is no longer possible to move an ssd with ubuntu from one machine and plop it into the new machine.  i don't know how to install ubuntu via efi secured. yet. 

ISSUE 2: I've been looking for a laptop upgrade from my e7450.  the e7x50 line by dell used msata which is a different form factor.  it appears like there is enough room in the 7490 to use an msata to m.2 adaptor.

---

### Post by AnotherBrian on 2019-03-28
Oops - I reported wrong: b140han03.3 is a matte. 

msata ssd worked!  i tried the single (all one piece color green)  msata ssd to m.2 adapter and its too tight of a fit.   The 2 piece adapter (color black with ribbon cable) worked.  The part that connects to msata sits a little under the battery and also under the m.2 connector part.  The ribbon cable winds around a bit.  I suppose there could be a heat issue but we will see.   

converting from legacy bios system ssd to efi secure boot system  was met with limited success.   boot-repair utility is suppose to be able to make the conversion from non efi to efi. I did achieve limited success in that the "repaired" drive would start grub in efi mode.  But no os would load up.  I think it was doable at that point but I didn't want to go through the learning curve of getting ubuntu up from grub.    So I did a copy of the legacy system to another drive, fresh ubuntu install, and then copy back of user data.  ubuntu liveusb knows how to install on efi - all automatic.

---

### Post by fubofo on 2019-09-09
> **AnotherBrian said:**
> success! very easy install. huge improvement. 
...
the old FHD panel is matte nv140fhm-n47 with 262k colors using 30 pin edp connector. 
the new FHD panel is glossy  b140han03.3 with 16.2m colors on ebay for $60. ...

I also am in the process of trying to replace the 1366x768 TN panel in my Latitude 7490. I purchased an InnoLux N140HCE-G52 1920x1080 IPS panel which uses 30-pin connector. However, when I connect the panel only the backlight seems to flicker for half a second, every 1-2 seconds. Would you have any idea about this?

---

### Post by moonbear on 2019-09-23
> **fubofo said:**
> I also am in the process of trying to replace the 1366x768 TN panel in my Latitude 7490. I purchased an InnoLux N140HCE-G52 1920x1080 IPS panel which uses 30-pin connector. However, when I connect the panel only the backlight seems to flicker for half a second, every 1-2 seconds. Would you have any idea about this?

Did you ever figure this one out?  I've run into the same issue. Replaced a 1366x768 with an fhd, and just get back light - nothing else...

**UPDATE**:  I '*think*' I found the issue.  The video cable is a 30-pin - fine, this fits the new LCD I wanted to swap for (assuming you're in the same boat), only lighting up the screen.  But, I'm pretty sure it's a 'single lane' HD cable, whereas FHD required '2-lane or eDP'.  In short, I think it's the cable.  I haven't found anything in a 30-pin for the 7490 that supports fhd (searching for parts) - only the original cable, and a touchscreen fhd one using 40-pins (which won't work for the lcd I already got).

I would definitely be grateful if anyone knows of an alternative cable, as I'd rather not have to order a touch screen replacement - especially not knowing 100% that it would actually work...

---

