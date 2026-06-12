---
title: "how do i obtain imei broadband modem number"
date: 2009-02-24
forum: Hardware
---

### Post by zander1013 on 2009-02-24
hi,

i am trying to connect an ibm t60 thinkpad to att wireless broadband using an onboard gsm modem using ubuntu 8.10. i need to give att an "id" number for the modem. i tried looking at the modem under the keyboard and there were a bunch of numbers i tried to copy them all down. some were written so tiny that i will need a jewelers loop to read them.

can i obtain the required number through the command line with ifconfig or some other command?
 
someone on atts' forum proposed the required identifier is called an "IMEI" number that is 15 digits with no letters. he can see the number through a windows program for his sierra wireless 3g modem with a "Watcher" program.

i am assuming that i setup the connection through the NetworkManager Applet -> Edit Connections -> Mobile Broadband tab.

please advise.
):P
zander

---

### Post by zander1013 on 2009-02-25
okay, i have added GNOME PPP because most of the mobile broadband cards seem to use this to manage the connection.

kppp was recommended but when i tried to install it via synaptic it gave an error that not all files could be downloaded and the installed aborted.

so i got GNOME PPP instead. when i press the button to "search for modems" in gnome ppp it says "none found"

shouldn't gnome ppp be able to find the internal gsm modem on my t60?


-zander

---

### Post by geraldm on 2009-02-25
Have you tried looking in the logs ? /var/log/messages /var/log/syslog
sudo lshw
sudo lspci]
see their respective man pages

Gerald

---

### Post by codedmin on 2009-03-24
> **geraldm said:**
> Have you tried looking in the logs ? /var/log/messages /var/log/syslog
sudo lshw
sudo lspci]
see their respective man pages

Gerald

I try it and nothing... i have an eeepc 901go, i have the 3g modem embbedd... anyway i can find the imei?

Thanks

---

