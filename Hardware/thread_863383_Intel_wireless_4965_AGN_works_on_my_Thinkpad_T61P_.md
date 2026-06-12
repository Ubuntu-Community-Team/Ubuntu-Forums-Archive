---
title: "Intel wireless 4965 AGN works on my Thinkpad T61P under Ubuntu 8.04"
date: 2008-07-18
forum: Hardware
---

### Post by perdubug on 2008-07-18
Finally got 4965 AGN running on the T61P with Ubuntu 8.04! A big problem I met is wireless network.After referencing [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html), it works.

Network environment:
wireless router: D-Link DI-624+A,DHCP service is active,WPA-PSK,TKIP,password.

Steps:
$sudo vim /etc/network/interfaces
Comment out everything other than “lo” entries in that file and save the file.

$sudo touch /etc/default/wpasupplicant
Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file.

Reboot your T61P.Note:Please do not reboot your laptop by using 'sudo /etc/init.d/dbus restart' mentioned by above link, because I got Ubuntu freeze then.

Once you login back in to your laptop you can select your wireless network by left-clicking the network manager icon in Gnome.It will prompts for password, type, etc. Input your router's password and select 'WPA Pers...' and 'Auto...'. 

After that my wireless network was connected and working fine.

---

### Post by rob1101 on 2008-07-26
I followed the instructions and i still cannot for the life of me get it to authenticate.

this are my files

 /etc/network/interfaces
```

auto lo
iface lo inet loopback

```

/etc/default/wpasupplicant
```

ENABLED=0

```

Please, i could use some help

---

### Post by b:z on 2008-08-02
i confirm it works great. I can access to my home wireless AP which is configured MAC security.
Thanks for good instruction.

There is also a matter on T61p, the wireless led does not show status "on". Is there anyway to fix it?

Thanks again.

---

