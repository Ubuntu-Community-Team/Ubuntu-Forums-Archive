---
title: "Networking probems on an acer aspire 1690"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by aladair333 on 2006-02-02
Hey guys, 
I have a "Broadcom NetXtreme Gigabit Ethernet" adapter. and running dapper ubuntu. When I boot up into ubuntu my card seems to be detected and running fine (i think its under the module name tg3). 

When ever i try to get an IP address from the DHCP server in my uni it wont find one at all, but I can boot into windows and it will find it fine no problems at all.. No one else seems to be having the problem. 

so i have come to a few ideas:
1) The DHCP server magically decides to stop working every time i start up ubuntu and then magically start working when i am in windows.

2) The tg3 driver is the wrong driver for my card.
    - Althought other distros like simply mepis use the tg3 diver and they run without any trouble what so ever i can use the network and run things fine.

3) dhclient is broken 

4) Linux hates me

I have no inet in ubuntu just through windows.

Sorry if this question has been asked before if it has can anyone direct me to the solution. I had a quick search but i think it was about the wireless card which i aint too bothered about at the moment 

cheers

Alasdair

---

### Post by Teroedni on 2006-02-02
hmm i have no clue as to what wireless device you have

Could you do a lshw
and lspci

and paste all the wireless info you get out of them?

---

### Post by aladair333 on 2006-02-02
[QUOTE=Teroedni]hmm i have no clue as to what wireless device you have

Could you do a lshw
and lspci

and paste all the wireless info you get out of them?[/QUOTE]
hi,
its not a wireless card its the wired card I am trying to get working. I aint too bothered about the wireless cause i dont have a wireless network anywhere around thats useable. 

The solution i found was for the Intel Wireless card but not the broadcom wired card. 

Sorry for the confusion. 

Alasdair


p.s. And i have just relised i have put this in the wrong forum! sorry again! it should probably go in the dapper section. dunce i am

---

### Post by j0rd on 2006-02-08
Same laptop, same network card, same problem.  Looking for answers...i'll let you know.

---

### Post by j0rd on 2006-02-09
Alright, I found out why our network cards are not working, but i've yet to find a fix.

There seems to be an IRQ conflict on my laptop. There are too many things sharing IRQ 10, kernel seems to get a conflict and shuts off ICQ 10 all together. NIC runs on IRQ 10, so it's loaded and all but doesn't work. After you boot check the dmesg for the error.  It's something like "Problem with IRQ: 10. Nobody cared"

I'm going to try a couple things and try to get this fixed.  I had the exact same problem on my Dual 750mhz machine a while back with a 2.6 kernel.  I remembering upgrading the kernel fixed it, but i think the kernel on ubuntu is newer than the one i upgraded to, so i doubt it's going to help.  Also the bios for the aspire doesn't allow us to change the IRQ's which is quite anoying.  

Let me know if you find a fix for this problem.  Thanks.

---

### Post by j0rd on 2006-02-09
[QUOTE=j0rd]Alright, I found out why our network cards are not working, but i've yet to find a fix.

There seems to be an IRQ conflict on my laptop. There are too many things sharing IRQ 10, kernel seems to get a conflict and shuts off ICQ 10 all together. NIC runs on IRQ 10, so it's loaded and all but doesn't work. After you boot check the dmesg for the error.  It's something like "Problem with IRQ: 10. Nobody cared"

I'm going to try a couple things and try to get this fixed.  I had the exact same problem on my Dual 750mhz machine a while back with a 2.6 kernel.  I remembering upgrading the kernel fixed it, but i think the kernel on ubuntu is newer than the one i upgraded to, so i doubt it's going to help.  Also the bios for the aspire doesn't allow us to change the IRQ's which is quite anoying.  

Let me know if you find a fix for this problem.  Thanks.[/QUOTE]

Edit /boot/grub/menu.lst and add 
`noapic irqpoll` to the boot options, i'm pretty sure all you need is irqpoll, but i added both at the same time, so i'm not positive.  It seems to cause a bunch of other problem in the dmesg though, so i'm hoping i can figure something out.

---

### Post by Tribe on 2006-02-16
Hi there,

A friend of mine got the same prob, but now with the 'noapic irqpoll' stuff we got sound + ethernet. BTW the wireless card ain't working but at least we got something.

Bb

---

