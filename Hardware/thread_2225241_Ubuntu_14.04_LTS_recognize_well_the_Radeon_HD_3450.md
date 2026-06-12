---
title: "Ubuntu 14.04 LTS recognize well the Radeon HD 3450 AGP edition?"
date: 2014-05-20
forum: Hardware
---

### Post by nicko2 on 2014-05-20
Hi, thanks for Ubuntu and this forum, this is my firt post and I wanted to thanks first :). 

My pc is a **AMD Athlon XP 2600+**, my graphic card is the [Club 3D Radeon HD 3450 AGP Edition with 512MB]("http://www.club-3d.com/index.php/products/reader.en/product/radeon-hd-3450-agp-edition.html"),   
at this moment I have Ubuntu 12.04 LTS installed

I followed many posts and instructions to could do my Radeon 3450 works with Ubuntu 12.04, so many that really I didnt remember it now, it was some months ago, even I tried to install 12.04.2 and 3 but could not do it works well in that versions, it had graphical artifacts and didnt works well. Although now in the info of the Ubuntu configuration doesnt appears the name of the graphic card, but at least works.

I never asked in the forum but now that Ubuntu 14.04 has been released Im thinking in format my pc and install it to see if Ubuntu recognize the Radeon HD 3450 AGP. Im not sure if the problem is a compatibility with the AMD Athlon XP 2600+ or the graphic card model is old and will no works with Ubuntu 14.04

---

### Post by Mark Phelps on 2014-05-20
AMD dropped restricted video driver support for your card last Summer, so now, there are no proprietary video drivers that will work with your card and any Ubuntu newer than 12.04.1.  The default Radeon drivers work, however -- but if you go hunting around for AMD drivers and force their install, you will  trash the video and have to remove them.

---

### Post by QIII on 2014-05-20
Also, if you follow the instructions many give for hacking around that, you will effectively break your system with indeterminate results.  Those hacks apply kernel patches, downgrade X Server and install an older proprietary driver.

I have had to help at least half a dozen people undo the damage.

I [B][I]highly recommend against using any of those methods.

[/I][/B]If you really want to use that card with the proprietary driver, you will need to do a clean install of 12.04.1 or earlier.  12.04 is supported until 2017, so you have plenty of time to enjoy it.

Otherwise, continue to use the default open source driver installed with Ubuntu.  It has gotten substantially better over the years and ATI has helped the open source developers with it.  You can improve performance by installing some of the mesa packages.  I'm not at home, so I don't have the package names handy.

---

### Post by Yellow Pasque on 2014-05-21
Try a Live CD/USB of 14.04 before you install it over your current install...

---

### Post by nicko2 on 2014-05-21
thank you all for the answers. 

yeah I think before I finally did and installation with the 12.04 version I tried doing many changes with the 12.04.3 and 2 to try to do the graphic card works properly, really I got the graphic card some months ago, my pc is too old and doesnt support a PCI Express card and I forgot that that card model really was release many time ago and before I bought it I should have done a research to see if it had update of drivers, was my fault, but after I installed the 12.04 it finally works well :) like all others Ubuntu versions I had before. After I started with Ubuntu I liked I had not dip in the box of drivers in each installation any more :)

---

### Post by mastablasta on 2014-05-21
i can tell you first hand that PCI version works ok with 14.04. i believe the guide is not that important as it is the chip support. if drivers support the chip it will work. AGP will have slower transfer than PCI express. 

i had an old AGP card (ATI 9600) and old DDR1 RAM. well i found a relatively new motherboard at the time with both PCIe and AGP slots and both DDR and DDR2 ram slots. so i bough it and installed. i added dual Core CPU (celeron, if i had the money i would buy iCore. well it all work there appart from sound occasionally. and i am still not sure if this is driver/OS issue or if i wired something incorrectly. the frame is really strange with excess wiring coming out.

---

