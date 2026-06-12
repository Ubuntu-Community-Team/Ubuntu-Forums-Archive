---
title: "How to set static Ip address?"
date: 2008-11-04
forum: General Help
---

### Post by davethewave83 on 2008-11-04
I click the connection icon in gnome, click "manual configuration" Unlock the settings, then click "Wireless Connection and click Properties, I disable "roaming mode" and set configuration as "Static" and punch in my desired address 192.168.1.7 (which is it's current address, I just don't want it to change) subnet 255.255.255.0, gateway address 192.168.1.1, under password type I choose WEP ASCI because there is no option for WEP 128, I punch in the ESSID exactly as it is then press OK... but it never connects to anything. Any reason why roaming would work while static would not work with identical settings? I am confused. Any way to make this work?

---

### Post by mikewhatever on 2008-11-04
You may need to restart the network after entering all of these by issuing <sudo /etc/init.d/networking restart>.

---

### Post by Marvindreyer on 2008-11-04
May be contact your ISP, they are the right people to tell you about it.

---

### Post by Peter09 on 2008-11-04
Firstly has your wireless router got DHCP set. If so you should really set any static wireless addresses through that.

Can you confirm that you are using a wireless router to connect to the internet, what type? If so do you know how to mak DHCP provide a static address to a device?

---

### Post by scouser73 on 2008-11-04
> **davethewave83 said:**
> I click the connection icon in gnome, click "manual configuration" Unlock the settings, then click "Wireless Connection and click Properties, I disable "roaming mode" and set configuration as "Static" and punch in my desired address 192.168.1.7 (which is it's current address, I just don't want it to change) subnet 255.255.255.0, gateway address 192.168.1.1, under password type I choose WEP ASCI because there is no option for WEP 128, I punch in the ESSID exactly as it is then press OK... but it never connects to anything. Any reason why roaming would work while static would not work with identical settings? I am confused. Any way to make this work?

You can follow the instructions in this tutorial; [http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html]("http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html")

---

### Post by davethewave83 on 2008-11-04
> **Peter09 said:**
> Firstly has your wireless router got DHCP set. If so you should really set any static wireless addresses through that.

Can you confirm that you are using a wireless router to connect to the internet, what type? If so do you know how to mak DHCP provide a static address to a device?

Yes I am using a wireless router, I am not completely daft :p besides it does connect via roaming mode. 

it is a Linksys WRT54GL broadband router version 1.1,

 When I used that other unmentionable OS I did not need to set anything in the router, just in that other unmentionable OS under TCP/IP properties and it always worked. 

I am thinking there must be a bug somewhere in Ubuntu's network program.

---

