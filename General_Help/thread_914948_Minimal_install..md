---
title: "Minimal install."
date: 2008-09-09
forum: General Help
---

### Post by pedrom169 on 2008-09-09
been looking at this

[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

and i was wondering do i need a wired connection to get all the required packages as i only have wireless connection available.

so is there any other way of getting these files?

Cheers
Peter

---

### Post by Bucky Ball on 2008-09-09
As long as you have access to the internet you shouldn't have a problem. Your only issue would be speed, all depending on how much data you are looking to download.

---

### Post by dimitarc on 2008-09-09
If you have wireless conection I supose you have more memory than 192 MB of ram. Have you tried to install those packages trough wireless? Does it not work? What error do you get?

---

### Post by pedrom169 on 2008-09-09
i havent tried yet with wireless. but i have look at APTonCD is that any use?

---

### Post by snowpine on 2008-09-09
It really depends on your wireless card. Some work out-of-the-box in Ubuntu, in which case you'd be fine. But some require downloading additional drivers, which is a catch-22 if you don't have a wired connection. 

Your best bet is to either boot from the Live CD (which is probably not an option with your low ram) to see if your wireless works, or search for your specific wireless card to see if others on the Forums have had any luck.

---

### Post by Bucky Ball on 2008-09-10
Type:

lspci

in a terminal and hunt down your wireless card, unless it is usb plug-in type of course. Then you can get the details from it.

---

### Post by Vivaldi Gloria on 2008-09-10
You can do everything a minimal cd does with the alternate cd as well. By the way there is a bug in Hardy installer which makes it impossible to install it in computers with less than 128MB of ram. See CLI in my sig.

---

