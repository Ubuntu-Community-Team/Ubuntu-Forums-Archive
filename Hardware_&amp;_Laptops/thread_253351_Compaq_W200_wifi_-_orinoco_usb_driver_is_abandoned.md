---
title: "Compaq W200 wifi - orinoco_usb driver is abandoned"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by David Gerard on 2006-09-08
[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

I've updated this with something I didn't know before: that the orinoco_usb developer, Manuel Estrada Sainz (ranty@debian.org) died in a car crash in 2004 and no-one's worked on it since.

So if it works at all, it's luck!

The CVS copy of the driver works in Dapper (kernel 2.6.15), but they're using Subversion now, so you need to pull the code from svn to test in Edgy (kernel 2.6.17). The orinoco_pci driver (which is maintained) works in 2.6.17, and orinoco_usb is basically patches to that, so it *might* work. See this post to orinoco-users for a possibly promising approach:
  [http://sourceforge.net/mailarchive/message.php?msg_id=30525102](http://sourceforge.net/mailarchive/message.php?msg_id=30525102)

I hope to try the svn copy of the driver in Dapper this weekend. If someone could please try it in Edgy, that would be most helpful. Then we can update the wiki page with a working procedure.

(Note that the svn copy of the code doesn't seem to include the firmware download script.)

I've emailed orinoco-devel noting that if anyone ever wants to take up orinoco_usb again, there's a pile of W200 users here who would be happy to be testers. The W200 driver is horrible, but having the wifi in the lid is *so* convenient. I've bent and damaged one PC-card wifi with my N410c so far ...

Mind you, I'm sorely tempted just to gut my W200, fit a standard USB socket and plug in a USB wifi adapter that's actually *popular* and has a *supported driver*. Gah.


- d.

---

### Post by Mimsy on 2006-09-08
Urgh. *gives threatening glares to the W200* You'd better keep working, you piece of... Er. :-#  I mean, you sweet wonderful example of magnificent hardware!

Right. :^o 

Mimsy,
just a bit bored at work today...

---

### Post by David Gerard on 2006-10-10
Dean Sos has updated the page and posted successfully using the W200 on Edgy. w00t!

[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

---

### Post by Mimsy on 2006-10-10
Sweet! Seeing that someone made this work in Edgy is great. It makes me happy. :)

Looking at the page I notice that there's no Edgy section for installing all the required packages. Will they come preinstalled in Edgy then?

/Mimsy

---

### Post by sas on 2007-01-09
Guys I'm really struggling getting this to work with Feistys kernel. Has anyone else gave it a try?

---

### Post by Mimsy on 2007-01-11
I recently reinstalled Ubuntu, and of course one of the first things I set about doing was to install the drivers for my wireless adapter.

I made it this far:
> mimsy@Falcon:~$ svn co [https://svn.sf.net/svnroot/orinoco/branches/usb](https://svn.sf.net/svnroot/orinoco/branches/usb)
Error validating server certificate for 'https://svn.sf.net:443':
 - The certificate hostname does not match.
Certificate information:
 - Hostname: *.sourceforge.net
 - Valid: from Dec  8 13:40:07 2005 GMT until Feb  7 13:40:07 2007 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: 49:b8:cb:87:04:8c:49:39:45:83:dd:4c:cf:c7:54:57:b0:9e:84:5d
(R)eject, accept (t)emporarily or accept (p)ermanently? p
svn: PROPFIND request failed on '/svnroot/orinoco/branches/usb'
svn: PROPFIND of '/svnroot/orinoco/branches/usb': Server certificate verification failed: certificate issued for a different hostname ([https://svn.sf.net)](https://svn.sf.net))

It works if I accept the certificate temporarily, but not if I accept it permanently. That's just weird.

/Mimsy

---

### Post by Mimsy on 2007-02-06
After spending a few weeks trying to get the Evo to go wireless with WPA-TKIP, it finally occurred to me to ask: Has anyone here managed to get the W200 to work with WPA encryption? How did you do it?

/Mimsy

---

### Post by sas on 2007-02-06
I've not tried using Linux. Personally I couldn't get WPA working in Windows though I did only try with the default driver.

---

### Post by Mimsy on 2007-02-06
So the W200 may in other words be too old and crappy to be able to connect to a WPA encrypted wireless network?

Gah. I suddenly wish I had thought to ask about this, in thsi thread, about three weeks ago. ](*,) 

/Mimsy

---

### Post by sas on 2007-02-06
> **Mimsy said:**
> So the W200 may in other words be too old and crappy to be able to connect to a WPA encrypted wireless network?

I only tried for five minutes and just dropped the security down to WEP for the evening (was at a friends) rather than mess around trying to get WPA working.

---

### Post by Mimsy on 2007-02-11
I have now dropped the security down to WEP, and set up everything else in the house to work along with the new settings. The W200 still refuses. I have network-manager-gnome installed and the network shows up in the list of available ones whenever I look for it, but  I can't connect.

I am open to suggestions...?

/Mimsy

---

### Post by mylinuxcluster on 2007-02-14
@ Mimsy

I have been struggling to do the exact same thing over the course of the last couple of days. I believe that the w200 has some major issues crypting WPA under linux. However, a downgrade to WEP worked like a charm... however I am now looking into setting up at least a VPN to the router to add some extra security.

* this however, should not encourage anyone to give up trying to set up the w200 with WPA :)

---

### Post by Mimsy on 2007-02-14
Personally, I am very curious to know why I can't connect to the router at all... not even with the security disabled. For some reason, the last five or six updates to netwrok-manager-gnome seem to have made it more and more difficult to connect to wireless networks with it. This is getting absolutely ridiculous. 


/Mimsy

---

### Post by MicheleZ on 2007-04-13
Hello Mimsy,

I had loads of issues with WEP and the W200, basically it was working for 5 minutes and then wrecking my access point (D-Link 524 IIRC). I actually had to reset the Access point to make it work again. 
Since the AP also provides the DHCP, I ended up removing the WEP and the DHCP, so that the IP address allocated are static and linked to the MAC addresses. Now if someone can spoof the MAC address of my W200 he/she can gain access to the network, but until I upgrade my laptop that's all I can do :(
I still have to reset the interface every now and then, but now it works.

Let me know if you have any luck at least with WEP.

Cheers,

Michele

---

### Post by amgat on 2007-04-27
Confirmed. My W200 card is now working using the instructions from that website. Using it right now. Ubuntu 7.04. Thankyou for your effort! :)

---

### Post by Mimsy on 2007-04-27
And of course, now teh eternal question... how's the WPA connectivity? 

/Mimsy

---

### Post by mr_skater99 on 2007-11-25
Hi all,

Just wondering if there was any news or updates on the W200 driver.

I'm still using a pcmcia card, but would love to use the inbuilt w200.

Anyone interested in getting together to see what we can do to get this done?

Cheers,

Scotty

---

### Post by otman on 2007-12-29
The installation of the driver for W200 worked on my Evo N800c. However, as in the [[COLOR="Red"]writeup[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200") for W200 on the Ubunto website, the thing is very unstable under 7.10. It froze my computer several times and I gave up trying to make it work. I had to re-install the OS 7.04 but have not tried re-installing the driver yet.Not sure yet if I will do the installation of this driver after so much frustation and pain. Thanks for the nice writeup though.

---

