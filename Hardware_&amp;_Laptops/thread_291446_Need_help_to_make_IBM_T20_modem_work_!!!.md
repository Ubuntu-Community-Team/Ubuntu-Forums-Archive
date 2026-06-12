---
title: "Need help to make IBM T20 modem work !!!"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by CEDRIC22 on 2006-11-02
Hello every body,

Please, can anyone help me make the modem of my IBM Thinkpad T20 work under Edubuntu 6.1 ???

In fact, I have received a donation of 15 laptop that should be shipped from Switzerland to Lebanon for schools that are being rebuilt and re-equipped after last July war and for tons of positive reasons, I decided to load on them Edubuntu 6.1 instead of windows ...

The problem so far is making sound and modem function depending on the thinkpad type.

I can say for the moment that Edubuntu 6.1 works 100% fine on the IBM thinkpad 600X model, I mean not one single hardware problem.
Info just for those who are interrested to know.

Another info, the T20 has a screen problem when first time loaded and you can resolve it very easy by following what Matt has written in his thread:

1.When the computer is booting up, enter the GRUB bootloader and select the "recovery" option.
2.After the system is fully loaded and you are presented with a command prompt as root, type "dpkg-reconfigure xserver-xorg" to enter the configuration utility.
3.Have the utility attempt to autodetect the card (for the T20, it should autodetect to the Savage driver).
4.Continue through the screens selecting the default values until you reach the screen telling you to "Enter the amount of memory (in kB) to be used by your video card." on the line, type "8192", because the T20 savage video card is an 8MB card... 8 x 1024kB. This is the critical step in getting the graphics to load correctly!
5.Continue selecting default values until you reach the screen where you must select "Easy" "Medium" "Advanced" or something regarding the way you will set the refresh rate. Select "Medium", and then on the next screen select "1024 x 768 @ 75 Hz"
6.For color depth, select "24".
7.Continue hitting "OK" through the wizard until you are dumped back to the command line. Type "telinit 6" to restart the computer. Let the computer boot completely, and you should see graphics!!!

That's it! Hopefully this helped somebody whose video memory wasn't detected correctly.

Matt

---

### Post by Mark Stosberg on 2006-11-02
This modem is supported Linux. 

See [Installing the Ltmodem drive for Mandriva]("http://www.thinkwiki.org/wiki/Installing_Ltmodem_driver_for_Mandriva").

I know it's not Ubuntu-specific, but I think it will get you headed in the right direction. 

Good luck with your project! Edubuntu sounds like a good choice. 

  Mark

---

