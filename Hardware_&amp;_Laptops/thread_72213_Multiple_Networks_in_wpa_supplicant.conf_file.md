---
title: "Multiple Networks in wpa_supplicant.conf file"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by sigma2805 on 2005-10-05
Hello everyone,
has anyone been able to sucessfully configure two networks in the wpa_supplicant.conf file? ive been able to configure it to connect to my home network but not the school network. basically, the school network is open no authentication but after you get a ip address the first site that opens asks you to login to use the wireless network. its called Vernier Secure Logon. Anyway, below is my wpa_supplicant file. please let me know if there are any errors in it. Thanks!

ap_scan=2
network={
   scan_ssid=1
   ssid="myhome"
   psk="mypass"
   key_mgmt=WPA-PSK
   proto=WPA
}
ap_scan=2
network={
	scan_ssid=1
	ssid="school"
	key_mgmt=NONE
}

---

### Post by mlomker on 2005-10-05
Here's what I use and it works fine for two open networks.  I'm not sure what your scan commands do:

```

network={
        ssid="2409"
        key_mgmt=NONE
}
network={
        ssid="NETWORKING"
        key_mgmt=NONE
}

```

---

