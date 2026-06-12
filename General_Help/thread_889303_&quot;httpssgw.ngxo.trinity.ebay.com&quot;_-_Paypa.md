---
title: "&quot;https://sgw.ngxo.trinity.ebay.com&quot; - Paypal times out..."
date: 2008-08-14
forum: General Help
---

### Post by emarkay on 2008-08-14
Recently I have not been able to use PayPal to make eBay payments -I get to the "Confirm Payment" section and click, then it goes to :
[https://sgw.ngxo.trinity.ebay.com/?X-EBAY-SVC-SERVICE=paypalpay_paypal_ebay.com](https://sgw.ngxo.trinity.ebay.com/?X-EBAY-SVC-SERVICE=paypalpay_paypal_ebay.com)...............
and then times out.

I have reboted and cleared my DNS cache.

It does work in window$, and both are running FF 3.0.1

Anyone else have this prob or a solution?

Thanks!

MRK

---

### Post by Mgiacchetti on 2008-08-14
[https://payments.ebay.com](https://payments.ebay.com)

---

### Post by emarkay on 2008-08-14
Um, that link goes to the sell your stuff page..


OK, NEXT?

---

### Post by emarkay on 2008-09-02
Anyone???

---

### Post by kevinherring on 2008-12-03
Hey I have exactly the same problem. However, I am using OS X with Opera. I just tried paying with Safari, and it just gives up and gives me a blank screen.

Its really annoying as I have no idea whether the payment went through or not. I ended up paying twice the first time it happened and then I got charged to get a refund!!

It has only been doing it the last 3 months or so.

My url is similar, except I am in Aus, so I have a .com.au

---

### Post by H4rm0ny on 2008-12-22
I'm going to bundle into this thread because I think my problem is the same / related. Apologies if it later turns out not to be. I can at least offer some possible other details, however.

I now have three sites where I am unable to post or carry out certain actions from my Kubuntu Hardy installation. However, I am able to carry out the actions from my Windows XP installation. This appears independent of browser as it happens both in the latest Firefox and in Konqueror. One site is an online fitness forum and the other is my online banking site. In both cases, the issue occurs when using http**s** and POST commands and the symptom is an apparent timeout in waiting for a response from the server. I currently have to boot up Windows to interact with these sites which is irritating as you can imagine.

I'm reasonably adept with my system and I can investigate firewall settings, or even sniff packets, etc with a bit of advise as to what to look for. Any suggestions from people as to where to go from here?

---

### Post by emarkay on 2009-10-12
FWIW, this is STILL an issue!
[http://picturepush.com/public/2370883](http://picturepush.com/public/2370883)

Locally at respective forums, too:
[http://forums.ebay.com/db2/topic/Techni ... g523096620]("http://forums.ebay.com/db2/topic/Technical-Issues/Ebaypaypal-Double-Billing/520160229&#msg523096620")
[http://www.paypaldev.org/yaf_postst1645 ... yebay.aspx]("http://www.paypaldev.org/yaf_postst16459_eBayPayPal-double-billing--sgwngxotrinityebay.aspx")

---

### Post by dcstar on 2009-10-13
> **emarkay said:**
> FWIW, this is STILL an issue!
[http://picturepush.com/public/2370883](http://picturepush.com/public/2370883)

Locally at respective forums, too:
[http://forums.ebay.com/db2/topic/Techni ... g523096620]("http://forums.ebay.com/db2/topic/Technical-Issues/Ebaypaypal-Double-Billing/520160229&#msg523096620")
[http://www.paypaldev.org/yaf_postst1645 ... yebay.aspx]("http://www.paypaldev.org/yaf_postst16459_eBayPayPal-double-billing--sgwngxotrinityebay.aspx")

Yep, had it happen to me on my 9.04 system using FF 3.0.14 the other day - unfortunately I am used to it by now!       :(

Every time a new FF version is released major eBay functionality is lost until they catch up, but they still can't get a website that works reliably for anything but IE on Windows - the pack of dopes.....

---

### Post by genterminl on 2010-04-11
Over a year, and the problem persists.  However, it is not specific to browser or to distro.  I have the same problem on Gentoo with Firefox, Konqueror, Chromium, Epiphany.  The give different error messages, but all come down to the connection has been reset.  Ebay and paypal work fine by themselves, but the handoff for a payment seems to be where the problem pops up.

Does anybody have any serious ideas on how to troubleshoot this?

---

### Post by Carl Farrington on 2010-04-11
> **genterminl said:**
> Over a year, and the problem persists.  However, it is not specific to browser or to distro.  I have the same problem on Gentoo with Firefox, Konqueror, Chromium, Epiphany.  The give different error messages, but all come down to the connection has been reset.  Ebay and paypal work fine by themselves, but the handoff for a payment seems to be where the problem pops up.

Does anybody have any serious ideas on how to troubleshoot this?

I'm seeing the same, using Chrome on Lucid x86. I also had the same earlier today on my Netbook running UNR Lucid, again using Chrome.

I think it's just an eBay/PayPal problem. Not sure why some people are saying it works in Windows, doesn't seem to make sense. I just tried again earlier on the netbook and it worked. Also I just bought a new laptop, from this laptop, and it worked. Now I just tried to pay for a replacement bezel for this laptop, and I'm having the problem again.

---

### Post by genterminl on 2010-04-11
OK - somebody suggested something to me today, which seems to have worked.  I made two purchases/payments today with no problems.

I changed the MTU from 1500 to 1492.  I made the change in my router (I'm on DSL), but could apparently also have done it directly on my PC (Linux, using ifconfig).  This particular change (dropping MTU from 1500) seems to be related to a DSL related quirk - not sure why Windows doesn't seem to have the same problem - perhaps their default MTU is already lower than 1500.

Hopefully this will work for more than just me!

---

### Post by genterminl on 2010-04-13
(I thought I posted this yesterday - but I suppose it went someplace else....)

Somebody finally gave me a suggestion that worked.  I dropped my network MTU from 1500 to 1492, and I can now pay for ebay purchases with paypal without any problems.  This is apparently a known issue related to DSL with PPoE, so it may not solve the problem for everyone.

In my case, I changed the MTU setting in both of my routers (both Linksys) but I could apparently have also changed it on my PC directly with ifconfig.  I wonder if Windows simply doesn't let the MTU get too high?

(Now I'm really confused - I posted this because I didn't see my post from yesterday - but not that I posted this I do see it.  Sorry for the duplication, but I hope it helps someone else.)

---

