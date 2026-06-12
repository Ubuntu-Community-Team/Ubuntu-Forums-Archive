---
title: "How to install printer (system-config-printer broken)"
date: 2010-06-30
forum: Hardware
---

### Post by b.friedrich on 2010-06-30
Dear all,

I am using KUbuntu jaunty and want to install a HP K1663 printer.
This printer is not yet supported by hplip v.3.9.2 which belongs to my current release 'jaunty', but it is supported by hplip v3.9.8 from the next release 'karmic'. 

So this is what I tried
- changing all instances of 'jaunty' to 'karmic' in etc/apt/sources.list
- sudo apt-get update
- run kpackagekit to install the v3.9.2 version of hplip and hplip-data
--> some dependencies also got resolved and now the printer setup app from system configureation does not work any more
- I tried reinstalling system-config-printer-kde for jaunty, no success.

Is there a way to get the printer setup app running again?
Can I install my printer in a different way?

I am still a linux beginner, 
and this is really hard for me.

Any help appreciated
Benjamin

---

