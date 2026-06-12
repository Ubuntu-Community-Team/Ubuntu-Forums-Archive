---
title: "Do I need an Internet connection to install printer drivers?"
date: 2008-05-17
forum: Hardware
---

### Post by Mr. Picklesworth on 2008-05-17
Edit: Duh I need it to install printer *drivers*! I mean "do I need an Internet connection to install printers from a complete Ubuntu Hardy setup?"

Incredibly obvious question here that should be answerable in about 10 seconds by someone with direct access to a printer.

I have volunteered to help with something for a community organization, and this task involves lots of printing. (And spreadsheets). Naturally, I hope to use Ubuntu so that this is to my advantage; at least one person (whoever is helping me) will get a bit of exposure to free software, bringing my plan for world domination one step closer. Here's the kicker: There is no Internet connection and I will not see the printer up close until the day of. It would be most unfortunate if I had to use Windows Vista due to printer issues.
The printer is a Canon Pixma MP130. (I may have to get my hands on another printer anyway, since it's not a good printer for the ammount we will be pushing through it...)

Will I be able to just plug this in to USB and have it work (just text; no need for fancy colour profiles or anything) without Ubuntu wanting the Internet? If not, how can I download the right stuff in advance?

---

### Post by EXCiD3 on 2008-05-18
Try it and see. I dont think you will need an internet connection to install the drivers. Just go to the Printing applicatoin add the printer. I didnt need it when i installed my HP printer drivers.

---

### Post by Mr. Picklesworth on 2008-05-18
Thanks, EXCiD3!
It's a trivial thing, but I'm giving you a little medal for being in the support forums and answering silly questions like this :)

Okay, I convinced it to install a printer for a device that doesn't exist and it got as far as testing the thing (then moaning about the device not being there), which indeed suggests it does not need a connection. Yay!

Bad news is that the MP130 driver is unavailable, so I am going on tips to use ip1500 driver (also not easily available) or bjc7000 / bjc 800 drivers. Completely winging it now...

---

### Post by EXCiD3 on 2008-05-18
Haha, thats what im here for. Answering those questions helps keep a lot of people from just diving right back into Windows because they cant get one little thing to work in Linux so they give up all hope. But i like to think i help put a stop to that. ;)

Heres a quick little tutorial i found online for setting up that printer:
> 
If you want to install Canon PIXMA MP130 Printer  follow this procedure

Add the following to the /etc/apt/sources.list:
  

  ```
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./
```Then in terminal:
  

  ```
sudo apt-get update
```Then:  
  

  ```
sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
```Cupsys will be automatically restarted and you can select printer in cupsys configuration which is (should be able to open in firefox i think)
   

  ```
http://localhost:631
```To add the printer through the cups, the first thing you do is click on add a printer. The next screen will ask you for the name of you printer, location and description. The only thing you really have to fill in is the name anything you want will do. After you have filled in the information click continue. The next page asks you to select your printer which should be Gutenprint USB Printer #1 (Canon MP130). Hit continue and then it will ask you for your driver. Select the Canon Pixma iP1500 Ver.2.50 (en) then click on add printer. Printing a test page should work! I've used the method on both Gutsy and Hardy.

Source: [http://ubuntu4life.com/aggregator/Only_Ubuntu_Linux/2008/04/20/HOWTO__Install_your_Canon_PIXMA_MP130_Printer_using_the_iP1500_Printer_Driver](http://ubuntu4life.com/aggregator/Only_Ubuntu_Linux/2008/04/20/HOWTO__Install_your_Canon_PIXMA_MP130_Printer_using_the_iP1500_Printer_Driver)

---

### Post by Mr. Picklesworth on 2008-05-18
Unfortunately, [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) gives me error 403. There is a [wiki page]("https://wiki.ubuntu.com/CanonPixmaIP1500") on setting up ip1500 which I will step through some day.

---

### Post by EXCiD3 on 2008-05-18
Ah, sorry about that, i didnt check the link. Looks like his instructions are still up but the ubuntu repo isnt there anymore: [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

Also if you are using 64 bit it looks like not even compiling from source will work. Sounds like you got a printer with awful linux support. :(

Just in case: [http://ubuntuforums.org/showthread.php?t=487890](http://ubuntuforums.org/showthread.php?t=487890)

---

### Post by Mr. Picklesworth on 2008-05-18
That was lucky! Thanks for the heads-up.
A quick search took me to this:
[http://ubuntuforums.org/showthread.php?t=593414](http://ubuntuforums.org/showthread.php?t=593414)

Worth a shot. However, I think it may be worthwhile to find another printer :O

---

### Post by EXCiD3 on 2008-05-18
Yeah probably so. HP printers have good linux support, dont get with epson as i read that they have programmed into their software a 3 year lifetime for THE PRINTER. HP's have protection against refillable ink cartridges and most cartridges have only 1000 page lifetime, not meaning 1000 uses of that color...1000 pages...you should def look up info on the companies first. they have all these little tricks they use to squeeze moeny out of customers...its truly an awful practice. :(

Good luck with that tutorial!

---

