---
title: "rdesktop with Server 2008 TS Gateway"
date: 2008-10-11
forum: General Help
---

### Post by Phlosten on 2008-10-11
My employer has decided to implement a TS Gateway setup on our work terminal server (Windows Server 2008) that requires the remote desktop client to connect through a TS Gateway first.

As far as I can tell there is no functionality within the current rdesktop client to be able to connect to Windows Server 2008 servers this way.

Is anyone aware of a method to do this?

At the present point I am forced to use Windows to connect to work remotely, however I can still use rdesktop while at work on the local network where I don't need to connect to the TS Gateway.

---

### Post by CM-Mitch on 2009-01-11
I'd also like to know if anyone has solved this problem.  I'm thinking about running the most current Microsoft TS client in wine but I'd prefer Ubuntu's built in TS client include the TS gateway settings.

---

### Post by CM-Mitch on 2010-04-08
.... still looking for an RDP 6.x client for Ubuntu.  :(

---

### Post by abbbottt on 2011-08-10
I have been banging my head against the wall for weeks trying to look for any solution to get connected to work network through a damn TS Gateway. In the end I found a solution that I'm not 'idealistically' happy with but am just bloody glad IT FINALLY WORKS.

If you're in a similar position and can live with a small diversion from your FOSS ideals then it's 20 Euros well spent!

[http://itap-mobile.com/desktop/rdp](http://itap-mobile.com/desktop/rdp)

Think this is fairly new...? Hope this helps some of you guys out!

Chris

---

### Post by CM-Mitch on 2011-10-18
Finally!  I already use iTap mobile on my Android phone (works well!), I guess I'll have to purchase it for my laptop too.

---

### Post by richud on 2012-03-20
I am posting here as it seems the top hit in google and so lots of people should hopefully see it.

Please register your support here in the feature request 

(FreeRDP is effectively the 'replacement' to Remmina)

[https://github.com/FreeRDP/FreeRDP/issues/386]("https://github.com/FreeRDP/FreeRDP/issues/386")

---

### Post by dcstar on 2012-03-20
> **richud said:**
> 
(FreeRDP is effectively the 'replacement' to Remmina)


Rubbish, Remmina **uses** FreeRDP as one of its components, they are "sister" projects:

[http://remmina.sourceforge.net/](http://remmina.sourceforge.net/)

Remmina replaces the old Rdesktop package.

---

### Post by Compson on 2012-03-20
à âû ñîáèðàåòåñü ïðîäîëæàòü ýòó òåìó íà ubuntuforums.org , åñëè ÷åñòíî - ïðèêîëüíî!

---

