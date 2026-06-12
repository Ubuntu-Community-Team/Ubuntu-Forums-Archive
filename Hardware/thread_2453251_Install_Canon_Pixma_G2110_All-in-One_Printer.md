---
title: "Install Canon Pixma G2110 All-in-One Printer"
date: 2020-11-06
forum: Hardware
---

### Post by charlie-ramirez-anima-st on 2020-11-06
Hello Team, I have been trying to install my printer for several months. It is a Canon Pixma (G series) multifunctional - G2110, (Apparently in Mexico they are sold with a slight variation by adding an lcd screen to count the number of copies there the "10". So internationally it should be very similar to the G-2100 model)


Although the printer only has drivers for Windows, I know it is compatible with Ubuntu, as in my early days with Ubuntu 18.04 I was able to install it only using the add printers feature in settings. The only driver there was was for the G2010 (so I think I used that one) with not many settings like in Windows but at a decent level. Back then I could only print it, the scanner didn't detect it. in that same time I can also install another Canon g-3100 that I had at my work. With similar results and methods (only it was for Wifi)
However, I did try various distributions in between that time, and finally went back to 20.04. To avoid problems when switching between distributions I decided to format the HDD before going back to ubuntu




So, I tried to "reinstall" my printer, but was unsuccessful, the farthest I've come is that it is detected in the settings but in "generic text-only mode" (by the way, it fails). When I try to search for drivers the window always freezes and I have to force close it. I can only once, select the driver for the G2100 in the settings,
the facility is clean (less than 2 weeks)


. Is there a way to install my printer again (at least for printing) and get the scanner detected as well?
- only connects via USB
I leave you a photo (or what remains) of the printing test sheet from that time, (maybe it will help)[IMG]https://photos.app.goo.gl/swHF4YqPUcpRDovJ9[/IMG] [IMG]https://i.ibb.co/6HZWG3J/IMG-20201106-033936100.jpg[/IMG]

And Sorry the Bad english ppl. I'm not very good at writing in the past tense :-k

---

### Post by brian_p on 2020-11-06
This is a long shot: give what you get for ```
lsusb -v | grep -A 3 bInterfaceClass.*7
```

---

### Post by kurt18947 on 2020-11-07
Let me say I have not installed a Canon printer and our Canon 8800F scanner is plug 'n' play. I have tracked Canon printers because I may need to buy a new printer at some point and Canon seems like a viable choice. It is best to use open drivers if they are available and functional. If not, here is what I would probably try:


[URL="https://www.canon-europe.com/support/consumer_products/product_ranges/printers/pixma/"]https://www.canon-europe.com/support/consumer_products/product_ranges/printers/pixma/
[/URL]Ths one should work with Pixma devices.

---

