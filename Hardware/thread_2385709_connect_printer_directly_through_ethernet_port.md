---
title: "connect printer directly through ethernet port"
date: 2018-02-23
forum: Hardware
---

### Post by oldmanukko on 2018-02-23
i acquired an older thermal printer and would like to hook it up without buying more hardware. it does not have usb or bluetooth. only an ethernet port. i believe it could be possible for me to connect it directly to my computer. however, i don't know how to do that or what to google for. using terms like 'printer' and 'ethernet' and 'port' are a lil vague. i seem to have found a response saying that connecting directly with a patch cable should do the trick. however, my printer is not obtaining an IP address so that i can then setup the print driver.

sorry, clueless here..

some help or a lil insight would be much appreciated.

thanks

---

### Post by Dennis N on 2018-02-23
I set up my network printer this way:

Connect ethernet cable from printer to router, not the computer. Turn printer on. It should acquire an IP address on you LAN from the router. Then, in the computer's printer setup dialog, there is an option to find network printer. Once it is found, continue with the setup steps in the printer dialog. 

Note: It's best to give the printer a static IP address so it won't change in the future. I did that through my router's on-screen set up dialog.

---

### Post by slickymaster on 2018-02-23
Thread moved to **Hardware** for a better fit

---

### Post by oldmanukko on 2018-02-23
thank you

---

### Post by oldmanukko on 2018-02-23
this printer/computer combo will be in "the field" and "they" need a minimal setup. (want the weight and number of pieces of equipment to be minimal) looking for a way for the printer to connect directly to the laptop. (and sadly the thermal printer picked does not have usb or bluetooth)

---

### Post by sccman on 2018-02-24
I have a couple of questions:
1) What's the printer make and model?
2) What Linux/Windows/Mac versions will be running the printer?

---

### Post by oldmanukko on 2018-03-01
i got this to work. once my printer was connected. (for my printer i use telnet) i then telnet into the admin interface and gave it a static ip. and then with a static ip i setup a printer through cups with the ip i assigned it.


```
/etc/network/interfaces
===========================================
    auto eth0
    allow-hotlug eth0
    iface eth0 inet static
    address 192.168.3.1
    netmask 255.255.255.0



/etc/dnsmasq.d/dnsmasq.eth0.conf
===========================================
    interface=eth0
    listen-address=192.168.3.1
    bind-interfaces
    dhcp-range=192.168.3.10,192.168.3.254,12h
```


(note: my Pi is also a hotspot. in order to listen on multiple interfaces i needed to delete dnsmasq.conf and put my interface configurations into the /etc/dnsmsq.d directory. my pi accepts connections on eth0 for the printer and wlan0 for the hotspot. but, if have an /etc/dnsmasq.conf file, you may put this in that file)

---

