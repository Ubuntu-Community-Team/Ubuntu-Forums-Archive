---
title: "Wireless problem Toshiba L755"
date: 2011-08-13
forum: Hardware
---

### Post by mchenier1 on 2011-08-13
Hi there,

Just bought a new Toshiba laptop L755 and installed Ubuntu 11.04 on it. Every went fine except I can't connect to Internet with the wifi connection. I'm connect to the wireless router but I can't access Internet. 

There is no physical switch to on/off the wireless connection on the laptop but the FnF8 keys seem to have that function. But it doesn't seem to work on Ubuntu. 

I have run de nm-tool and my wireless is connected. Must have something to do with the wireless ''switch''.

No problem when I use Windows 7 on it. Anybody have a clue?

Thanks for your advice,

Martin.

---

### Post by mchenier1 on 2011-08-13
I found my problem. I was able to ping my router and [www.google.com](www.google.com).

The problem was ipv6 in Firefox, I had to disable it with:

about:config and search for:

network.dns.disableIPv6

and set it to TRUE

Internet was accessible with Chromium. Curious problem...never had that before...

Thanks for your interest,

Martin

---

### Post by mchenier1 on 2011-08-13
Well, after all, the problem still there....don't know what is going on.

---

### Post by mchenier1 on 2011-08-16
Problem solved. The problem was the drivers, I updated them:

sudo iwconfig wlan0 rate 54M
sudo apt-get install build-essential
wget [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.1/compat-wireless-3.1-rc1-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.1/compat-wireless-3.1-rc1-1.tar.bz2)
tar jxvf compat-wireless-3.1-rc1-1.tar.bz2
cd compat-wireless-3.1-rc1-1
make 
sudo make install
sudo make unload

restart computer

---

