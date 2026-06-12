---
title: "Canon Network Scanner Blocked by Firewall"
date: 2019-06-18
forum: Hardware
---

### Post by electroconvulsive on 2019-06-18
Hi;
I have recently bought a Canon TR 4560 network multi-function centre. It is for the most part working however the network scanning has been a bit problematic. Firstly I installed the canon Scangear application from their website. Initially I could not get it to recognise the scanner over the network until I disabled the firewall on my system. With the firewall disabled it works just fine however I do not think I want to disable the firewall each time I scan a document. I'm not really into workarounds and would prefer a proper solution. I have tried to get it working with SANE the same way I got my old Epson to work over the network by editing the dll.conf to point t the canon.conf file and then using the ip address in that file.I also tried to point the dll.conf directly to the net.conf where I put my IP address which I had set up on my router's DHCP server to the MAC address of the printer but to no avail. I am pretty sure there is no SANE support for the printer. When I look at the properties page of the printer in the printers panel the address comes up as a dnssd address so i guess that is the reason I cannot get it to be recognised by SANE. Basically what i need to find out is what is the port number that the scangearmp2 application is using to connect to the scanner so I can add the rule in the firewall configuration. BTW I am using GUFW to configure my firewall. Any help on this one is appreciated.

---

### Post by brian_p on 2019-06-18
> **electroconvulsive said:**
> Hi;
I have recently bought a Canon TR 4560 network multi-function centre. It is for the most part working however the network scanning has been a bit problematic. Firstly I installed the canon Scangear application from their website. Initially I could not get it to recognise the scanner over the network until I disabled the firewall on my system. With the firewall disabled it works just fine however I do not think I want to disable the firewall each time I scan a document. I'm not really into workarounds and would prefer a proper solution.

Scanning works without ufw. With a firewall, it doesn't work. Your firewall rules are haywire. This isn't a scanner problem. Look to your iptables rules. Only you know what they are.

> I have tried to get it working with SANE the same way I got my old Epson to work over the network by editing the dll.conf to point t the canon.conf file and then using the ip address in that file.I also tried to point the dll.conf directly to the net.conf where I put my IP address which I had set up on my router's DHCP server to the MAC address of the printer but to no avail.

Scangear knows nothing about SANE. Sane knows nothing about Scangear. Thinking other than this way leads nowhere.

> I am pretty sure there is no SANE support for the printer.

Definitely.

> When I look at the properties page of the printer in the printers panel the address comes up as a dnssd address so i guess that is the reason I cannot get it to be recognised by SANE.

Nonsense. You are contradiicting yourself.

> Basically what i need to find out is what is the port number that the scangearmp2 application is using to connect to the scanner so I can add the rule in the firewall configuration. BTW I am using GUFW to configure my firewall. Any help on this one is appreciated.

Exactly. What does canon have to say about it? It is their device after all.

---

### Post by electroconvulsive on 2019-06-19
Hi Brian;
Thanks for your response. I have a few things to note.
> Scanning works without ufw. With a firewall, it doesn't work. Your firewall rules are haywire. This isn't a scanner problem. Look to your iptables rules. Only you know what they are.
I have also tried it on a fresh install with no iptables rules set via GUFW. Also to clarify this the Scangear application cannot detect the scanner on the network at launch. That is what the actual problem is here.
> Scangear knows nothing about SANE. Sane knows nothing about Scangear. Thinking other than this way leads nowhere.
Thanks. Duly noted. I was hoping that there would have been a generic scan driver that worked with SANE like my old scanner which was an Epson. No such luck!
> I am pretty sure there is no SANE support for the printer.
Definitely.
I meant the scanner component as it s a multifunction centre I am dealing with here.
> Nonsense. You are contradicting yourself.
I don't understand how I am contradicting myself. I was pointing out the fact that the printer/scanner uses a DNSSD (bonjour?) address when it sets up. If it used an IP address to identify itself on the network couldn't I could open up all communication to the device's IP address in the firewall?
> Exactly. What does canon have to say about it? It is their device after all.
So i asked their support people which port or ports to open in the firewall to enable communication between the scanner and the PC and here is their response.
> Thank you for contacting Canon Australia.

The Canon BJNP port for scanning (Applicable models only) is TCP/UDP 8612.

Please note that we do not support drivers and software for the Linux operating system. The drivers and software are provided "as is" with no warranty or support. For further assistance, please contact Linux.

 I especially like the last line of the response. I will be sure to contact "Linux" LOL. 
But anyway I tried 8612 and the result was the same. The Scangear application does not see the scanner on the network when the firewall is up and that port is open.
Next I have to answer the question as to why I am using a firewall in the first place. I am running a WordPress website on this PC for development of my own website. That is the reason I am running the firewall in the first place. Considering this do I need it? If I have a firewall running on my router shouldn't that be enough to protect the open ports in the WordPress (Apache) installation? from outside my network?

---

### Post by brian_p on 2019-06-19
> Next I have to answer the question as to why I am using a firewall in the first place. I am running a WordPress website on this PC for development of my own website. That is the reason I am running the firewall in the first place. Considering this do I need it? If I have a firewall running on my router shouldn't that be enough to protect the open ports in the WordPress (Apache) installation? from outside my network?

I am uncomfortable giving advice on security matters. However, I have been running mail, web and ssh services behind a router for many years with no problem. I'd see this as your easiest and quickest solution.

As to why Scangear cannot detect the scanner on the network - I do not know. You could try a little investigation, though. The command

```
nmap <IP_address_of_device>
```

(without < and >) should  the show services offered by the TR4560. It would also be of interest to see the outputs of

```
avahi-browse -rt _uscan._tcp
avahi-browse -rt _ipp._tcp
```

The commands can be tested with and without a firewall.

---

### Post by electroconvulsive on 2019-06-20
I managed to solve it by adding a rule to allow all all UDP ports from the Canon printer/scanner's IP address to be opened through the firewall (UFW). Admittedly I tried this through the GUI (GUFW) and it refused to add the rule and that is where I got stuck. So I finally added the rule in Terminal using this command ```
sudo ufw allow proto udp from <IP_address_of_device>
``` So thanks brian_p for helping me out as much as you did. It was much appreciated. I should have been able to solve this on my own so thanks again for your patience with a guy who should have known better. Cheers!

---

