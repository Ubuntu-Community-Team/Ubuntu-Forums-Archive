---
title: "Inspiron 8600 and UBUNTU - (Wireless Working Yet)?"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by persis on 2005-04-06
What's up you crazy ubuntu freaks :)  

Okay, migrated to ubuntu on both my desktops, but have yet to take on the marriage of ubuntu and an Inspiron 8600.

I've heard there are issues - not detecting integrated Wireless?

Has this been resolved yet?  If it has I'm migrating - if not, it's solo windows until there is support for the on board wireless.

get back to me playas -

---

### Post by blueplazma on 2005-04-06
I have an Inspiron 8600 with the Intel/PRO Wireless 2200 (b/g).  It auto-detected it fine.  I haven't really tried setting WPA up yet, but wpasupplicant claims to the suppor the ipw2200 driver, so it should work.

---

### Post by persis on 2005-04-07
[QUOTE=blueplazma]I have an Inspiron 8600 with the Intel/PRO Wireless 2200 (b/g).  It auto-detected it fine.  I haven't really tried setting WPA up yet, but wpasupplicant claims to the suppor the ipw2200 driver, so it should work.[/QUOTE]


That's good news - it doesn't hurt to give it a run.  I'll be doing a dual XP / Ubuntu on the laptop, so if wi falters I can just bootup xp.

---

### Post by blueplazma on 2005-04-08
Good luck with that.

---

### Post by Legion on 2005-04-08
[QUOTE=blueplazma]I have an Inspiron 8600 with the Intel/PRO Wireless 2200 (b/g).  It auto-detected it fine.  I haven't really tried setting WPA up yet, but wpasupplicant claims to the suppor the ipw2200 driver, so it should work.[/QUOTE]

wpa_supplicant does indeed support ipw2200 - I'm running Gentoo right now on my Inspiron 6000 and wpa_supplicant gets my ipw2200 wireless card on my WPA encrypted network.

---

### Post by wylie348 on 2005-04-09
I have been using my inspiron 8600 (with the centrino 2100) and it has worked flawlessly from 4.10 to 5.04.  No problems, just be careful when using WEP - you should use a ten-digit password on your wireless AP - seems to work better for me.  There are still issues where it is a little flaky when changing network settings for other environments (Changing the WEP to a different value on another net), but for the most part it works really well!
 :-P

---

### Post by blueplazma on 2005-04-09
[QUOTE=Legion]wpa_supplicant does indeed support ipw2200 - I'm running Gentoo right now on my Inspiron 6000 and wpa_supplicant gets my ipw2200 wireless card on my WPA encrypted network.[/QUOTE]

Could you post that config?  It seems to work better in theory than in practice for me.  This is my current /etc/wpasupplicant.conf file:
```

#home blueplazma network with WPA
network={
		ssid="blueplazma"
		scan_ssid=1
		key_mgmt=WPA-PSK
		psk="supersecretpassword"
}

```

---

### Post by blawson327 on 2005-04-10
I installed hoary and my ipw2200 was detected fine, but I can not get it to connect to my AP. I've checked and rechecked and rechecked the WEP key, set for DHCP but it still will not work. I havent got around to try updateing the firmware and drivers yet but I may try that unless anyone else has any ideas

---

