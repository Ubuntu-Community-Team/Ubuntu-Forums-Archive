---
title: "Zyxel NSA221: Default IP, setup"
date: 2012-02-12
forum: Hardware
---

### Post by drubdrub on 2012-02-12
Do you have experience with the Zyxel NSA221? 
What is the default IP?

Background
[LIST]
[*]The little jewel arrives with a Windoze setup CD.
[*]The default IP is not listed in the manual.
[/LIST]

How great is that? Do I really have to set up a Windoze VM and run the silly CD? I'd like to connect to the web config interface and get it running without the silly CD.

Any hints, suggestions?

Many thanks!!

---

### Post by drubdrub on 2012-02-12
OK. Pretty simple. It grabbed a DHCP-assigned address.

My steps, for those who follow ...
[LIST=1]
[*]Log into the router and examine the list of DHCP-assigned IP numbers. In my case, this is on a Netgear N600 (WNDR3800).
[*]Plug the NSA221 into the LAN.
[*]Again, examine the DHCP-assigned IP numbers.
[*]Note the IP number that is new on the list.
[*]Point the browser to that IP number.
[*]The Sys Admin user interface was presented. Here, you can pull levers and twist dials. Set the IP to your desired value.
[/LIST]

Would love to ear of other techniques that could be used to discover the device. No doubt there are other solutions.

BTW, after about 5 min of use, I am impressed with the user interface.  :D  Looks quite thorough and easy to use. This is my first Zyxel product, so no basis for comparison. The HDs arrive, tomorrow, so I may update this opinion after attempting to configure RAID 1.

Best of luck!

---

