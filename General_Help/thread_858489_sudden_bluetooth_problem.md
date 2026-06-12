---
title: "sudden bluetooth problem"
date: 2008-07-13
forum: General Help
---

### Post by PRichi on 2008-07-13
Hello,
I have a sudden problem with the bluetooth connection to my LG KE970.
I installed the packages and the "pairing", everything worked fine, and as a newb i was suprised that it was so easy. 
But now i have a problem, when i try to send a file to the phone it says that the Host is down, when i check that bluetooth is turned on and click "Retry" it says: "Method "CreateBluetoothSession" with signature "ssb" on interface "org.openobex.Manager" doesn't exist".
When i try to browse the device, it seems to do nothing, but after about 8 minutes it says 

"Couldn't display "obex://[XX:XX:XX:XX:XX:XX]/". Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again."

I restarted bluetooth on my laptop and phone, but it was no solution.
Sending a file from the phone to the pc surprisingly works fine. 

When I type "hcitool scan" in the terminal, it finds my phone.

The connection was already working yesterday evening and i don't know why it does not work now... I remember that i did updates recommended by the update manager yesterday evening but i don't know if that is the problem...

I would be thankful for every suggestion.

thanks in advance!

---

### Post by fragos on 2008-07-13
Install blueman from the Ubuntu repository. It's a GUI bluetooth manager that makes things much easier to deal with. No command line required.

---

### Post by PRichi on 2008-07-13
Thanks for the hint, this blueman is really great.
I just updated some bluetooth packages and restarted my phone, and now it works!

Thanks a lot.

---

### Post by jabezkaiser on 2008-09-17
I don't found any pakage named blueman, does it changed to other named?

---

### Post by fragos on 2008-09-17
It is in the Ubuntu repositories. Running the Synaptic Package Manager and doing a search for "blueman" should find it. If not, make sure that in the Software Sources Preference you've checked the boxes for "universe" and "multiverse".

---

### Post by teledyn on 2009-04-26
I have all those repositories selected under 8.10, but there is no blueman found in the listings.

---

### Post by fragos on 2009-04-26
> **teledyn said:**
> I have all those repositories selected under 8.10, but there is no blueman found in the listings.

[http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html](http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html)

---

