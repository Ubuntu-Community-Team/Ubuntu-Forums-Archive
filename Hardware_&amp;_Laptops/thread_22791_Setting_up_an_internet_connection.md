---
title: "Setting up an internet connection"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by Warhammer on 2005-03-29
Hi, I'm a newlly fleged Ubuntu 4.10 user ^^.
Now, my main problem is setting up the internet connection. I'm using cable connection, with an external modem . I have no idea where to start. My friend told me to use "pppoeconf". I did what he said and the program failed to detect the connection. If someone could explain me exactly what I should do to establish a simple cable internet connection I'd be really thankful.

---

### Post by m4ng0 on 2005-03-30
What kind of error messages do you get when doing
sudo pppoeconf
?

---

### Post by Warhammer on 2005-03-30
It says,
"Sorry, I scanned1 interface(s), but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem."

The connection is fine, I can connect to the net through Win.

---

### Post by m4ng0 on 2005-03-30
What kind of modem do you have? How is it connected to your PC? It's an USB or Ethernet modem? Does your ISP offer ppp over Ethernet or ppp over ATM?

---

### Post by Warhammer on 2005-03-31
The modems model is SuperLink2800, from Joohong. It uses an Ethernet connection (though I can connect to it through USB, too). I guess the ISP supports ppp over Ethernet.

---

### Post by Whiffle on 2005-03-31
i'm on a cable modem too, all I have mine setup for is dhcp.  Then again I have a router that handles that...  

Did your cable modem come with a manual?

---

### Post by Warhammer on 2005-03-31
Yes, I have a manual, but, not surprisingly, it says nothing about Linux (not to mention Ubuntu).

---

### Post by Whiffle on 2005-03-31
What kind of connection does it say it supports?  It should say something about dhcp or pppoe in there.

---

### Post by m4ng0 on 2005-03-31
Just to be sure... is your ethernet card recognized?
Type in a terminal:
ifconfig eth0
and look for some output.
If your ethernet card is usable and your ethernet modem is turned on, with sudo pppoeconf you should have no problem (if your ISP supports ppp over Ethernet as you said).

---

### Post by Warhammer on 2005-03-31
Well, I've managed to establish a connection by creating a network connection that uses DHCP. Then I typed "dhclient" in the terminal and I could connect to the net. Since the whole "identification procedure" hasn't been implemented yet, the only thing I can see is the ISP's page which forces me to download their automatic dialers. The only ones they have for linux are a script-based dialer for red-hat, and a more general script-based dialer for "all" linux versions. None of them are good for Ubuntu. I tried reconfiguring the "general" dialer to make it work with ubuntu, but I don't have enough knowledge and understanding of network communications. I reached a point where the script file "connected" me to the net, but something was missing. It still wouldn't work.
If it helps any, here are the "dialers":
[http://cables2.netvision.net.il/linux/](http://cables2.netvision.net.il/linux/)
Maybe someone could take a look at them and config them so they'd work properly with Ubuntu (or come up with a different solution). I'd be really grateful (though I do understand it's quite a request...).

---

### Post by Warhammer on 2005-04-01
Well, problem solved - found a dialer created by the local community of linux lubbers. ^_^

---

