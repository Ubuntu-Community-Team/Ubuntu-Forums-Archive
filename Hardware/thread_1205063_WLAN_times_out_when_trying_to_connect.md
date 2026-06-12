---
title: "WLAN times out when trying to connect"
date: 2009-07-05
forum: Hardware
---

### Post by GSMX on 2009-07-05
Hi all,

Today, my sony vaio vgn-fw31zj couldn't connect via wifi anymore. Connecting already was a problem lately, but somehow it always worked after some minutes, today it didn't as it kept asking for the WPA key, but when I entered it, the prompt came up again after some time, when I clicked 'show password' it came up with "d8b5a9b352a255105da0d30f2d0a850b649b5a315f5a773d05902346b5f72" which is kind of different from our 10-character WPA-key. I have no idea where to look, so here are parts some syslogs (I only copied some parts, multiply every block with 12 and you have the actual log ;))

kern.log / debug:```
Jul  5 16:06:16 ubuntulaptop kernel: [  913.517990] wlan0: authenticate with AP 00:24:17:04:8b:87
Jul  5 16:06:16 ubuntulaptop kernel: [  913.520142] wlan0: authenticated
Jul  5 16:06:16 ubuntulaptop kernel: [  913.520150] wlan0: associate with AP 00:24:17:04:8b:87
Jul  5 16:06:16 ubuntulaptop kernel: [  913.522820] wlan0: RX ReassocResp from 00:24:17:04:8b:87 (capab=0x411 status=0 aid=2)
Jul  5 16:06:16 ubuntulaptop kernel: [  913.522825] wlan0: associated
Jul  5 16:06:27 ubuntulaptop kernel: [  924.520445] wlan0: disassociating by local choice (reason=3)
Jul  5 16:06:29 ubuntulaptop kernel: [  926.409464] wlan0: authenticate with AP 00:24:17:04:8b:87
Jul  5 16:06:29 ubuntulaptop kernel: [  926.411395] wlan0: authenticated
Jul  5 16:06:29 ubuntulaptop kernel: [  926.411402] wlan0: associate with AP 00:24:17:04:8b:87
Jul  5 16:06:29 ubuntulaptop kernel: [  926.414079] wlan0: RX ReassocResp from 00:24:17:04:8b:87 (capab=0x411 status=0 aid=2)
Jul  5 16:06:29 ubuntulaptop kernel: [  926.414085] wlan0: associated
Jul  5 16:06:40 ubuntulaptop kernel: [  937.410006] wlan0: disassociating by local choice (reason=3)
Jul  5 16:06:42 ubuntulaptop kernel: [  939.239375] wlan0: authenticate with AP 00:24:17:04:8b:87
Jul  5 16:06:42 ubuntulaptop kernel: [  939.245335] wlan0: authenticated
Jul  5 16:06:42 ubuntulaptop kernel: [  939.245343] wlan0: associate with AP 00:24:17:04:8b:87
Jul  5 16:06:42 ubuntulaptop kernel: [  939.248502] wlan0: RX ReassocResp from 00:24:17:04:8b:87 (capab=0x411 status=0 aid=2)
Jul  5 16:06:42 ubuntulaptop kernel: [  939.248508] wlan0: associated
Jul  5 16:06:53 ubuntulaptop kernel: [  950.249411] wlan0: disassociating by local choice (reason=3)
Jul  5 16:06:55 ubuntulaptop kernel: [  952.213447] wlan0: authenticate with AP 00:24:17:04:8b:87
Jul  5 16:06:55 ubuntulaptop kernel: [  952.219726] wlan0: authenticated
Jul  5 16:06:55 ubuntulaptop kernel: [  952.219733] wlan0: associate with AP 00:24:17:04:8b:87
Jul  5 16:06:55 ubuntulaptop kernel: [  952.222414] wlan0: RX ReassocResp from 00:24:17:04:8b:87 (capab=0x411 status=0 aid=2)
Jul  5 16:06:55 ubuntulaptop kernel: [  952.222420] wlan0: associated
Jul  5 16:07:02 ubuntulaptop kernel: [  958.950554] wlan0: disassociating by local choice (reason=3)
Jul  5 16:07:13 ubuntulaptop kernel: [  970.414102] wlan0: authenticate with AP 00:24:17:04:8b:87
Jul  5 16:07:13 ubuntulaptop kernel: [  970.416075] wlan0: authenticated
Jul  5 16:07:13 ubuntulaptop kernel: [  970.416081] wlan0: associate with AP 00:24:17:04:8b:87
Jul  5 16:07:13 ubuntulaptop kernel: [  970.418776] wlan0: RX ReassocResp from 00:24:17:04:8b:87 (capab=0x411 status=0 aid=2)
Jul  5 16:07:13 ubuntulaptop kernel: [  970.418781] wlan0: associated
Jul  5 16:07:24 ubuntulaptop kernel: [  981.419538] wlan0: disassociating by local choice (reason=3)
```

wpa_supplicant.log```
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:24:17:04:8b:87 (SSID='SpeedTouch1B16BA' freq=2412 MHz)
Associated with 00:24:17:04:8b:87
Authentication with 00:24:17:04:8b:87 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:24:17:04:8b:87 (SSID='SpeedTouch1B16BA' freq=2412 MHz)
Associated with 00:24:17:04:8b:87
Authentication with 00:24:17:04:8b:87 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:24:17:04:8b:87 (SSID='SpeedTouch1B16BA' freq=2412 MHz)
Associated with 00:24:17:04:8b:87
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Authentication with 00:00:00:00:00:00 timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:24:17:04:8b:87 (SSID='SpeedTouch1B16BA' freq=2412 MHz)
Associated with 00:24:17:04:8b:87
Authentication with 00:24:17:04:8b:87 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:24:17:04:8b:87 (SSID='SpeedTouch1B16BA' freq=2412 MHz)
Associated with 00:24:17:04:8b:87
```

---

### Post by GSMX on 2009-07-07
anyone?

---

### Post by wojox on 2009-07-07
This may help troubleshoot you problem

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

