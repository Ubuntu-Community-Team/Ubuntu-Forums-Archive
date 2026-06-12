---
title: "Strange wifi problem"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by Carandol on 2006-04-06
When I use the Ubuntu live CD on my desktop PC, it detects my wifi card (a D-Link DWL-G520+) and detects the essid with no problem at all. But now that I've installed Ubuntu, it refuses to detect the essid. The card is installed, but it's not detecting a signal. Go back to the live CD, and the signal's detected again. I can only assume that some part of the installed system is interfering with the card. I've been through the wifi troubleshooting guide and failed to find any problem (the setup appears exactly the same as it is with the live CD). Any suggestions appreciated, because I'm at my wit's end, and can't connect to the internet any other way!

---

### Post by sadjack on 2006-04-06
I had a similar problem with fedora. I can only think that there are drivers in the live cd that are not installed when you make a full install.

I solved my problem then by getting drivers from the whax live cd - they were in a folder called firmware - perhaps you could look to see if there is a similar folder on the ubuntu live cd, sorry I don't have one to look myself.

However I must say that when I got rid of fedora and installed breezy, it identified and ot my card to work straight off.

Someone may have better ideas but thats my twopennarth

Cheers

---

### Post by Carandol on 2006-04-12
I did get it working in the end -- it required additional firmware and the blacklisting of the original driver. Now it's working fine!

---

