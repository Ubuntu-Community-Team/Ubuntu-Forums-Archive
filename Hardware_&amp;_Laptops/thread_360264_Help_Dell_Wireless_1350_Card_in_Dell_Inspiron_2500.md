---
title: "Help: Dell Wireless 1350 Card in Dell Inspiron 2500"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by clevelandohio on 2007-02-12
I installed Ubuntu 6.10 on my Dell Inspiron 2500. It recognizes that there is a wireless card plugged in, but will not connect to the internet. It is not a dual boot installation. I'm not running Windows. I'm only running Ubuntu

The wireless card is the Dell Wireless 1350 WLAN PC Card (Model WL-611GD).

I've searched the Ubuntu forums and Google looking for a solution and haven't come across any instructions dealing specifically with the Inspiron 2500 and the 1350 card.

Please note that my Dell Inspiron 2500 does not have an ethernet jack, so I cannot connect to the Internet at all. 

If I must have an ethernet jack, I am willing to purchase and install one. 

If anyone has any knowledge of a solution that will allow the Inspiron 2500 to successfully work with the 1350 card, I'd be very interested in hearing it.

I'm a relatively new to Ubuntu and greatly appreciate your assistance!

Thank you very much.

---

### Post by tgalati4 on 2007-02-20
Cleveland Rocks!

Grab yourself a terminal:

What does lspci tell us?

How about:  dmesg | more                 (q to quit)

We need to find if the proper driver is being loaded.

How about: ifconfig

How about:  iwconfig

We need to determine the actual wireless chipset that is being used, that will point us to the correct driver.  

Wireless cards are cheap and there are several that work out of the box.  Chances are we can get yours to work, but it requires some effort on your part.

The wireless driver detection changed from 6.06 to 6.10.  Try a 6.06 Live CD and see if it picks up the card.

Unfortunately, configuring Linux is more than finding someone with the exact same hardware as you.  You need to dig a little.

What is the wireless chipset?

Useful outputs of:

lspci
dmesg | grep somethingrelatedtowireless
ifconfig
iwconfig

With this information, we can provide a more authoritative answer.

Keep the faith,
Terry

---

### Post by clevelandohio on 2007-02-20
Terry:

Thanks for the reply. I figured out my chipset and learned that in order to enable my wireless connection, I really need to have a working Internet connection. 

I went out and purchased a 3com ethernet card. I installed it tonight and plugged in my cable expeting to be able to access the Net and get rolling -- and of course that isn't working either.

This is a much more complicated problem for me -- I'm not sure if it's a hardware issue or what...I'm going to post details in a different message than this one. I'm bummed out, but I'm determined to get this working. Thank you very much for your response.

---

