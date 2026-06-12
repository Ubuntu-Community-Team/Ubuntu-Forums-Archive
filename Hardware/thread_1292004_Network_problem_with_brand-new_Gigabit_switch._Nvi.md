---
title: "Network problem with brand-new Gigabit switch. Nvidia Nforce ethernet."
date: 2009-10-15
forum: Hardware
---

### Post by Nokao on 2009-10-15
Hi ...

I have a really slow network (slower than 10/100) with a brand new gigabit switch.

I'm using the Nvidia Nforce network of this motherboard:
[http://www.ciao.it/ASUS_M2NPV_MX__656544#productdetail](http://www.ciao.it/ASUS_M2NPV_MX__656544#productdetail)

Can you help me?

---

### Post by Giblet5 on 2009-10-15
"Slow" is a subjective term...

Netgear has cool color-coding on their switches. Does yours? Do you show the color code for 1000Mb/Full-duplex for the cable where your PC is plugged in? Try pulling the cable out, waiting a sec, and plugging it back in. Did it change? That would be a BIOS issue: upgrade your BIOS.

If not.

Install the ssh server via ```
sudo apt-get install openssh-server
```

Now, create a test file called 500MEG.DAT: ```
dd if=/dev/random of=500MEG.DAT bs=1M count=500
```

Now, time your nic's interface: ```
scp 500MEG.DAT `hostname`:500MEG-2.DAT
```

What was the final average MB/s. I get around 47MB/s (470Mbps). I'm on an intentionally low-priority switch port though.

Now, try that against another system to really test the switch itself. I'd try systems at all speeds (10/100/and 1000Mbps) to verify that the store/forward (speed switching) logic is good.

Remove the data files ```
rm -i 500MEG*.dat
```

---

### Post by Nokao on 2009-10-15
it's actually 7 mb/s ...

It was 15 when I had a 10/100 switch.

---

### Post by Giblet5 on 2009-10-15
> **Nokao said:**
> it's actually 7 mb/s ...

It was 15 when I had a 10/100 switch.

15 would be 150Mbps, so that must have been a compressed data test. A 10/100 can't do 15MB/s. The theoretical max is 10MB/s, but that is impossible in real life.

So, it thinks you're at 100Mbps.

Your motherboard does 1000Mb, so you need to figure out what speed it's running at.

What is the output of ```
sudo mii-tool eth0
```

It should be something like ```
$ sudo mii-tool eth0
eth0: negotiated 1000baseT-HD flow-control, link ok
```


What make/model is the switch?

---

### Post by Giblet5 on 2009-10-15
Note that you can force the NIC to a specific speed via ```
sudo ethtool -s eth0 speed 1000 duplex full
``` but that may leave you without network access.

I'd recommend writing down what the current settings are before forcing it...

---

### Post by Nokao on 2009-10-15
> **Giblet5 said:**
> 15 would be 150Mbps, so that must have been a compressed data test. A 10/100 can't do 15MB/s. The theoretical max is 10MB/s, but that is impossible in real life.

So, it thinks you're at 100Mbps.

Your motherboard does 1000Mb, so you need to figure out what speed it's running at.

What is the output of ```
sudo mii-tool eth0
```

It should be something like ```
$ sudo mii-tool eth0
eth0: negotiated 1000baseT-HD flow-control, link ok
```


What make/model is the switch?

# mii-tool eth0
SIOCGMIIPHY on 'eth0' failed: Operation not supported

Also note: 
# ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

[B]I repeat: a week ago with a 10/100 switch I was surely downloading files from a samba server at least at 10-12 megabytes per second.
[/B]
Now with a gigabyte switch the transfer speed is 6-7.

I think it's just a driver problem, but I can't find a solution googling around.

---

### Post by Nokao on 2009-10-16
Can someone help me?

Does ubuntu work with gigabit ethernet?

---

