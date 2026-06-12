---
title: "Connecting to bluetooth supported phone"
date: 2009-11-08
forum: Hardware
---

### Post by kerryhall on 2009-11-08
I am trying to connect my Razr V3 to my computer via bluetooth. I feel like I am so close!! Here is what I have done so far. I can scan for my phone with hcitool. hcitool finds my phone, and give me the phone's mac address. So far so good. 

I downloaded and installed moto4lin. However, moto4lin needs me to specify the phone's device filename. (/dev/xxx) ACM protocol/device/??. How do I make an ACM device from my phone's bluetooth mac address?

Why am I doing this? I want to be able to do things like make phone calls with my computer mic and speakers, or play sounds out into my phone calls, or record calls, or send text messages from my computer. 

Thanks!!

---

### Post by kerryhall on 2009-11-08
I have done some more digging, and found gnome-phone-manager. 

This attempts to connect to my phone, my phone prompts me for a pin, and I enter the default (/etc/bluetooth/hcid.conf) of "1234"

phone rejects this pin as invalid. I think I need a passkey agent. How do I set one up?

---

