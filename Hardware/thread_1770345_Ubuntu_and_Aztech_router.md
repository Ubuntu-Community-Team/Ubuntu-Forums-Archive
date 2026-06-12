---
title: "Ubuntu and Aztech router"
date: 2011-05-29
forum: Hardware
---

### Post by Erienne on 2011-05-29
I need some help with our new modem/router. Before I was home, my dad installed a new wired/wireless modem to replace our old one. Now, my dad and my sister both can connect to the internet (I'm on dad's comp).

I mucked around with the settings, but screwed up somewhere so I had to take a pointy stick to the reset button. After fiddling around the settings some more, I got my laptop to connect to the access point (but not the internet)

For the record, the modem/router is an Aztech DSL 1000ew, which is a Malaysian company I believe. My dad and sister both use Windows 7, and I use Ubuntu Maverick 10.10. They used wired, and I wireless.

Looking in the settings of the modem/router, I see that my laptop is authenticated and authorized by the AP, but still, no Internet. I think the problem is that in Win7, there's a login-form for the ISP... kinda like the dial-up form of old times. (Now that I think of it, it's pretty much the same.) If it were that, it would explain why I'm able to get a wireless connection without any internet. But the problem is, there's no such similar form in Maverick. I'm completely at a loss as to what to do.

Any suggestions as to what I should do? Other than install Windows, I mean.

---

### Post by vishwasharitsya on 2012-04-29
Hi Erriene,

          I'm stuck up with the same problem. Could you please let me know if your case is solved and if yes, what is the solution?

Regards,
Vishwas

---

### Post by ahallubuntu on 2012-04-29
In the original poster's case, since he did a factory reset of the modem, he wiped out the PPP username and password that was (most likely) saved in the modem to connect to the DSL ISP automatically.  So his modem would now no longer connect, since the username/password is gone.

Your DSL/internet provider may have provided a CD you can use to setup your modem again.  You can also do it via your web browser most likely, to login to your modem.  Try pointing to:

[http://192.168.1.1](http://192.168.1.1)

or

[http://192.168.0.1](http://192.168.0.1)

and see if that pulls up a page on your modem.  The address varies depending on the make/model of your modem.

Then, you can configure the modem.  Find a place for PPP login where you would supply a username/password for the DSL provider.  Of course, you will need to remember your username/password.  If you don't know them, contact your provider.

---

