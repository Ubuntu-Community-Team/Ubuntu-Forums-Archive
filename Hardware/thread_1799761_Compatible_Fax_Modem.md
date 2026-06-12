---
title: "Compatible Fax Modem"
date: 2011-07-08
forum: Hardware
---

### Post by RogerDavis on 2011-07-08
I need a compatible INTERNAL fax modem.  No magic incantations, no adaptations for WinModems, no "adjustments", just install and run.

Can someone recommend one that they are SURE about?

Thanks!

---

### Post by walt.smith1960 on 2011-07-08
I don't know of *any* PCI (internal) modem that is not a 'WinModem'. There may be one though.  The dial-up networking guys seem to prefer US Robotics external serial.  Good luck to you.

---

### Post by RogerDavis on 2011-07-08
I was aware of the preference for the external serial.  That's why I emphasized INTERNAL.

I do know for sure that there at least WERE some internal USR modems that were NOT Wimmodem types.  In fact, I know where one is, in my old computer that I gave to my girlfriend some years back.  I may be able to recover it, but I'd much prefer to just replace it, IF it would work without hassle.

For example, USR quotes the 56K* V.92 Internal Performance Pro Modem as suitable for Linux, at  [http://www.usr.com/products/modem/compare-modem-home.asp](http://www.usr.com/products/modem/compare-modem-home.asp) ,  and at  [http://www.usr.com/products/modem/modem-product.asp?sku=USR5610C](http://www.usr.com/products/modem/modem-product.asp?sku=USR5610C) .   However, these ain't cheap, and I'd like to be sure first.

SOMEONEs gotta know for sure...

---

### Post by walt.smith1960 on 2011-07-09
> **RogerDavis said:**
> I was aware of the preference for the external serial.  That's why I emphasized INTERNAL.

I do know for sure that there at least WERE some internal USR modems that were NOT Wimmodem types.  In fact, I know where one is, in my old computer that I gave to my girlfriend some years back.  I may be able to recover it, but I'd much prefer to just replace it, IF it would work without hassle.

For example, USR quotes the 56K* V.92 Internal Performance Pro Modem as suitable for Linux, at  [http://www.usr.com/products/modem/compare-modem-home.asp](http://www.usr.com/products/modem/compare-modem-home.asp) ,  and at  [http://www.usr.com/products/modem/modem-product.asp?sku=USR5610C](http://www.usr.com/products/modem/modem-product.asp?sku=USR5610C) .   However, these ain't cheap, and I'd like to be sure first.

SOMEONEs gotta know for sure... 
I hope someone can help you.  You discovered the reason WinModems triumphed. They're cheap, "real" modems aren't.  You are correct the be cautious about "works with Linux". I bought a WiFi adapter that was listed as "works with Linux".  I couldn't get it to work and gave it to Chili555 to do with as he pleased.  He was able to get it to work but he's no mere mortal when it comes to Linux+networking and he didn't find it easy.  The lesson for me is to take "works with Linux" with a large grain of salt.

---

### Post by gordintoronto on 2011-07-09
> **RogerDavis said:**
> I was aware of the preference for the external serial.  That's why I emphasized INTERNAL.

I do know for sure that there at least WERE some internal USR modems that were NOT Wimmodem types.  In fact, I know where one is, in my old computer that I gave to my girlfriend some years back....
...

The kicker is that the definition of "internal" has changed. I have a couple of old internal modems, which you plug into an ISA (as defined by the IBM PC) slot. It's been over eight years since I last saw a computer for sale which included an ISA slot. At least the serial port has not changed, although they are also getting rare.

---

### Post by RogerDavis on 2011-07-09
So if I have a PCI slot, this is as good as an external modem?

This one is the USR5610C.  How about the USR5610B?

-----
For example, USR quotes the 56K* V.92 Internal Performance Pro Modem as suitable for Linux, at [http://www.usr.com/products/modem/co...modem-home.asp](http://www.usr.com/products/modem/co...modem-home.asp) , and at [http://www.usr.com/products/modem/mo...p?sku=USR5610C](http://www.usr.com/products/modem/mo...p?sku=USR5610C) . However, these ain't cheap, and I'd like to be sure first.
-----

---

### Post by gordintoronto on 2011-07-09
A non-Winmodem is as good as an external.

Are you mostly interested in sending or receiving faxes?

---

### Post by RogerDavis on 2011-07-10
Yes... That is, both send and receive.  

And it's not impossible (though very unlikely) that I may need to use it for internet access in an emergency.

---

### Post by gordintoronto on 2011-07-10
Have you checked that your computer has only PCI slots?

Once upon a time, I was an "expert" on modems, and all my experiences with U.S. Robotics were good. However, my "expertise" is six years out of date.

---

### Post by foresthill on 2011-07-11
Some of the later US Robotics PCI modems were Winmodems, but most of the models they sold were hardware based.

I used to have a USR 5686 PCI modem that I loved, but it just stopped working one day. I have looked and looked for a replacement, but new ones are no longer being made, and second-hand ones rarely turn up.

And as another poster mentioned, the early models US Robotics made were not PCI, but ISA, so finding one of those would not be terribly helpful, unless your motherboard was built around 1996 or earlier (highly unlikely). 

However, if you want to go with a serial modem, pretty much any of them will work, and if you don't have a serial port, buy a USB to serial adapter (these are plug and play in Linux) and you'll be all set.

---

### Post by RogerDavis on 2011-07-11
I do have PCI slots...  I'm almost certain at least one is available.

Expansion Slots:
Four (4) DIMM sockets
[COLOR="Red"][SIZE="3"]Four (4) PCI slots[/SIZE][/COLOR]
Two (2) PCI Express x1 slots
One (1) PCI Express x16 slot

The USR modem is PCI
Minimum System Requirements
    PC with 486DX or Pentium class processor or equivalent
    [SIZE="3"][COLOR="Red"]Available PCI slot[/COLOR][/SIZE]
    Analog phone line
   [COLOR="Red"][SIZE="3"][SIZE="4"][SIZE="3"][SIZE="3"] Linux (Kernel 2.3 and higher)[/SIZE][/SIZE][/SIZE][/SIZE][/COLOR], Microsoft Windows 95, 98, Me, NT4.0, 2000, XP, Server 2003, XP 64 bit, Server 2003 64 bit, Vista, Vista 64 bit, Win 7, Win 7 64 bit operating system** (Unimodem TSP/TAPI compliant)

Looks ok to everyone?

---

### Post by gordintoronto on 2011-07-11
Yes, that looks OK, but I can't guarantee it.

---

### Post by walt.smith1960 on 2011-07-12
> **RogerDavis said:**
> I do have PCI slots...  I'm almost certain at least one is available.

Expansion Slots:
Four (4) DIMM sockets
[COLOR=Red][SIZE=3]Four (4) PCI slots[/SIZE][/COLOR]
Two (2) PCI Express x1 slots
One (1) PCI Express x16 slot

The USR modem is PCI
Minimum System Requirements
    PC with 486DX or Pentium class processor or equivalent
    [SIZE=3][COLOR=Red]Available PCI slot[/COLOR][/SIZE]
    Analog phone line
   [COLOR=Red][SIZE=3][SIZE=4][SIZE=3][SIZE=3] Linux (Kernel 2.3 and higher)[/SIZE][/SIZE][/SIZE][/SIZE][/COLOR], Microsoft Windows 95, 98, Me, NT4.0, 2000, XP, Server 2003, XP 64 bit, Server 2003 64 bit, Vista, Vista 64 bit, Win 7, Win 7 64 bit operating system** (Unimodem TSP/TAPI compliant)

Looks ok to everyone?

If your prospective modem uses PCI, you probably have one suitable slot.  PCI-E x1 is a much smaller connector with fewer pins than PCI but has higher capacity than PCI and is commonly used for things like USB3 and eSATA expansion cards.  PCI-E x16 is only used for graphics cards AFAIK.  Can you get this from a source where you have at least a couple weeks to return it if you can't get it to work?

---

### Post by RogerDavis on 2011-07-12
I haven't checked on how many slots are open, but I'm sure at least one of the four are open, probably 2 or 3.

I haven't tied down where to get the modem yet, probably later today or tomorrow, but you have a good point about returning it if needed.

Thanks!

---

### Post by RogerDavis on 2011-07-12
A new question - USR has modem software written for Red Hat.  Will this work in Ubuntu?

---

### Post by walt.smith1960 on 2011-07-13
> **RogerDavis said:**
> I haven't checked on how many slots are open, but I'm sure at least one of the four are open, probably 2 or 3.

I haven't tied down where to get the modem yet, probably later today or tomorrow, but you have a good point about returning it if needed.

Thanks!

You probably only have one slot that will accept the modem.  It will not fit your 2 PCIe x1 or your PCIe x16, only your single PCI.  It might be a good idea to be sure your PCI slot is available.  You're lucky to have 2 PCIe x1 though.  Most newer expansion cards seem to require PCIe x1.  I only have one.

---

### Post by RogerDavis on 2011-07-13
I have four.

From an earlier message:
Expansion Slots:
Four (4) DIMM sockets
Four (4) PCI slots
Two (2) PCI Express x1 slots
One (1) PCI Express x16 slot

---

### Post by fatboysmith on 2011-07-14
I use a [MultiTech MultiModem ZPX ]("http://www.multitech.com/en_US/PRODUCTS/Families/MultiModemZPX/")and have for years...no drivers just point gnome-ppp to ttyS3 and it works...

---

### Post by RogerDavis on 2011-07-15
Thanks for the MultiModem info.  

I think I can assume it's very similar to the USR that I ordered today.

---

