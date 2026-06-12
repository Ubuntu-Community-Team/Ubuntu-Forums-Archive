---
title: "Epson SX-435w setup on 11.10 and iPad"
date: 2012-03-25
forum: Hardware
---

### Post by owend on 2012-03-25
I just got an Epson SX-435w printer (half price at Tesco!:p). Good little machine, small footprint for my crowded desk, and I'm pleased with it so far, but it didn't work out-of-the-box for me (the Copy function worked - should have, it's PC-free copying). I took about three hours off and on to get it working, so here's a tutorial to let you do it in 20 minutes! You need the lsb package, version 3.2 or up – version 4.0 already with Ubuntu 11.10, or it's available in the repositories.

Two caveats: I don't use wireless (hard-wired from the computer via USB), and I don't think I'll ever print photos direct from a card although the printer has a card slot, so I haven't set these two functions up.

**Printer**: I'm on Ubuntu 11.10 32-bit (there are different files for 64-bit but on the same pages). You can get the printer driver from [http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/) Find the printer (about halfway down the list, or use the search/find command) then download the right file (for me, epson-inkjet-printer-201105w_1.0.0-1lsb3.2_i386.deb); open with gdebi. This puts the PPDs for **seven** printers in Opt/epson-inkjet-printer-201105w/ppds/Epson.

I think the ejecting-unprinted-pages scenario that some people have experienced (including me at first) is caused by the system using an incorrect driver from that folder. Go to CUPS (localhost:631), then go to CUPS for administrators>Adding printers and classes>Manage printers. Click on Epson-Stylus-SX430>Administration>Modify printer>click Continue>click Continue again>under “Or Provide a PPD File” click Browse and navigate to Opt/epson-inkjet-printer-201105w/ppds/Epson, then click on Epson-Stylus_SX430_Series-epson-driver.ppd.gz. Robert's your mother's brother, all printing works!

For the **scanner** you need iscan: go to [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo) then find the SX-4325w as before; check the button and answer the two-question survey! Then, download the data package first (iscan-data_1.13.0-1_all.deb), then the core package (iscan_2.28.1-3.ltdl7_i386.deb). Open both with Gdebi. Scanner now works too!

As I said, I don't use wireless – hardwired to the printer – but there's a network driver for iscan, which presumably gets wireless working.
 
For the **iPad**: The SX-435w isn't an AirPrint printer (to be fair, no-one's claimed it is), but get the free Epson iprint app on your iPad. Open it and you can print several areas directly (webpages, and photos stored on the iPad notably) - you can also scan from the printer direct to the iPad. Some apps allow you to save output as a photo, which you can then easily print from iprint; one or two allow you to “save” the file to iprint then print, but you seem to not save the file in iprint, just in the original app. I don't intend to print much from my iPad, but with the iprint app you get at least some options – if you print much from your iPad, explore further and let us know!  

Hope this helps someone!

Owen

---

