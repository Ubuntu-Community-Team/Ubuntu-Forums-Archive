---
title: "WPA2 broken on 9.04 i386?"
date: 2009-04-27
forum: Hardware
---

### Post by rvanderwerf on 2009-04-27
I installed 9.04 on 2 older dell laptops, (C400), and I can see my Linksys wireless network fine, but when I try to connect, WPA2 Personal is not in the list of options to chose for the key. If I pre-set one up in network manager, I can choose WPA2, but network manager will never use it to connect. I always have to pick the wireless network in the drop down list again, but I get hit with the prompt that doesn't have WPA/WPA2 as an option is this a bug in 9.04 or just a compatibility problem with older laptops? 

I'm curious if this feature is working for others.

---

### Post by aikiwolfie on 2009-04-27
I looked at the options I get on my Dell 1330n and it gives me "WPA & WPA2 Personal" and WPA & WPA2 Enterprise" as well as "WEP 40/128-bit Key", "WEP 128-bit Passphrase", "LEAP" and "Dynamic WEP (802.2x)".

---

### Post by rvanderwerf on 2009-04-27
If I click in network manager on the wireless network, I only get these options:

"WEP 40/128-bit Key", "WEP 128-bit Passphrase", "LEAP" and "Dynamic WEP (802.2x)"

However if I go to Edit Connections, and edit one, I have all choices listed. But it seems to ignore my  settings when I set the WPA2 passphrase, and when I click on the network browser to connect again, it just adds another entry into the wireless connections list.

---

### Post by supersnow on 2009-05-01
I am also having the same issues on my upgrade from 8 -> 9

---

### Post by klemperal on 2009-05-01
I'm having issues with this as well.  I had just assumed it was hardware related, but maybe not.

---

### Post by cwelch on 2009-05-06
I'm having this issue too. At school, we use WPA2 Enterprise with PEAP (i think?) and TKIP, and Enterprise doesn't even show as an option. Worked in 8.04 to upgrade to 8.10, and worked in 8.10 enough to make sure the machine was alive after the upgrade. Since putting on 9.04 it hasn't worked though. Any bug filed on this yet?

---

### Post by newbie09 on 2009-05-24
i am having the same problem which i am sure is linked to my issue with my secured network i am trying to connect in Ubuntu 9.04 Wubi ... does anyone have a solution???

P.S. my laptop is fairly new Asus A8S series

---

