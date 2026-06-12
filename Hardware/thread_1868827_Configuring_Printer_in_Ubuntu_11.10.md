---
title: "Configuring Printer in Ubuntu 11.10"
date: 2011-10-24
forum: Hardware
---

### Post by nogueira13 on 2011-10-24
I am trying to configure a network printer in Ubuntu 11.10. When I go in "System --> System configuration --> Printers" and there I choose "Add a New Printer", I receive a receive a notification message telling me: FirewallID is not being executed.The printers detection requires the mdns, ipp, ipp-client and samba-client services enabled in the firewall. Can you help me to solve this in a step by step way? I don't know how to configure the firewall in order to not receive this message longer. I am running Ubuntu 11.10 64bits in a Dell Inspiron 1545  Laptop. Thanks in advance.

---

### Post by giox069 on 2011-10-26
I had the same problem, and it happens because I'm not using Unity.
Try to launch system-config-printer manually: (press ALT-F2, type system-config-printer and press enter). It worked for me.

---

### Post by nogueira13 on 2011-10-26
Yes, I begin with unit (Ubuntu 2D) and it worked also for me. But now I am having another problem. I am not being able to configure a network printer. I have another laptop (Asus eeepc) as a printer server, but the Dell Laptop that is in my internal network (maskerade IP) is not finding the printer that is at IP 10.0.0.4 my Laptop is at IP 10.0.0.3. I already enabled the printer at 10.0.0.4. I don't know why it is not finding.

---

### Post by wolfen69 on 2011-10-26
Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall. Once you have those things, you need to go to network in Printing, and have it search for it.

---

### Post by sammiev on 2011-10-26
If your trying to use cups at this time then your likely out of luck if your running 11.10 as many people are having troubles at this time. There is a bug report entered at this time but it hasn't been assign to anyone yet. GL :)

---

### Post by nogueira13 on 2011-10-31
wolfen69, I would like to know how to enable (step by step, please) mdns, ipp, ipp-client and samba-client in firewall. It should be enabled in IPTABLES?. Please, if you can help me I will be very thanks.

---

### Post by Jamina1 on 2012-01-27
> **giox069 said:**
> I had the same problem, and it happens because I'm not using Unity.
Try to launch system-config-printer manually: (press ALT-F2, type system-config-printer and press enter). It worked for me.

Thank you. This finally got the printer interface I was used to!

---

