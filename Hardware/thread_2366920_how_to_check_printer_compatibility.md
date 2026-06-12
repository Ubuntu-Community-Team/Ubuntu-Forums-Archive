---
title: "how to check printer compatibility"
date: 2017-07-23
forum: Hardware
---

### Post by vegan1 on 2017-07-23
I'm thinking of purchasing one of the new Canon Megatank printers. How do I do research to find out compatibility with Linux?:D

---

### Post by efflandt on 2017-07-23
I found something for Linux web searching "canon megatank printers linux support"
[http://www.canon-printerdrivers.com/2017/05/canon-pixma-g4200-driver-download-mac.html](http://www.canon-printerdrivers.com/2017/05/canon-pixma-g4200-driver-download-mac.html)

But I rarely print and the jets on any ink jet printer would tend to dry up on me. So when my very old b&w laser printer (HP4L) indicated a paper jam I could not find, I used that as an excuse to get a color duplex network color laser printer (Lexmark C543dn, since discontinued) which supports HP PCL and postscript printer languages. So even before it had Ubuntu support, I was able to use an older driver (C534) from same manufacture for it to work fine. No worries about drying out ink jets.

And I also have an X204n all-in-one b&w laser that also does HP PCL and postscript that I bought for $150 to temporarily replace a failed business HP printer at work by simply assuming its IP address without changing any drivers. Although, I have yet to figure out why its scanner driver that works in 64-bit 14.04 (and 32-bit version in 32-bit 16.04 in virtualbox) fails to work in 64-bit 16.04 or 16.10 (maybe due to systemd). So for now I have to use virtualbox to scan, but no printing issues from any Ubuntu since it does postscript.

---

### Post by vegan1 on 2017-07-23
I didn't understand most of that, but I've never evaluated the idea of a color laser printer, based on ink consumption and ink costs and ink and heads drying out. I understood the part about using an older driver. I thought color laser printers were super expensive. Thanks!

---

### Post by cariboo on 2017-07-23
You can check printer compatibility here:

[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

---

### Post by pdc on 2017-07-25
so welcome to the forum vegan1;

Cariboo has kindly pointed you to the Open Source printer drivers; Canon do make drivers; they test them on their machines; so that seems good; 

Canon supply linux drivers for all their inkjet printers: and the same driver they supply drives them all; so that makes it straightforward; to help the different versions of linux, they supply the drivers in 3 formats: source code, and then rpm package; and debian package; Ubuntu uses debian so to install a driver for Ubuntu one would go here;

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100839901.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100839901.html) ...... **[SIZE=4]this is the official Canon site; I would suggest one only uses Canon's site for getting drivers[/SIZE]** ...............

and if one clicks to DOWNLOAD, and selects SAVE then it should end up in your Downloads folder as [COLOR="#0000FF"]cnijfilter2-5.40-1-deb.tar.gz [/COLOR]

to install that if you open a terminal ........ hold 3 buttons down together ...... control alt and t .......and to paste into the terminal; right-click at the text prompt, and look for PASTE in the menu options that appears ......... after each paste into the terminal, hit the ENTER key .....

so one by one the commands to paste are (oh, and please COPY from here  ........ then no spelling errors ........)

```
cd Downloads
```

```
tar -zxvf cnijfilter2-5.40-1-deb.tar.gz
```

```
cd cnijfilter2-5.40-1-deb
```

the last command .......... that is coming up next ....... in a minute ........ runs the install script that should do all the work for you so I suggest you make the terminal ful-screen so you read the questions the script may check with you .............

here is the final command to paste ```
./install.sh
```

______________--

after I write all this, I see this device is AIRPRINT compatible; [http://au.pcmag.com/review/46768/canon-pixma-g4200-wireless-megatank-all-in-one-printer](http://au.pcmag.com/review/46768/canon-pixma-g4200-wireless-megatank-all-in-one-printer) and 17-04 ubuntu has AIRPRINT in it, so my understanding was you would not need to install drivers; 17.04 uses airprint; but you would surely need to have the device accepted by your router; pressing the WPS button ......... you happy with all that stuff?

Indeed, from here, [https://support.apple.com/en-nz/HT201311](https://support.apple.com/en-nz/HT201311) ........ all the Canon G devices are airprint compatible ........... well done Ubuntu again for introducing this into your latest release 

___________

here is a link to the guide Canon supply [http://support-asia.canon-asia.com/contents/ASIA/EN/0302608701.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0302608701.html)

it comes down as guide-pd-5.40-1_en.tar.gz and if you open your DOWNLOADS folder; right-click on this file; select OPEN WITH ARCHIVE MANAGER and then click the EXTRACT button and extract it to your DOWNLOADS folder, then you have a copy there; but the instructions above should get you getting working

---

