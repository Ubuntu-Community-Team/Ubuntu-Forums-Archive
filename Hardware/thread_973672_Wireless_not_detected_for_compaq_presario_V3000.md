---
title: "Wireless not detected for compaq presario V3000"
date: 2008-11-06
forum: Hardware
---

### Post by vamsi2k on 2008-11-06
Dear All 
Iam relatively new to ubuntu. recently i moved from windows to ubuntu 8.1, and now facing problem for wireless hardware not been detected.

Some please suggest.

---

### Post by frank_costanza on 2008-11-18
I have a v3000 and am also having wireless problems. There are basically three options for enabling networking on the Broadcom 4311 wireless adapter (which is what all v3000's have I think). 
[LIST=1]
[*]Broadcom STA driver (also known as the wl driver)
[*]BCM43xx driver
[*]ndiswrapper
[/LIST]

My results with all three methods under Intrepid have been disappointing. When I first installed Intrepid, I used the Broadcom wl driver which you can enable by going to System > Administration > Hardware Driverts. There should be an option in the list for the Broadcom STA wireless driver (also known as the wl driver). You just have to click the button to activate it and reboot.

When using the wl driver, I can sometimes connect to my WPA2 protected network. Other times, it hangs while trying to obtain an ip address from my router. And the rest of the time, it doesn't even get that far, it just keeps prompting me to re-enter my WPA password. Anyway, I'd try the wl driver since that seemed to work the best of any of the other options in Intrepid. Make sure the wireless switch on the front of the computer is in the 'on' position. Give it a shot and let us know how it turns out.

I'd be interested to hear from anyone who has wireless working under Intrepid with a Compaq v3000.

---

