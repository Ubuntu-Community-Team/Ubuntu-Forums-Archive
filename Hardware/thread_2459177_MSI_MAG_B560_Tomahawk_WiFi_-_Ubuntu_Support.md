---
title: "MSI MAG B560 Tomahawk WiFi - Ubuntu Support"
date: 2021-03-12
forum: Hardware
---

### Post by Zlobomir on 2021-03-12
Hello,

I did my best to search the forums and I did not find a similar topic.
Today I received my new motherboard. Under Windows 10 everything is fine, no ? or ! marks in the Device Manager.
Unfortunately, under Ubuntu 20.04 my both network adapters, Bluetooth and front USB ports do not work. I tried also live Ubuntu 20.10 and Linux Mint, no difference.
Please advise. Thanks in advance for your time and efforts.

Best regards,

Zlo

---

### Post by CelticWarrior on 2021-03-12
Assuming you're talking about [this motherboard]("https://www.msi.com/Motherboard/MAG-B560-TOMAHAWK-WIFI/Specification") then we have:

1. The Ethernet NIC is a Realtek 8125B 2.5GB LAN. Support for this new NICs is still a work in progress. Try this: [https://askubuntu.com/questions/1259947/cant-get-rtl8125b-working-on-20-04](https://askubuntu.com/questions/1259947/cant-get-rtl8125b-working-on-20-04)

2. The WiFi NIc is Intel WiFi 6E AX210. Also new therefore support still a work in progress but seems to work fine with kernel 5.11. I'll leave a possible solution in the meantime for the experts.

---

### Post by Zlobomir on 2021-03-12
Thank you very much, I already have a wired internet. Just downloaded the driver and ran the script.

---

### Post by Zlobomir on 2021-04-26
Hello,

Time for some feedback. After updating Ubuntu to 21.04 indeed both the ethernet and Wi-Fi NICs work. However it looks like the Bluetooth is still not recognized.

Best regards,

Zlo

---

### Post by Yellow Pasque on 2021-04-26
Make sure it's not blocked with rfkill:
[https://www.reddit.com/r/linuxquestions/comments/lpz4vc/does_anyone_have_working_bluetooth_on_intel_ax210/gv9xubw?utm_source=share&utm_medium=web2x&context=3](https://www.reddit.com/r/linuxquestions/comments/lpz4vc/does_anyone_have_working_bluetooth_on_intel_ax210/gv9xubw?utm_source=share&utm_medium=web2x&context=3)

---

### Post by Zlobomir on 2021-04-26
Yes thank you, it was blocked. Followed the steps and bluetooth now works!

---

### Post by Yellow Pasque on 2021-04-26
Nice. Please mark the thread SOLVED (Thread Tools menu above first post.)

---

