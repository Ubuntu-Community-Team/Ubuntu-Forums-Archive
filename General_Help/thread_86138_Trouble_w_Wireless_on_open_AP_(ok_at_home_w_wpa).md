---
title: "Trouble w/ Wireless on open AP (ok at home w/ wpa)"
date: 2005-11-04
forum: General Help
---

### Post by carlos_ on 2005-11-04
Hello,

I'm having trouble connecting to an open access point at the local coffee shop.

What's frustrating is that I have been able to set up ndiswrapper and wpa successfully with this computer and have had no trouble with my home router.

When I run iwconfig I see the card which makes me believe ndiswrapper is coming up ok.

However, when I run "sudo iwconfig wlan0 essid coffee_shop_id" I see no error message, but when I run iwconfig it has not associated with the AP.

Does anyone have any ideas as to what might be going on?  What log I can look at for errors?  Do I need to disable wpa_supplicant somehow?

Thanks in advance.

---

### Post by carlos_ on 2005-11-04
Sorry to reply to my own post... I shoulda' tried this before posting.

I simply brought down the interface "sudo ifdown wlan0" and retried "sudo iwconfig wlan0 essid coffee_shop_id".

It works!

---

