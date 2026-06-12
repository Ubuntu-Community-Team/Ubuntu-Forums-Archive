---
title: "eMail server"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by drhiii on 2009-04-28
I know I know.  This horse has been so beat into the ground, but I have to ask... why is setting up an eMail server still at the Model T stage?  I followed the 'Perfect' series to install among other thingsand email server, to a 'T' so to speak, and I still cannot get SASL to work properly.  Had to chase down some problems which at this point one would think would have been ironed out by now.  Postfix running chrooted and the SASL directory not being seen was one glaring one.

So not that I have that minor rant out... folks, can anyone point me to a comprehensive HowTo set an eMail server?  Have not tried Zimbra, Citadel gave me a seg fault, so am trying to bang through the Postfix/TSL/SASL thing.  No go.  I keep getting an authentication error 

Anyone?

I just upgraded to 9.04 and may give Citadel a retry.  But, recommendations?

tx

---

### Post by kronepils on 2009-04-28
I would recommend Kolab ([www.kolab.org](www.kolab.org)).

It uses postfix, cyrus, apache, php and so on.
It's pretty easy to install, and is very good.

It uses openpkg however, so everything will install under /kolab. Which means that security updates is not as simple as apt-get upgrade, but still easy...

I use it for my mail.


./Troels

---

### Post by drhiii on 2009-04-28
Tx for the really fast response.  Feels like someone threw me a life preserver after swimming all night.

The server in question is running headless, and Kolab uses a GUI.  So not sure how to come at that.  But I will continue to review it.  I just really need some environment that can be managed, and Kolab looks good.  I just may not be able to do it with my server limitations.

tx


> **kronepils said:**
> I would recommend Kolab ([www.kolab.org](www.kolab.org)).

It uses postfix, cyrus, apache, php and so on.
It's pretty easy to install, and is very good.

It uses openpkg however, so everything will install under /kolab. Which means that security updates is not as simple as apt-get upgrade, but still easy...

I use it for my mail.


./Troels

---

