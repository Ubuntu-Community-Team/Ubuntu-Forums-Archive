---
title: "ipw3495 and wpa2 gutsy x86_64"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by lynrees on 2007-11-04
I have a Toshiba u300 laptop with intel ipw3495 wireless, running gutsy 64bit. I've found posts where people have problems, but none like mine.

I can connect to my Linksys wireless ADSL router with no security, but not with WPA2.

Using wpa_supplicant on the command line, it tells me that it "Failed to set encryption".

My Samsung R50 with ipw2200 connects to the router fine with WPA2 however.

I'll tried with the gutsy live disk to confirm that it wasn't something I did, with the same result. I also tried with a live 32bit OpenSUSE 10.3, and that worked fine!

Any ideas?

Thanks.

---

### Post by lynrees on 2007-11-06
Is there an element of insanity in replying to yourself?!?!

Anyway, I've installed Gutsy 32bit, and now WPA2 works!

Can't see all 4GB of RAM though!?!

I'd dearly like to get this thing working properly, preferably with 64bit.

Any use trying to get the iwlwifi driver running in 64bit?

---

### Post by tonyric on 2007-11-06
Are you trying WPA Personal or WPA Enterprise? Personal works fine on my son's laptop (Thinkpad with 3945)

---

### Post by lynrees on 2007-11-06
At home: Personal, in work: Enterprise. Same results with both. :(

---

### Post by Seisen on 2007-11-06
Have you created a wpa_supplicant.conf file, if you have post it here but take out your WPA2 key and your ssid. I think I know what the problem is because I messed with WPA2 for about two weeks before I finally got it working.

---

### Post by lynrees on 2007-11-06
I just used a very simple one like this:

 network={
               ssid="home"
               scan_ssid=1
               key_mgmt=WPA-PSK
               psk="very secret passphrase"
          }

Thanks for your help.

---

### Post by WadiJM on 2008-03-23
I have the same problem. Please let me know if you found any solution. 


*Sometimes I just miss guindows.....*

---

### Post by lynrees on 2008-03-23
No luck as of yet... It seems I have the same problem with Hardy Heron so far also, having tried with the live CD.

Does no one have any idea? :(

---

