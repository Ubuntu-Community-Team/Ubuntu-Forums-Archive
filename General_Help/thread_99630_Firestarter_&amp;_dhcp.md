---
title: "Firestarter &amp; dhcp"
date: 2005-12-05
forum: General Help
---

### Post by SilentK on 2005-12-05
I am having issues setting up internet connection sharing via firestarter.

Here's the setup I have. I have a wireless internet card (wlan0) and a ethernet card. (eth0) my internet connection is from wlan0. I want other computers to be able to dhcp and connect from eth0.

My configuration for eth0 is the following.

Configuration: Static
Ip Address: 192.168.0.1
subnet mask: 255.255.255.0
gateway (left this blank as instructions for firestarter said)

I have attached a screenshot of my firestarter configuration.
as well as a screenshot of an error I am getting when I start the firewall along with dmesg output.

It gives me this error when I start the firewall and says it has failed to start however it says that's it's active a few seconds after the error message.

I have tried dhcping from another box and it fails to assign an ip address.

Any ideas on how to fix this?

---

### Post by SilentK on 2005-12-06
Any ideas? Help would be greatly appreciated.  I am somewhat of newbie when it comes to linux.

---

### Post by moberry on 2005-12-06
I use firestarter for my network. I do not use the firestarter built-in dhcp server. Based on your error it looks like your firewall is blocking dhcp (port 67) you will want fix this. It is in the wizard under "Address is assigned via dhcp" or you can set a policy allowing for everyone. If you want help configuring a traditional dhcp server let me know... hope this helps.

---

### Post by leeb on 2005-12-06
try subnet mask: 255.0.0.0  may be it will help.

---

### Post by SilentK on 2005-12-07
Initially I was going to use dhcp3 but on the firestarter site they sugged dhcp.

I'll try it with dhcp3 as well the different subnet mask. Thanks, I'll let you guys know if it worked or not.

---

### Post by praetorian46 on 2005-12-07
I am having this same problem.  I don't think it's a firestarter problem because my dhcp server wasn't working before I installed firestarter and firestarter doesn't have a dhcp server built in it uses the systems dhcp server

---

### Post by SilentK on 2005-12-11
Well I got it working.

I installed the dhcp3-server package and followed the directions located at 
[http://ubuntuguide.org/#installdhcpserver](http://ubuntuguide.org/#installdhcpserver)

and now it works perfectly.

---

