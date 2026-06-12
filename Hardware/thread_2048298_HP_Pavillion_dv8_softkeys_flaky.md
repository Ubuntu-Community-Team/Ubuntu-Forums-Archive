---
title: "HP Pavillion dv8 softkeys flaky"
date: 2012-08-26
forum: Hardware
---

### Post by Arctother on 2012-08-26
Hello,

My HP Pavillion dv8 laptop includes a row of "softkeys" up above the keyboard.

They include volume, fast forward, stop, rewind etc, and one for the wireless. The wireless one has always been flaky - turning itself off and on randomly. Since "upgrading" to 12.04 pernicious pangolin, the button changes its mind every 5-15 minutes (worse than it was), and once it turns the net off, the softkey does not turn it back on - the wifi button turns but the system continues to believe the hardware says "wifi off".

stephan@Ursula:~$ sudo rfkill list all

1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
10: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

I am using the KDE interface, if that matters.

A) How do I remove the package / driver / set the system to ignore the softkeys in their entirety ? I want Linux to not even know they exist - in part because ALSA/ Kmixer do not play well with the volume control anyway, so they are useless to me.

B)If anyone has any ideas as to why it turns the net off, and has ideas about persuading it to not turn the net off - I don't really care. Thanks anyway. I just want the softkeys to go away.

Thanks !
Arctother

---

