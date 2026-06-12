---
title: "Verizon PCMCIA card works; Sprint doesn't"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by gulagarchipelago on 2007-07-17
I tested out a Verizon aircard with my Dell Latitude D520 running Ubuntu 7.04.  That one seems to work perfectly without any extra configuration.  However, when I plug in my Sprint Merlin S620 card, the system immediately freezes and I have to do a hard reboot.  Can anyone tell me if I need to do something special for my system to recognize the Sprint card?  Or at the very least, a way to see if any kind of error is being recorded before the system freezes.

---

### Post by jml on 2007-07-17
You might want to post this question on the networking and wireless sub-forum, or ask a forum moderator to move it for you.  You may get more responses to your question.

There can be several reasons one card works out of the box and another one does not.  I assume you have tested the card that does not work in Ubuntu on another computer (running Windows for example,) to make sure that the card is functional.  Assuming that the card is OK, the most common reason for one card to work and another not to is the wireless chipset that your cards are based on.  Several chipsets have good support in Linux, (Atheros, Prism2,) and several are notorious for having very poor support, (Broadcom being the most common example here.)        

So, a bit more information would be helpful, (again, you may get both faster, and more numerous responses from the other sub-forum I mentioned.)  What is the chipset used by your Sprint Card?  What type of wireless network are you trying to connect to?  Open, WEP encrypted, WPA eicryption, WPA2?  Does your system actually see the card even if it does not connect?  It would also be helpful to post the output from the commands ifconfig and iwconfig here as well.  Hang in there, getting wireless networking in Linux can be very difficult and tedious to accomplish.  But with a bit of luck, you will succeed.

Joe

---

