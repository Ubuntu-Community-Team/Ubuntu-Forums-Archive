---
title: "Firefox startup problem"
date: 2008-10-10
forum: General Help
---

### Post by colintivy on 2008-10-10
Hi folks!

I have posted this qery in Absolute Beginner but without response. I beg your patience in posting it here.

I have migrated my Voyager 210 form my Win98SE tower to My Ubuntu driven laptop. I find that on power-up my network ikon appears to have a wired connection and all the green lights are on at the router. However if I fire up Firefox 3 it gives me "Page load error" and "Address unknown". If I unplug the Ethernet cable and reconnect it, the ikon shows its little twiddle and bingo Firefox connects correctly. It clearly learns something in the process but what do you think the setting is that it lacks? I have the primary secondary and tertiary DNS addresses for Plus.net listed in my network which worked with IE6. 

Guidance appreciated pleas:confused

colintivy:confused:

---

### Post by Mister.Vash on 2008-10-11
First thing to take a look at - when you are getting those page load errors, open up a gnome-terminal window and see if you get a response pinging something.  Try to ping google.com and see if it resolves and you get a response back.  If you don't get a reply, or it isn't able to resolve the address, the issue is not firefox, it is something with the network.  

If you do get a response from the pings and firefox is not working, double check and make sure that it isn't set to 'work offline'.  Check for a tick next to 'Work Offline' via the firefox File menu.

If it's not offline, and your ping is working, try closing and opening firefox again and see if works - try to open up the the site you were pinging ( you could leave ping going in the background while you were testing ).  

If it still doesn't work, try the ip address of whatever you were pinging rather than the name.  

And if that still isn't going anything close firefox and start firefox from a gnome-terminal window - that window will output error message and status messages if firefox sends them - try going to the site you were pinging again (by name), then unplug the cable and plug it back in to see if anything shows up in the gnome-terminal window you started firefox from.


Post back how the tests went, depending on what it does, we may need to get some further information, or run some other tests or get some output from the logs.

---

### Post by elj4176 on 2008-10-11
I'm seeing the same problem with both firefox and epiphany while opera works fine. I can check 'work online' and it works fine. It just is defaulting to 'offline' for some reason.
I'll add that I'm running 8.10 if that makes a difference.

---

### Post by colintivy on 2008-12-05
Hi folks,

Been distracted by other matters but still have not resolved my access to web site problem. What I have found out is that Firefox does occasionally make connect correctly. This is certainly evident when the Update Manager has some updates available before I start Firefox.If I let the updates load then open Firefox it connects immediately. Letting the system wait for some time after booting up will sometimes cure the problem. But I have tried to do this after a 20 minute wait without result as well. What does clear it is to use Network Configuration to tell me that Auto configuration is set and if I deselect it and reselect it and the Reconfiguration is carried out, connection is immediate. It seems to need the shot in the arm to achieve the desired result. I do switch off my router as a matter of routine overnight but when it comes on it soon tells methat the connection, as far as its lights are concerned, is OK.It seems as thought there is a degree of amnesia present.

colintivy :confused

---

### Post by philinux on 2008-12-05
One thing to try.


Tools>options>Advanced>network>settings

Make sure its set to "No Proxy"

---

### Post by colintivy on 2008-12-06
> **philinux said:**
> One thing to try.


Tools>options>Advanced>network>settings

Make sure its set to "No Proxy"
Hi Phil,

I am not sure that I am missing something. I am on Hardy and my settings panel does not have any mention of "No Proxy". It does have an option (which is not ticked) to "allow roaming" I am wired to a BT 200 router and dchp is selcted. Strangely today connection was quite normal after about 10 minutes of booting up.

colintivy :-\

---

### Post by GuruX on 2008-12-12
> **colintivy said:**
> Hi Phil,

I am not sure that I am missing something. I am on Hardy and my settings panel does not have any mention of "No Proxy". It does have an option (which is not ticked) to "allow roaming" I am wired to a BT 200 router and dchp is selcted. Strangely today connection was quite normal after about 10 minutes of booting up.

colintivy :-\

I'm sure that philinux refers to the menu in firefox, not in gnome. Try that.

---

### Post by colintivy on 2008-12-12
Hi GuruX,

I must be thick but I cannot find the menu in Firefox (3) or anywhere else. Please put me out of my misery!

colintivy :-\

PS Everything looks as though DHCP is there and working, but when I fail to connect and go via Admin to Network Settings, select Wired Connection (which shows dhcp) untick which runs  and reset the tick, but I know that it does not do anything apart from shjowing activity.If I then untick again I get the "Changing interface config" remark and all is well. You can see why I call the problem amnesia.

---

### Post by ravl on 2008-12-12
The next time it's not working, try this without changing any settings or unplugging the cable:

```
sudo dhclient <interface>
```

Replace <interface> with the proper interface name listed in ifconfig: eth0, eth1, etc.

---

