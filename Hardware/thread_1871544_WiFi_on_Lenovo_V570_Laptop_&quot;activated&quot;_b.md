---
title: "WiFi on Lenovo V570 Laptop &quot;activated&quot; but not streaming?"
date: 2011-10-29
forum: Hardware
---

### Post by TasteDaHate on 2011-10-29
So, hi. I'm new to actually posting and getting serious about ubuntu even though I have played around with it on, and off since 8.10. For lack of a better word, I used "streaming" .By streaming, I mean no data is being sent back and forth. I download something in the Ubuntu Software Center, I read the progress and it says sending 0kb/s, as well as mmy browser does not load sites.I have broadcom wireless with what was bcim4313 I believe it was called, I got the wireless to even show up, with this work-around..

[B]sudo rmmod -f acer-wmi 
sudo rfkill unblock all 
sudo rfkill list all

[/B]Is my wireless extremely slow, is there an update I need, what should I do? This is one of those things that make me want to go back to windows. I need my wireless because my wired connection is terrible to connect.

---

### Post by varunendra on 2011-10-30
Hi TasteDaHate, and welcome to the forums!

Please open a terminal, run and post back outputs of the following commands:
```
sudo lshw -C network
lsmod
```

Please wrap the outputs in 'code' tags by selecting (only) the pasted output, then clicking on the **#** symbol at the top of the edit box in which you write your post.

---

