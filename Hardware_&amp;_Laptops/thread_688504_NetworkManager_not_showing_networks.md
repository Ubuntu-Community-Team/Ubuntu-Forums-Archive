---
title: "NetworkManager not showing networks"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by bapa on 2008-02-05
Hi there,

I have my nm-applet running and appearing in my panel, but it's not helping much. Left-clicking on it just shows a button that sends me to the network administration software (network-admin). My understading was that it would let me see a list of available networks, wired or wireless, from which I could pick... 

Everything works, in that I can connect to whatever network I pick via network-admin, but it would just be very handy to have access to the networks from the panel.

Any clues?

Thx

PS I am running 7.04 on an Acer Travelmate 3002

---

### Post by KyleAnderson on 2008-02-05
Hmmm....
Just to check, a lot of laptops have a swtich that turns on the wireless, but it sounds like it is already on if you say that you can connect via network-admin.

can you figure out what the name of your wireless interface is? Its probably "eth1" or maybe "ath0" something like that. Running "iwconfig" will make it obvious what it is called.

After you figure that out, when you run "iwconfig [whatever it is] scan", does it spit out a list of access points? (Cause that is the same thing that nm-applet would be running)

Another thing to ask, when you right click on the applet, do you see two check boxes, one for wired and one for wireless? If so are they checked?

---

### Post by rje_nc on 2008-02-06
Also be sure that your wireless adapter is not entered into the /etc/network/interfaces file.  Typically, when using network manager to manage connections, the /etc/network/interfaces file should only have an entry to the loopback connection (lo).  Network Manger cannot manage the adapter if it is being configured directly.

Bob

---

