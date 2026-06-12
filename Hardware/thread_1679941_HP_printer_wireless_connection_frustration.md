---
title: "HP printer wireless connection frustration"
date: 2011-02-01
forum: Hardware
---

### Post by aeronutt on 2011-02-01
I'm getting really frustrated with my Ubuntu to HP officejet j6400  wireless printer. At random times (every few weeks), the darn thing just stops working. And I'll spend an hour or more reloading s/w, or re-discovering the printer, or some other perverted debug effort. I don't change any settings between mis-haps, but certainly allow s/w upgrades as recommended by the update manager.

Ok, enough ranting. Maybe.

Everything was working fine 2 days ago, and now same problem as always. I booted my laptop, turn on the printer, (order doesn't matter) and when I try to print something it goes to the queue and just sits there. Then, I fire up the HP device manager and click on status and get "Device communication error 5012". Sometimes, rerunning hp-setup and manually entering the IP address works, but not this time. Device discovery just reports 'no devices found'.

I really really need to print something. This IS enough to push me back to Windows after years of Ubuntu.

Any ideas on how to debug and fix this permanently?

---

### Post by him610 on 2011-02-01
> manually entering the IP address works

Can you permanently set the IP address in your printer? If it gets set dynamically (DHCP) by the wireless router, it is liable to have a randomly assigned IP address each time you turn it on. Without a consistently assigned IP address for your printer your computer will have problems linking up with the printer.

You might consider leaving your printer always powered on which should maintain the same IP address on it.

Cordless phones and microwave ovens have been suspected to have caused wireless problems also.

Good luck.

---

### Post by aeronutt on 2011-02-02
Thanks, I have set the IP address manually in the printer.

---

