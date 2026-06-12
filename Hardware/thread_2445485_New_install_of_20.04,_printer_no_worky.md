---
title: "New install of 20.04, printer no worky"
date: 2020-06-15
forum: Hardware
---

### Post by Extreedoc on 2020-06-15
Upgraded to 20.04 and plugged in my old Epson stylus 680 which I know is good; Gutenprint driver offered and applied and printer showing on the computer, status 'ready'. 
Problem: when asked to print, a little message says: 'Printing', then: 'Printing finished' but nothing happened...? Tried a different printer: Epson D92, same thing. Any ideas? Please bear in mind, I'm not techy but have been using Ubuntu for several years now.

---

### Post by ActionParsnip on 2020-06-15
Is it an Epson Stylus Photo RX680? I can't find an Epson Stylus 680 online......
I found this
[http://www.openprinting.org/printer/Epson/Epson-Stylus_Photo_RX680](http://www.openprinting.org/printer/Epson/Epson-Stylus_Photo_RX680)

---

### Post by Extreedoc on 2020-06-15
No, it's called a 'Stylus Color 680' it's quite old but a driver was offered for it through 20.04
Thanks for your reply.

---

### Post by Extreedoc on 2020-06-16
Nobody? I see twingle93 is having similar issues with his Brother printer; is this unsolvable? What printers do work with 20.04?

---

### Post by gdesilva on 2020-06-17
You may want to check /var/log/access_log for any error messages which may give you some idea what is going on.

---

### Post by slickymaster on 2020-06-17
*Thread moved to **Hardware**.*

---

### Post by Extreedoc on 2020-06-17
Will do and thanks to whoever moved the post to a more appropriate place.

---

### Post by Extreedoc on 2020-06-17
Thank you, as I said: I'm not techy so - how do I access this log?

---

### Post by kurt18947 on 2020-06-17
> **Extreedoc said:**
> Thank you, as I said: I'm not techy so - how do I access this log?

Try var/log/cups. I think you'll find it there.

---

### Post by Kris_M on 2020-06-17
see if this site is of any use for you...
[https://tutorialforlinux.com/2016/06/16/epson-stylus-rx680-rx685-driver-software-for-ubuntu-16-04-xenial-how-to-download-install/](https://tutorialforlinux.com/2016/06/16/epson-stylus-rx680-rx685-driver-software-for-ubuntu-16-04-xenial-how-to-download-install/)

---

### Post by Extreedoc on 2020-06-18
> **kurt18947 said:**
> Try var/log/cups. I think you'll find it there.

Good but - how do I access this log?

Kris_M: Your link was helpful but it seems there isn't a Linux driver for my old Color 680, it _isn't_ an RX680. I have an Epson stylus D92 as well, much newer model and there isn't a Linux driver for it either.
Edit: I have discovered that  my printer is known as a Stylus Color 777 in the US; it is not supported with a Linux driver by Epson. Its Gutenprint or nothing by the looks...

---

### Post by kurt18947 on 2020-06-21
> **Extreedoc said:**
> Good but - how do I access this log?



I was able to just click on it and it opens in a text editor. I must be logged in as a privileged user though. As far as a linux driver, if gutenprint isn't able to help can you find another very similar model that does have a linux driver? Sometimes a printer driver from a very similar model will work. No guarantees of course but when all else fails ...........

---

### Post by Extreedoc on 2020-06-21
Thanks Kurt, I think I will probably end up buying a new printer that will work with Linux. If anybody can suggest such a printer, that will be very helpful; just a basic colour inkjet, nothing too expensive...

---

### Post by The Cog on 2020-06-21
I have a basic colour inkjet printer - it's an HP Envy 5030. I couldn't be happier with it. I used the LCD control panel to enter the wifi password, and it joined. Then I went to printer setup in the Linux GUI and there it was. I didn't even have to click add printer - just set it as the default printer. 
It has an inbuild web server that shows the ink levels and offers the option to scan and download PDF or JPG (no PNG option, sadly).
I went for the cheapest version because I could not find anyone who could confirm compatibility with Linux, and at that price I wouldn't grieve too much if it turned out to be a doorstop: probably give it to my mum. If this one dies, I will probably get a higher spec model in the same range (HP Envy) now I know they work.

Incidentally, a few weeks later, I signed up for HP's Instant Ink subscription - £1.99 plan for 50 pages a month. You can carry some rollover if you don't do 50 one month, and new cartridges just turn up in the post before you current ones reach empty. I guess it depends on yoru usage, but it's about right for me. 

I know this reads like an advert, but it is a genuine comment. I just wish they allowed scanning to png as well. The jpeg artifacts on text scans are annoying.

Edit: That post set me thinking, and I had another go at using the hplip toolbox GUI (from the hplip-gui package). I pointed that at the printer's IP address and I find that it does have the ability to save scans as pdf, jpeg, png or soem web format I'vfe never heard of. The gui is a bit clunky, but save to png is possible. Now, why don't they put download to png as an option in the printer's inbuild web server?

---

### Post by Kris_M on 2020-06-21
as to advert ;) I go with Canon partially because they take non Canon cartridges, and with the TS line because it has better resolution/better print.  I agree, HP, WITH HP cartridges produce/s a fine printout, but way too pricy for me, and using non HP cartridges on an HP printer  is problematic as it will constantly try to "clean" the cartridge and waste a lot of ink. epson, for me, was just an ink consumer. So I stick with Canon - the TS6020 at the moment with easy European drivers for printer and easy way to use its scanner.

Yes, there is a problem with the non-Canon cartridges, sometimes, and I have to be careful of chosing vendor, but works for me.

---

### Post by Extreedoc on 2020-06-21
Thanks for the input The Cog and Kris. Ink cartridges are a big issue for me, I don't do a lot of printing now but I've never bought a genuine cartridge and don't intend to in the future and I always choose a printer depending on whether cheap compatibles are available. Always had Epsons but my wife has a Canon Pixma MP 550 and the compatible cartridges are reasonably priced. (Her Canon doesn't work with 20.04 either...)

---

### Post by Kris_M on 2020-06-21
Yes, always assure there is a driver, like that link I gave you, before you buy a printer for Linux! :) That's what I do. You still can't be totally sure but you will be within return window if you buy from Microcenter or BestBuy or newegg or the like.

---

### Post by kurt18947 on 2020-06-21
HP or Brother. I'm a big fan of Brother for their Linux support. They supply an installer script that has worked perfectly for me. Ignore the "before you install" stuff on their Linux website.  I have refillable cartridges in a MFC-6490CW, made before chips in ink cartridges was a thing. SWMBO has an HL-3170 color laser. Both are connected via ethernet and just work. You can get refillable cartridges that have auto reset chips. Supposedly when you remove the cartridge to fill it, it resets the cartridge to full. I have no first hand experience with them. A trick I recall from reading about them is once the cartridge is installed, do not let the printer do a firmware update. If the printer updates it will no longer recognize the cartridges. 

In theory the new "driverless" printers should be plug-n-play. Even if the printer portion is indeed plug-n-play there's oftentimes a scanner involved. I need both and if the 'magic' fails, it's nice to have a plan B, i.e. manufacturer supplied drivers.

---

### Post by Kris_M on 2020-06-21
"plug and play" printer unfortunately means the very limited CUPS support which is worthless.

---

