---
title: "The IBM T23 ThinkPad's annoying integrated Agere 56K WinModem &quot;headache&quot; ..."
date: 2009-10-16
forum: Hardware
---

### Post by BETATEST on 2009-10-16
I've seen a lot of Ubuntu users (escpecially IBM ThinkPad laptop users) ask in the forums how to get their integrated **Agere Systems WinModem 56k** working for dialup internet access and/or faxing.  ](*,)

I've also seen most of these questions go unanswered.

The answer is: *don't bother wasting your time* or efforts trying to make the integrated Agere WinModem work in Ubuntu 9.04. :mad:

The **Martian Agere Systems WinModem software** you commonly read about in the Ubuntu forums ([http://martian.barrelsoutofbond.org/index.html](http://martian.barrelsoutofbond.org/index.html)) is meant to work with the Agere Systems WinModem **PCI modem cards** under LINUX.  I've never been able to get it to work with the IBM T23's Agere *integrated* 56K WinModem under Ubuntu 9.04 - even though the Scanmodem utility says Martian will work with its chipset. I'm not saying that there probably isn't a way to make this work ... but if someone has figured out how to make it work, I haven't seen any details posted how it was done and would be seriously interested in the steps taken to do so. :confused:

The quickest and most sensible way around the Agere WinModem issue (if you want to fax or use dialup on your IBM T23 laptop under Ubuntu) is to obtain either a **US ROBOTICS USR5637 USB modem** or a **ROSEWILL RNX-56USB USB modem**.  8-)  I know - this does not solve the integrated Agere WinModem issue itself.  But in lieu of a solution that probably isn't going to happen, this is a better way (IMHO) to get dialup/faxing than messing around trying to reverse engineer Agere's otherwise mediocre modem product.

These USB Modems are detected by Ubuntu natively because they are true physical **hardware-based modems**, unlike the Agere WinModem which is essentially just a phone jack which requires software to "*emulate*" a modem controller for it to be of any use.

If you have the money, get the US ROBOTICS USR5637. US ROBOTICS actually makes it a point to support linux compatability with this usb modem's firmware and I haven't encountered a Linux distribution that that hasn't natively recognized it out of the box. However, like most US Robotics items ... the USR5637 does come with a pretty hefty price for what is essentially, old 56K dialup technology.

If you're more like me and have to carefully consider anything you purchase, the ROSEWILL RNX-56USB usb modem (roughly half the cost of the US ROBOTICS USR5637) is probably a more price conscious alternative.  It also uses less power off the USB than the US ROBOTICS usb modem.

The one thing to keep in mind is that ROSEWILL itself is *not focused* on Linux compatibility like US ROBOTICS. It's specifically targeted for Microsoft Windows users. However, since it is a hardware-based modem controller following most standards, Ubuntu 8.10 and 9.04 recognize it natively out of the box. This was *not always* the case in Ubuntu 8.04 and some earlier releases (which did not recognize it) and your ROSEWILL compatibility may vary with releases of Ubuntu after 9.04. But for now ... Ubuntu releases 8.10 and 9.04 work just fine with the RNX-56USB for less money.

Since I primarily use a ROSEWILL on my IBM T23 Ubuntu 9.04, I'll describe how I made it "*just work*" for me.

My T23 laptop's Ubuntu 9.04 recognizes it as **ttyACM0**.  

**GNOME-PPP** (Dialup Internet Access): The ROSEWILL RNX-56USB will be detected as DEVICE: ** /dev/ttyACM0**  and TYPE:** Analog Modem**  (*not USB*).  
[COLOR=Blue]
[/COLOR][COLOR=Blue]*Just a Reminder: GNOME-PPP's latest release *still* has a bug where you still have to select REMEMBER PASSWORD (even if you don't want to) when entering your username/password in order to successfully dial and connect.*[/COLOR]
[B][COLOR=Black]
EFAX and EFAX-gtk[/COLOR][/B] (Faxing): Go to **FILE-SETTINGS** and on the **MODEM **tab, for **SERIAL DEVICE** just enter:** ttyACM0**  (*not /dev/ttyACM0* ).

And that's it.  I call the USB modems a "sensible" approach because if you have several computers (Ubuntu or Windows), you can use the USB modem among all of them and you're not stuck with using it on just one system.

So don't go banging your head on the T23's keyboard trying to make your ThinkPad's internal Agere Systems WinModem 56k do something it never really was good at doing even under Microsoft Windows XP (which my T23 originally came with eons ago).  Avoid the annoyances associated with Agere, get a real hardware usb modem, and get on to more important Ubuntu tasks ... like ***Pingus*** or ***Frozen-Bubble***.  

As always ... good luck. :)

---

