---
title: "Printing Wireless from Laptop"
date: 2012-08-12
forum: Hardware
---

### Post by Wuxin on 2012-08-12
I have an IBM ThinkPad t43 that runs Xubuntu 4.12.  I print my documents with a wireless connection to my Brother HL-2170w printer.  Up until a few days ago all was well.  Now when I go to print a document, the printer does not recognize my computer.  What is the best way to remedy this situation?  My computer has a fine wi-fi connection so the problem isn't with the router.  If anyone has suggestions, I will welcome them!  Thank you.

---

### Post by ahallubuntu on 2012-08-12
I assume the printer was connected via WiFi before?

I think if you hold the GO button down for 10 seconds, the printer will print out a status page including network connection information.  Make sure it has obtained an IP address from the router.  If it has an IP, make sure it hasn't changed for some reason - make sure the Ubuntu installation of the printer still references that same IP address.

Sometimes if you hit the GO button or hold it down, that alone will put the printer back online so you can print again.  I have seen this many times with Brother printers!

---

### Post by Wuxin on 2012-08-12
Thank you for this.  I don't know if the router has an IP or what it is?  (Where would I find that information?)  Is it a good idea to set up a static IP for the router (or other devices, for that matter?).  I've heard there are reasons for and against this.  

So just hold down the "Go" button for ten seconds?  If the page prints out--I think it will--where would I find the reference for the IP of the router and/or printer?  In the past few weeks we've had some electrical storms in this area--I'm wondering if that may have disrupted something.  Thank you again.

---

### Post by ahallubuntu on 2012-08-13
Try holding the GO button.  The worst that you lose is one page of paper and a little toner.

You should see reference to an IP address on that page.  If it's 0.0.0.0 or 169.something, it doesn't have a real IP address.  But as I said, just hitting the button may put it back online.  Just try printing again right after you do that.

Static IP is nice, yes.  Usually your router has the ability to make a DHCP reservation for any connected device, so it always gets the same IP address.  This isn't quite the same as "static IP" (where you set the IP to a fixed address ON THE DEVICE ITSELF).  I find it easier to manage my network in one place (the router).

If you want to know what IP was used (if any) when you installed your printer, open up the Printers tab in System Settings and check the Properties of the printer as installed now.  You should see an IP listed there unless it used something besides IP.

Assuming you own and control the router, find out how to login to it.  If your laptop's IP address is 192.168.1.4 (try "ifconfig" in a terminal window to find out your IP), then go to the gateway which is probably 192.168.1.1 - in a web browser window:

[http://192.168.1.1](http://192.168.1.1)

You'll be asked for an admin username/password.  Username is probably admin.  If you never set an admin password it's probably blank or "admin" or "password" or "1234" .  Anyway, once you login there you can change your router settings, find out what IP might currently be assigned to the printer (if any), make a DHCP reservation for it, etc.

---

### Post by Wuxin on 2012-08-13
Thank you for the above.  What about this: I called the printer company (Brother) and they had  me simply delete and then reinstall the printer on my main desktop computer.  Might it be a good idea to do the same on my laptop?  How would I do that?  We have had electrical storms in this area over the past few months and that included some power outages.  I would imagine that a disruption of power could cause crazy things to happen with wireless settings.  What do you think?  Would deleting and then reinstalling the printer be a good way to start?

---

### Post by dandnsmith on 2012-08-15
Re-installation is the 'easy' fix (for Windows), but only postpones the problem.
I agree that a 'static' IP address is the way to handle this, so that the queuing details don't get to be invalidated.
A DHCP reservation at the router is certainly a good idea, as rendering the printer fixed in that locality, while retaining the ability to transfer quickly and easily to another network site (but then, how many do this?)

---

