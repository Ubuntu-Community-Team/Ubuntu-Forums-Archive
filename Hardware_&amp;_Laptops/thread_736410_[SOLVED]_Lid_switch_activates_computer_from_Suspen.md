---
title: "[SOLVED] Lid switch activates computer from Suspend"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by rdoolen on 2008-03-26
I have never been able to get my laptops lid switch to do what I want. I want to lid to make the LCD go blank, but nothing else. I have set the power manager to &#8220;Do Nothing.&#8221; When I close the lid, it does what I want, nothing except turn off the screen. The problem comes when I have already set the computer to Suspend, Then if I close or open the lid, it activates the computer. This happens on Hardy as well as Gutsy. Its even worse now in Hardy because I get the same behavior from Hibernate, toggling the lid activates the computer. In Gutsy this didn't happen. 

So, is there a way to have my computer not activate if the lid is toggled?

My laptop is a Fujitsu P5010, running 7.10 or 8.04 beta.

---

### Post by rdoolen on 2008-04-12
bump

---

### Post by rdoolen on 2008-06-07
I fixed this. I basically disabled the lid switch. The only thing that the lid does is turn off the back light when closed. I used the following command:

sudo acpitool -w

From that there is a list of acpi events(?). They are numbered. The lid switch was on the list as number 3. Then

sudo acpitool -w3 

toggles the enable/disable.

I'd like to thank everyone for all there help :wink: :lolflag:

---

