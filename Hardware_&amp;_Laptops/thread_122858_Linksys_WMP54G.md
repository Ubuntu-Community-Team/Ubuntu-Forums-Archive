---
title: "Linksys WMP54G"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by Arc Owner on 2006-01-28
I am trying to get the Linksys WMP54G wireless pci card working on my ubuntu computer. It uses the Rt2500 chipset. I did a 'iwconfig' and it detected it under the rao connection interface. When I tryed to configure rao in the network settings my computer froze up on me every time. Can someone help me get this to work?

---

### Post by Jainor on 2006-01-28
IF anyone can help Arc. i would like it to. i got the same wireless nic and need to get it to work. would GREATLY appreciate any help.

---

### Post by Arc Owner on 2006-01-28
with my pci card, I think that ubuntu is detecting it, but whenever I go to administration+network settings and to the properties menu of rao interface, my computer just freezes. I have done this many times and it always freezes. I have even used the live cd to see what would happen then, but it still froze.

---

### Post by boomerian on 2006-02-01
No one seems ready to take this adapter on...
I've an older version (2) with a Broadcomm chipset, and although Lambert tried to help for a while, I stopped getting any suggestions or direction.
In general, there's a lot of frustration in this "hardware help" forum, much of it due to wireless issues.
I've basically given up, have signed up for the Linuxant ($20) solution, but that's no picnic, either. (Many issues with kernel versions, etc.) I'd rather get ndiswrapper to work, since its the "free" part of all this that attracted me in the first place - that and trying to learn something on an old box.
I welcome/**challenge** any gurus/baristas/whatevers who read this to help us, who are eager to run Ubuntu but are disappointed in the (lack of) wireless capability.
Regretfully,

---

### Post by jcl on 2006-02-03
I am no expert on this by any stretch, but I found a post on here that made my life much easer with my WMP54G. Here is the gist of it:

Hardwire you computer up to your access point.

System -> Administration -> Synaptic package manager.

Settings -> Repositories -> Add -> Add a checkmark to 'Community maintained (universe)' then click 'Ok' twice then 'yes' and let it add the new repository.

Search for 'ndis' and install 'ndisgtk' and 'ndiswrapper-utils'.

After the install is complete you should have an icon for System -> Administration -> Windows wireless drivers.

Click 'Install new driver', put your WMP54G driver CD in the drive and direct the installer to your rt2500.inf file under /cdrom/drivers/WMP54Gv4 (or something similar) and let it install. You should then have an entry for 'rt2500/hardware present: yes'

Select it and click 'configure network' and enter your SSID and other settings and you should be good to go.

Note: I'm using WEP and tried to enter my passkey in ASCII and that didn't work. I had to log into the router and get the Hex version and type that in. Then I danced a jig \\:D/

---

### Post by Arc Owner on 2006-02-03
I figured it was more trouble than it was worth, so I took it back and bought one that I know is compatible, the NetGear WG311T:cool:

---

### Post by jcl on 2006-02-05
That always works too :mrgreen:

---

