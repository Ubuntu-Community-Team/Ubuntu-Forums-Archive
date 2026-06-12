---
title: "wifi problem"
date: 2009-05-17
forum: Hardware
---

### Post by andrey1978 on 2009-05-17
[SIZE=3][FONT=Calibri]Hi All![/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I use HP tx2650 with Broadcom 4312, driver has been installed and active. The problem is: I don’t see “my” wifi-network, but at the same I see “other” networks which are presented in my building. I can say for sure “my” network is active and works properly as this message is being written from my Vista-desktop using “my” network. Could you please advice something? [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I’m new in Ubuntu and so I would like to ask you to write advices as detailed as possible :-).[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Thank you in advance![/FONT][/SIZE]

---

### Post by devosion on 2009-05-17
Run this in a terminal and see if your wireless network appears.

> 
sudo iwlist scan


---

### Post by andrey1978 on 2009-05-17
> **devosion said:**
> Run this in a terminal and see if your wireless network appears.
 
using yhis somand I can see "other" nets....
it's some kind of magic....

---

### Post by andrey1978 on 2009-05-17
Now it works,
but why????? I did nothing..
Any idea?
thank you!

---

### Post by devosion on 2009-05-17
I can't say for sure. That command should have just scanned available networks in your area. The fact that it worked afterwards is just luck. :) Enjoy.

---

### Post by andrey1978 on 2009-05-17
> **devosion said:**
> I can't say for sure. That command should have just scanned available networks in your area. The fact that it worked afterwards is just luck. :) Enjoy.
but i had a s**x with this issue some during some days :-)

---

### Post by Favux on 2009-05-17
Hi andrey1978,

Does your router have a hidden SSID?

---

