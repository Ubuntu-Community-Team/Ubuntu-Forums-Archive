---
title: "Making a Server"
date: 2008-11-12
forum: General Help
---

### Post by Knuffle on 2008-11-12
I am trying to make a server out of one of my laptops. I installed Ubuntu Server Edition with no bells or whistles installed. I would like to know how to set it up do do what I need it to do. I would like it to act as a firewall for my wireless network so all communications have to go through it. I would also like a _local only_ SSH server so it cannot be attacked or be accessed from the internet. Any other things that you can think of for it to do would be appreciated. All help will also be appreciated. I am a total noob when it comes to networking, so thanks for your help in advance.

---

### Post by Tamalin on 2008-11-12
Ok, well, I have done this before, and the first thing I did was hook it up to an ethernet cord and install Apache Server.  (In synaptic if that is in ubuntu server, I used Hardy Desktop edition...)

---

### Post by Knuffle on 2008-11-12
I'm not looking for a web server. Just a server to do stuff with a local network.

---

### Post by daleus on 2008-11-13
if you install "openssh-server" in the config file (/etc/ssh/sshd_config) You can set what interface (IP Address) it listens on, as well as the port if you so choose (don't forget to uncomment the lines by removing the #)

If you want to use it as a firewall, there are a few tutorials that make use of iptables to create a decent enough router, they are easily found by google.

Also, if you want it to give DHCP addresses to your clients, you will need to install a dhcp server, there are plenty of them about on ubuntu and most of them are easily configurable.

---

### Post by adieb on 2008-11-13
Here is a How-To for Connection Sharing. I think you want to setup your "firewallmachine" as a gateway for the other maschines.

You will have to adjust the iptable-rules to your needs.
(man iptables ...)
[http://ubuntuforums.org/showthread.php?goto=newpost&t=713874](http://ubuntuforums.org/showthread.php?goto=newpost&t=713874)

Are you going to use the wireless network adapters? Because I am not sure, if that is so easy...


Good Luck

---

### Post by mcduck on 2008-11-13
a laptop as a firewall? Your problem is that most likely your laptop doesn't have two thernet connections. To use it as firewall you'd need two, one for the internet and other to connect to your local network.

Wireless interface won't help you unless your internet connection _is_ wireless or the laptop's wireless interface supports operating as an access point (and most of them don't).

(of course I might be wrong here, but single-interface firwall sounds quite funny to me, as both trusted and untrusted zones would be on the same interface..)

---

### Post by Knuffle on 2008-11-13
Ok, thank you. Yeah, I just realized that I would need a second eth0 port to make the firewall work. Anyways, I will look into the DNS server thing and see what that is. Thanks for your help so far. Also, is there anyway to have a small optional GUI so that everything would be normal unless I pressed something like ctrl alt F7?

---

### Post by binbash on 2008-11-13
> **Knuffle said:**
> Ok, thank you. Yeah, I just realized that I would need a second eth0 port to make the firewall work. Anyways, I will look into the DNS server thing and see what that is. Thanks for your help so far. Also, is there anyway to have a small optional GUI so that everything would be normal unless I pressed something like ctrl alt F7?

There is no gui at server edition.Tho you can use webmin for interface i guess

---

### Post by mcduck on 2008-11-13
If you want, you can just install any desktop environment you like. The default server install doesn't include any, as most of the time servers don't need to run any GUI.

For the most common desktops, you can just use the following command: "sudo apt-get install ubuntu-desktop" (replace ubuntu-desktop with kubuntu-desktop for KDE or xubuntu-desktop for XFCE4). This will install the DE and all the applications Ubuntu includes with it by default.

Of course it's also possible to install the DE without all extra applications, you'll probably find a thread with instructions and list of required packages somewhere on these forums.

Webmin is a nice solution as well, as it allows you to manage the server from your other computers (so the server doesn't even need a display or keyboard).

---

### Post by Knuffle on 2008-11-14
Ok, I have everything working how I want it to except I don't know if my ssh is rsa encrypted at all. How do I find out if it is? Or is it automatically encrypted?

---

