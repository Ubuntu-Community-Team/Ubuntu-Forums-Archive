---
title: "Compatible Laser Printers with Ubuntu 22.04.01"
date: 2023-01-24
forum: Hardware
---

### Post by Quad0 on 2023-01-24
G'day all,

I am in the market for a new laser printer. I had terrible experience with Kyocera which thankfully I was able to send back! 

Could folks kindly mention what sort of printer they run flawlessly with Ubuntu 20/22+ OS?

Thanks.

---

### Post by TheFu on 2023-01-25
What you want is a printer that supports "driverless printing".
[https://openprinting.github.io/driverless/](https://openprinting.github.io/driverless/)
[https://openprinting.org/printers](https://openprinting.org/printers) 

I have a Samsung laser printer from 2008 that supports IPP and works great, but Samsung sold their printer business, so that isn't an option.  During the setup, I pick a slightly different, but related, model.  Every year, I shake the toner to get even blacks across the pages.  I have a spare cartridge here bought about 10 yrs ago, still sealed.  Might have to use it this tax season. 

If you are looking for a scanner too, look for driverless scanners.  My next scanner will allow SDHC or USB flash drives to be connected and will place the scanned files onto that flash memory, no computer connection needed, ever.  If a computer does work, that's a bonus, but I'm tired of having scanners that work for 12 yrs then not again.

---

### Post by Autodave on 2023-01-25
My HP Color Laser worked out of the box: both wired and wirelessly.  I have always had good luck with HPs.

---

### Post by oldfred on 2023-01-25
My black & white only Brother works well. It is both USB & WiFi.
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lpstat -e [/COLOR]
Brother_HL_L2390DW 
Brother_HL_L2390DW_USB

Supposedly all printers work better in 22.04 as some drivers were improved.
ippusbxd is decidedly sub-optimal. Even its author would support your removing it from your system. 
It has been replaced by ipp-usb in later editions of Ubuntu. 

[/FONT]

---

### Post by kurt18947 on 2023-01-27
Check the prospective printer's support info, see if there are Linux drivers available. You may well not need them, see TheFu's post but if there are Linux drivers available I see that as a good sign. I would do some research on HP, they play games with ink where cartridges expire and won't print even if they're nearly full. I don't know about HP lasers, they may be fine. Personally in order of preference:

1. Brother. Hook it up and it works IME.

2. HP if they don't play toner games and will work with 3rd party cartridges/drums

3. Canon. No experience but Canon seems to get pretty good reviews. Check on Linux drivers, perhaps use non-US web sites to check in case driverless printing is not supported.

---

### Post by mark bower on 2023-01-27
Almost a ditto(HL_L2370DW =~HL_L2390DW).  My HL_L2370DW was easily set up to work with 20.04LTS.  Transmits via WiFi, a God Send replacement for my HP Laserjet 4 Plus that I was spending a lot of money on to keep it going.

---

### Post by #&amp;thj^% on 2023-01-27
> **kurt18947 said:**
> 

3. Canon. No experience but Canon seems to get pretty good reviews. Check on Linux drivers, perhaps use non-US web sites to check in case driverless printing is not supported.

I have one that is royal pain in the @@@ on linux.
It's been a few years since I've replaced my Lexmark, but that has been the most trouble free in my use.

---

### Post by TheFu on 2023-01-27
Some canon works and others require paid, proprietary, drivers to work. 
I have a brother All-in-One that worked and was supported for about 10 yrs, then support ended and it doesn't work with Linux.

Go with "driverless" devices.

---

### Post by him610 on 2023-01-27
Several years ago I purchased a refurbished Brother MFC-7360N B&W laser from Staples for about $100. It originally cost over $300. It prints, copies, scans, and sends/receives faxes. If it ever craps out on me, I will buy another Brother MFC device. Drivers are available for download at the Brother website. Brother installation procedures are well documented.
I also have used a Dell 1700N B&W laser printer for about 15 years; it still works fine. It uses generic laserjet drivers found in CUPS.

Good luck.

---

### Post by #&amp;thj^% on 2023-01-27
> **TheFu said:**
> 
Go with "driverless" devices.
When a replacement is needed on my end, that's the route I'm going.

---

### Post by SeijiSensei on 2023-01-28
I have had a Brother [https://www.brother-usa.com/products/hl3170cdw](https://www.brother-usa.com/products/hl3170cdw) for over a decade. Works flawlessly, though I don't do a lot of printing. Brother devices are well-supported in Linux. Recommended.

Here's the successor model: [https://www.bestbuy.com/site/brother-hl-l3270cdw-wireless-color-laser-printer-white/6265819.p?skuId=6265819](https://www.bestbuy.com/site/brother-hl-l3270cdw-wireless-color-laser-printer-white/6265819.p?skuId=6265819)

I hard wired the printer into my router and assigned it a static IP address. Can print to it directly from every device on my network.

---

### Post by mIk3_08 on 2023-01-28
> **SeijiSensei said:**
> I have had a Brother [https://www.brother-usa.com/products/hl3170cdw](https://www.brother-usa.com/products/hl3170cdw) for over a decade. Works flawlessly, though I don't do a lot of printing. Brother devices a re well-supported in Linux. Recommended.
 Same here. I do have a network DCP Brother Printer and works smoothly to my Ubuntu 22.04 LTS wirelessly. I have this for many years now. It works since I start using Linux Ubuntu 16 until now. It also work with driverless configuration. Regards and cheers.

---

### Post by Quad0 on 2023-01-29
Looking at ordering[SIZE=2] Brother HL-L3230CDW...[/SIZE]

---

### Post by kurt18947 on 2023-02-01
> **SeijiSensei said:**
> I have had a Brother [https://www.brother-usa.com/products/hl3170cdw](https://www.brother-usa.com/products/hl3170cdw) for over a decade. Works flawlessly, though I don't do a lot of printing. Brother devices are well-supported in Linux. Recommended.

Here's the successor model: [https://www.bestbuy.com/site/brother-hl-l3270cdw-wireless-color-laser-printer-white/6265819.p?skuId=6265819](https://www.bestbuy.com/site/brother-hl-l3270cdw-wireless-color-laser-printer-white/6265819.p?skuId=6265819)

I hard wired the printer into my router and assigned it a static IP address. Can print to it directly from every device on my network.

Same setup, ethernet from the router and static I.P. assigned to the printer. I've never had an incident where the printer was not found upon sending a print job, which seems to be a common complaint, especially with wifi. I also make sure the app "system-config-printer" is installed. It can be launched from the terminal or from the alt-F2 command box.

---

### Post by iamjiwjr on 2023-02-01
Ditto.

---

### Post by mark-chandler on 2023-02-01
Been really happy with my Brother MFC L2750DW on 22.04.1 (as well as Linux Mint).

---

### Post by r.stiltskin on 2023-04-05
> **mark-chandler said:**
> Been really happy with my Brother MFC L2750DW on 22.04.1 (as well as Linux Mint).

Have you been able to get 2-sided scanning to work in Linux?  I just got a Brother MFC-L2750DW. No problems with printing or single-sided scanning, but I can't get duplex scanning to work from Xsane or scanimage, or from the printer's own touchscreen using its "scan to pc" function.  (2-sided scanning does work in Windows 10, but that's a fallback I don't like to use.)

---

