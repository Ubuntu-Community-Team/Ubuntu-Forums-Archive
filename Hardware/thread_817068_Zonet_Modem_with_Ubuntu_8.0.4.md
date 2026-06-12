---
title: "Zonet Modem with Ubuntu 8.0.4"
date: 2008-06-03
forum: Hardware
---

### Post by bstanley on 2008-06-03
Hi! My name is Bruce and I have just installed Ubuntu 8.0.4
onto my Thinkpad T41 laptop using the 'Install as Application'
method.

I works great except for the Zonet modem I am trying to use
for dialup.

I am trying to use a ZONET PCMCIA modem, model ZFM5600CF, a 56K V.92 N hardware modem (not a winmodem).

When I run the modem search utility script, it finds the 
IBM built in Winmodem but does not seem to find the 
hardware Zonet modem.

When I use Mepis 6.5 in Live CD boot up mode, it can access
and use this modem without any problems as /dev/ttyS1.

Is there something else I need to install so that I can use
this modem?

---

### Post by bstanley on 2008-06-04
Hello!

Is there anybody out there?

Any help available for a Zonet PCMCIA Modem?

---

### Post by bstanley on 2008-06-05
Here is a text file that contains the message in the
system message file when the  Modem is inserted in the
PCMCIA slot 0  and also the results of a scanModem run.

Hope someone can help.

---

### Post by bstanley on 2008-06-09
Is this the wrong Forum to post this question on?

Should I repost this on the Networking Forum?

---

### Post by _duncan_ on 2008-06-09
I have no experience with PCMCIA modem cards so please view my post with the proverbial grain of salt. Anyway, here's my opinion:

1. My understanding is that most PCMCIA modem cards are hardware modems. If that's the case then you don't need drivers to make it work in linux.

2. Hardware modems don't always get detected by ubuntu, but they will still work if you know which port to point your dialer program to. In this case, it should be /dev/ttyS1, based on your experience with Mepis. I'm a little confused here though since in your attachment (zonetinfo.txt), your card seems to be in /dev/ttyS2. It's not a big issue. You can try both and see which one works.

3. Don't be concerned with the results of scanModem. It's primarily a tool to detect pci or usb based winmodems. I don't think it checks serial ports or pcmcia cards so it's logical your modem card will not show up in the scan results.

I suggest you try using one of the dialer programs (wvdial, pppconfig, gnome-ppp, etc) to set up your internet connection. If it doesn't detect your pcmcia card, try manually pointing it to either /dev/ttyS1 or /dev/ttyS2 and see if it works.

Click on the 2nd link on my signature (Dial-Up Modem Wiki) if you need instructions on how to set up a dialer program. Navigate to the "Configure Connection to Internet Service Provider" section to see the dialer programs available to you. I personally prefer using pppconfig (with pon & poff), but majority of ubuntu dial-up users use wvdial instead.

---

### Post by bstanley on 2008-06-10
Hi Duncan!   Thanks for responding.

I have tried setting up ppp with the gnome-ppp prgram
using  /dev/ttyS0,  /dev/ttyS1, /dev/ttyS2, and even
/dev/ttyS3.

When I hit the 'Detect' button, none of these devices work.
I always get the 'No Modems were found' error message.

If I try to go ahead and have  gnome-ppp dial up the ISP
anyway, I get an error message 'Modem not responding'.

I have not tried to use  wvdial yet.

It is a bit strange that Mephis 6.5 would see the modem as
/dev/ttyS1 while the  system log for Ubunto 8.0.4 seems to
see it as  /dev/ttyS2.



What is also strange that while the modem works with Mephis 6.5,
it will not work (same problems) with Mephis 7.0.  The difference
between the two version of Mephis is that 6.5 is based on the
Mandrake Kernel while with 7.0 they switched to a version of
the Debian kernel which is what I believe Ubuntu is based on.

This is why I wonder if there is a kernel PCMICA or Modem
driver that is missing?

---

### Post by _duncan_ on 2008-06-10
This is a long shot, but is it possible there is IRQ conflict with other devices? I remember helping a friend set up dial-up via pcmcia card on a laptop running win98 (yes, it was that long ago). The problem boiled down to an IRQ conflict. After reassigning IRQs the pcmcia modem worked flawlessly.

Problem is, I don't know how to do this in linux. My best guess is to use the [COLOR="Blue"]**lspci -v**[/COLOR] command on a terminal and visually checking IRQ numbers per device with your pcmcia card plugged in. If there is indeed conflict, perhaps the **[COLOR="Blue"]setserial[/COLOR]** command will allow you to map and reassign IRQs. You must understand though that I have absolutely no experience with this in linux so it's all pretty iffy.

Sorry I wasn't of much help.

---

### Post by bstanley on 2008-06-24
Well, vowallla........

I can't believe that one simple modem setting in the
network managers config screen, or in the .wvdial.conf
allowed my Zonet modem to start working.

By setting turning the 'Stupid Mode' on, everything started
working.  I first tried this in the  '.wvdial.conf' file
and then wvdial starting accessing my modem.

I am sending this reply on my Thinkpad T41 with the Zonet.

Thanks Duncan for your help but this was the only thing needed.

Why didn't anyone on this forum mention this?

And, what is the 'Stupid Mode' for?  Why would Ubuntu
finally be able to access the modem with this setting on?

Curious minds want to know......   :-)

---

### Post by bstanley on 2008-06-26
Well, I spoke to soon,  sort of.....

All was working well with the Zonet as  /dev/ttyS2 on irq #3

After updating the system yesterday with all the latest patches,
the system went from  kernel  2.6.24-17 to 2.6.24-19 and the
Zonet stopped working, and I was getting the same kind of problems as before.

This time however, there was some sort of chat script running in
the back ground putting a lock on  /dev/ttyS2.

I found the ppp0 config file in /etc that was starting this script up and renamed it so that I would not have this problem 
anymore (this was new).

I then played around with the setserial utility and determined
that I could get it to work again resetting the irq from 3 to 11.

Why...???  If that is the way it has to be, how can I get the
kernel to assign irq 11 to the PCMCIA modem when I insert it
instead of irq 3?

---

