---
title: "i think im wasting my time"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by bigflame on 2006-10-17
ok i have a linksys wrt54g wireless-g 2.4 ghz b-band router and a laptop is there something else i need to go wireless? or do i need something else

---

### Post by Old Pink on 2006-10-17
Do you know who manufactuer the chipsets?

---

### Post by bigflame on 2006-10-17
what is a chipsets & i'll try to find it 4 you

---

### Post by Kateikyoushi on 2006-10-17
Most likely lspci will list it for you, type it to a terminal.
Look for ethernet controllers.

---

### Post by localuser on 2006-10-17
Bigflame,

you will need to configure the router.  Have you already done that, or are you at the "stuff on floor in a big pile" stage?

~lu

---

### Post by John.Michael.Kane on 2006-10-17
bigflame as the other posters have said you will need to configure your router. another thing that you have not told us is what kind of wifi card your laptop have?

---

### Post by Quintin Riis on 2006-10-18
Configure router?  Most of the blue boxes you get at Best Buy will "just work".

---

### Post by localuser on 2006-10-18
Routers don't "just work" without some configuration.  Its like your email client.  Even though it works "out of the box", it only works correctly (for you) as soon as you enter all of your information.

Here is an example of how you might configure your router.  This link doesn't show the exact model that you have, but you screens will look similar...
[http://www.haxial.com/faq/routerconfig/linksys/](http://www.haxial.com/faq/routerconfig/linksys/)

The trick is to know which address you have to enter to get to the router.  The address shown in the link above is 192.168.1.1.  Yours might be 192.168.0.1 or something that looks like this.  You'll need to check your documentation.

Also, you will have to connect a computer directly (with cable) to the router in order to set up your wireless connections properly.

Finally, you will want to set up proper security, otherwise others in your area will be able to see and use your wireless connection.  Wireless security is known as WEP or WPA.

[COLOR="Red"]Geek alert![/COLOR]  The following links are for information only if you're interested.  You don't have to plow through these just to get things to work correctly.  You should be able to get all you need from the documentation which came with your router.  This stuff really isn't as daunting as it might appear at first.

Information about how routers work in general...
[http://en.wikipedia.org/wiki/Routers](http://en.wikipedia.org/wiki/Routers)  

Information about your router in particular...
[http://en.wikipedia.org/wiki/WRT54G](http://en.wikipedia.org/wiki/WRT54G)

Information about WEP and WPA security...
[http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy)
[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access)

~lu

---

### Post by Quintin Riis on 2006-10-18
[QUOTE=localuser;1631329]Routers don't "just work" without some configuration.[QUOTE]
If the WAN address is obtained via dynamic host control protocol, then, yes, they do.

---

### Post by localuser on 2006-10-18
> **Quintin Riis said:**
> [QUOTE=localuser;1631329]Routers don't "just work" without some configuration.[QUOTE]
If the WAN address is obtained via dynamic host control protocol, then, yes, they do.

I agree Quintin Riis, DHCP does indeed make life easier, but there are other considerations.  For example wireless may not be enabled by default, though I'm not sure about this one to be honest.

Security, however, will almost certainly not be set up properly.  There's WEP or WPA encryption to configure.  And it wouldn't hurt to set up access restrictions to particular MAC addresses.  The router's default password should also be reset.  Otherwise you may leave your system exposed since the default password is widely known.

These things are not difficult to do and DHCP doesn't address them.

~Cheers

---

### Post by Quintin Riis on 2006-10-18
Wireless is of course going to be on by default.

So, yes, they *do* 'just work' out of the box.

This is totally off-topic from the original poster's issue.  Someone said that he needed to configure his router, and I am saying that that is most likely unnecessary!

---

