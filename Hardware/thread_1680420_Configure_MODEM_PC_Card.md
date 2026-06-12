---
title: "Configure MODEM PC Card"
date: 2011-02-02
forum: Hardware
---

### Post by borgward on 2011-02-02
How do I configure PCMCIA MODEM card. Ubuntu 10.04 Dell Inspiron 1520 laptop.

Let me preface this by saying we are having electrical blackouts, so can not get online w/dialup w/o electrical power to my Linksys router which is connected to my USR external MODEM.

I have 2 different cards that work w/Linux one is a 3Com U.S.Robotics Model 3056. The other is a card for Mac thst I have used w/Linux it is a Global Village PowerPort Platinum Pro
Model A930

---

### Post by gordintoronto on 2011-02-02
From the USR 3056 user guide: "To install your modem you must be running Windows 95, Windows 98, or Windows 2000." It's a Winmodem, and I have read about a project to support Winmodems in Linux - but I have no hands-on experience. 

Ten years ago I was heavily into modems, but in the past six years I have only used a modem three times, and that was to send faxes. Even 10 years ago, I avoided Winmodems.

This might help you with the Global Village unit:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

If you need to install software, you can get it from packages.ubuntu.com

---

### Post by borgward on 2011-02-03
"To install your modem you must be running Windows 95, Windows 98, or Windows 2000." I am guessing that they were not considering Linux at that time.

It's a Winmodem, Are you sure? What is your source of info? Remember that Hardware MODEMs work w/Windows as well as Linux and Mac.

The 3 Com 3056 is listed at [http://xmodem.org/modems/pcmcia_list.html:](http://xmodem.org/modems/pcmcia_list.html:)

3Com Model 3CXM356B/3CCM356B, 3CXM756/3CCM756, USR Model 3056/3057, TI chipset, ADI chipset [3056/3057]

I have used both cards in my Dell Latitude CPi running CentOS and then Debian. I definitely did not use a wrapper or do anything else out of the ordinary for them to work.
--------
Maybe I am asking the wrong question.

Assuming that they are real MODEMS, Hardware MODEMS, and not WinModems, Will Ubuntu 10.04 work with them? I did shut down my Inspiron laptop and insert the cards, but Nothing happened on reboot. No "New Hardware" message.

Put another way, If I had Ubuntu installed on a desktop computer w/a PCI hardware (not WinModem), would Ubuntu 10.04 recognize it?

---

### Post by gordintoronto on 2011-02-03
Wow, my source of information was:
[http://www.usr.com/support/3056/3056-ug/](http://www.usr.com/support/3056/3056-ug/)

It appears USR had two different 3056 modems.

Ubuntu can use a real modem, I have a friend who only has dial-up Internet access. It's not the easiest thing you have ever done:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by borgward on 2011-02-04
I think it is really poor that Ubuntu does not configure modems during installation or when it sees new hardware. I remember that one version did, but forget which. It is important to have a Dialup option, in case one is in the hinterlands or any where there is not anything else available.

I took a look at the DialupModemHowto, but that looked like way to much trouble, and iffy to deal with, but thanks for the link anyway. It might come in handy someday.

I will probably Boot up Puppy, DSL, or a similar live disc that will work w/MODEM if I need to use the phone line. I forget which one will do it.

You can find if a MODEM is a hardware, or WinModem by Googling model xyz chipset

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/) is also a really good source.

Thanks for the help.

---

