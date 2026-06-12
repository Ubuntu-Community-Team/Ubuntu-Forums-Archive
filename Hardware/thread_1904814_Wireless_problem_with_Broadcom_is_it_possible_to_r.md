---
title: "Wireless problem with Broadcom is it possible to replace it ?"
date: 2012-01-05
forum: Hardware
---

### Post by bahha on 2012-01-05
Hi 

this may be a weird question to post here, but I hope I'll get some help here 

I got a Dell Vostro 3500 core i3   

it came with the most crappy wireless card BCM4313  its drivers are sloppy. 

I may regret buying a Dell, because I always buy HP machines. 

after hours/ days of reading and searching I found that their driver do not support data capture in aircrack-ng suit .  
I'm wondering if it's possible to replace it with my HP laptop  wifi card. it's an intel 3945abg 

 will it work or there will be problem with the bios. 

I'm not asking to show me how to , just to check if it's possible or I'll get a USB 

I opened my laptop I know where the hardware are .
thank you in advance

---

### Post by Mark Phelps on 2012-01-05
You sure that the intel 3945abg is a separate wireless CARD?  

Asking because all the references I've seen to it mention that it's integrated with Intel chipsets on motherboards.  This would most likely be the case with a laptop, where the boards are custom built to prevent the use of extra cards.

---

### Post by bahha on 2012-01-05
I couldn't wait for an answer as I don't know when I'll get one 

so I opened both laptops and grabbed the wireless cards 

on Dell Vostro 3500 there are two slots for the card  I tried the intel card on the one I removed the BCM4313 .  entered the bios setting it wasn't recognized I l booted into W7 install the driver nd restarted nothing happened. i changed the slot the same thing 

I booted to ubuntu 10.11 and backtrack 5   the lshw -c network detects only the Lan device 

i don't know if the bios is locked not to accept other cards or the card is not compatible 

although the BCM4313 works on windows and  connects to infrastructure access point on ubuntu  and it's a 802.11/n  .  It's still nothing to me  as long as it doesn't support capturing data . 

if there are any tips please help

I'm now in a place where I can't get a usb wifi . 

I'm doing security test using my htc device and hp laptop and I want to use the dell as the attacker because it's faster and has great specs  except the BCM4313

---

### Post by bahha on 2012-01-05
hi thanks for replying apparently you posted it while I was writing mine 

any way sure they are not integrated because I removed them from the slots and got them in my hands

they have two  wires on them one is black and the other is white . and two indicators not to put the wires on the wrong antenna

---

