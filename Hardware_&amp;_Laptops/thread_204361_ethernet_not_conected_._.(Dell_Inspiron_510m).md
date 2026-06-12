---
title: "ethernet not conected . .(Dell Inspiron 510m)"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by vha on 2006-06-26
Then it was time for upgrading the system form 5.04 to 6.06.
As last time I´m helping a friend of mine with the machine, else I use os-x . .
The installing of the new os just went smooth, even the network part that last time was terrible last time went automaticly. Today I had the idea of doing the final part, upgrade and so on, but there was no network, no internet conection at all. Nothing is changed in the settings, but the machine have been booted twice without network cable conected because someone borrowed the cable. Tried with static ip, manual config and all that, but gave up after 2 hours. The network is there, the cable have a signal, but the machine have decidet there is no, and claims the ethernet is disconected.

Clues ?

Have to say a reinstall sounds tempting, but that would bee a bit stupid I say :)

Thanks.

vha

---

### Post by vha on 2006-06-27
And suddenly it was working again . ..
Next time before upgrading the system I'll bring the computer  some offerings first :D
Sorry for disturbing .

vha

---

### Post by Hellkeepa on 2006-06-27
HELLo!

I sometimes have a problem with an unresponsive network as well, but that's only when both the cable and the wireless are connected to the same network.
What I do then, which is a very simple way to check if your network is working at all: Turning off everything but the interface I want to use ("sudo ifconfig eth# down"), and then running "sudo dhclient eth#" on the one left alive. "dhclient" makes sure all the routing information is correct, as well as the IP, DNS and gateway, so it clears out most config issues.

Happy codin'!

---

### Post by vha on 2006-08-07
And then it was malfunctioning again, sure its easy to fix, but the machine is in Argentina (Cordoba) and I´m in Norway.
My friend who uses the machine does not have much patience or time to spend on learning basic unbuntu, so i thought I make her a guide,  a web-page or so . . but since I use a Ibook with os-x i need some screen-shots of the network dialogue boxes and other screens.

Any place on the web to find or is there someone who could send me a few on my e-mail ?, if so send me a PM.

---

