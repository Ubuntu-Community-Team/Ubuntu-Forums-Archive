---
title: "Wireless on Acer Ferrari 4000"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by jrohde on 2006-09-19
Hi,

I'm trying to get wireles to work on my Acer Ferrari 4000 using Ubuntu Desktop 6.06 (32 bit). I have followed the instruction in the Ubuntuguide.org, and I downloaded the Windows-driver from Acer's homepage.

"ndiswrapper -l" says: bcmwl5   driver present, hardware present

but iwconfig says "SET failed on device wlan0 ; no such device".

When I use the GUI network tool from the Gnome menu, it says my wireless card is called eth1 - why, and how can I change it to wlan0?

Thanks,

Jakob

---

### Post by gtkourounis on 2006-09-20
Well, broadcom wifi card and linux dont usually mix by default but you can get them to work eventually. I got my Broadcom 4318 to work after months of trying. But I dont think you are going to need that much time. anyhow, could you please show the output that this command gives you (on the terminal)


```
lspci | grep Broadcom\ Corporation
```

that should show what card you have specific card you have.

---

### Post by jrohde on 2006-09-20
Hi gtkourounis

This is the output: 

0000:05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
0000:06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Jakob

---

### Post by gtkourounis on 2006-09-20
hey, you have the same card as i do. Its a tough one to install but i hope that we will get it to work. 

```
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

the other card that shows up from that command is your ethernet card (i am assuming)

My first question is does the card appear in your network window. If it does then thats a good sign, if not... we will have to add it there. To check that go to System > Administration > Network (NOT network tools!!!). That should open up a window showing all the hardware that could be used to connect to the internet. Your Broadcom Wifi should be the fist choice. If the wireless card icon doesnt show up there then your wifi card is not properly recognized by your comp. Anyways please tell me if the Wifi card icon shows up there and then i will tell you what the next step should be.


Sorry for the long explanation, I would have given you a simple code that would have told me what i need to know but i am in school right now and i cant remember the code.

-george

---

### Post by jrohde on 2006-09-20
Hi,

Thanks for your time, mate:-)

The first network connection on the list is the wireless connection, but it is assigned to eth1 and not wlan0. Does it matter what it is called?

Jakob

---

### Post by gtkourounis on 2006-09-20
nope its good enough that you have it on your list there. Have you tried activating it? To do that you should configure its properties and then activate it. And then, after you have activated it you should use Wifi Radar to connect to the port that you wish. (at least thats how mine worked. and mine shows as eth1 too so dont worry about that). Anyhow, the only concern that i have now is do you have a secured Wifi port. I couldnt quite get my card to work while i had a pass so i took the pass off and then it worked. Or maybe i forgot to reboot after i inputed all the passes.... but i am not going to risk trying it again.

Ok so now, what you have to do....
Go to Networking again (they way i showed you on my last post) and:
1.Configure the card
2.Activate the card
NOTE: these processes are going to take a LOT of time, dont get discouraged though, wait till they end and then close them. Dont force quit them(unless you are waiting for more then 5 minutes....)

After you have done that go to Application > Add/Remove... (the last option) and then search for Wifi Radar under Internet. You should be able to find it really easily. (Watch out not to get the one that has the K infront... that one is for Kubuntu, even though it would still work just fine, but i wouldnt be able to help you with it). When you find it check it off and then click on the apply button at the bottom of the window. that should get you through an install process (dont worry its automated). After, when it has installed succesfully then go to Applications > Internet > Wifi Radar (it should be there). The computer may ask for your admin pass, and then Wifi Radar should open up. Wait a little bit for the radar to ditect all of the wireless ports that it can connect to. Find your port and select it. Then click on the edit button (right of the window) and fill in all the appropriate info. After you are done, click on "Save" and try to connect to that port. It probably wont work. I **[COLOR="Red"]HAD[/COLOR]** so i guess you must reboot also. After the reboot open wifi radar and try to connect to your wifi port. It should work. It worked for me :).

I hope to have solved your problem. If any more problems arise please tell me. I will try to help you or redirect you to people with more knowledge then mine (i am a ubuntu noob too. tried it for a week last year and then just came back again last week because i heard that they fixed the problem with broadcoms. Ubuntu breezy badger 5.10 didnt work with broadcoms 4318. i didnt know anyone with that same card that got his wifi working....) Anyways, i hope to have solved your problem. If you still have problems please tell me. I will be more then happy to help you.

Enjoy ubuntu
-george

PS: Sorry for the HUGE post....

---

### Post by jrohde on 2006-09-20
Hi again,

Sorry, this doesn't work.

Have you installed and configured ndiswarapper and the Windows driver as it is discribed on ubuntuguide.org before doing the stuff you wrote?

I can activate the wireless network in the window, but WiFi Radar shows nothing, and when I reenter the Network window, the connection has gone back to inactive state.

Jakob

---

### Post by gtkourounis on 2006-09-20
i see you are online... could you please go to the ubuntu irc chanel?
i will be in there with the name gtk, if i dont see you there i will type up the message or actually do you have msn?

---

### Post by gtkourounis on 2006-09-20
ok you went offline i will have to type up the message.

First of all did you reboot? if not then try that. and if you did reboot then try out this post by The Raven, maybe it will help you. It helped me partly. That did half of the job for me, the other half i had to do alone. And by the way Wifi-radar takes a while to find ports so give it some time (if you didnt). And here is the post by The Raven:

[http://ubuntuforums.org/showpost.php?p=1189681&postcount=105](http://ubuntuforums.org/showpost.php?p=1189681&postcount=105)

or you could try this other thread for BMCL's 4318 (which didnt help me much because i couldnt understand what i had to do):

[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

---

### Post by gtkourounis on 2006-09-20
btw please tell me what happens, if it works tell me that it works or if not then inform me and i will try to help you again.

---

### Post by jrohde on 2006-09-21
Hi again,

I'm sorry - I give up! I have tried everything, but nothing works.

I'll give Gentoo a chance, and then I will probably go back to Windows.

Thanks for trying!

Jakob

---

### Post by gtkourounis on 2006-09-21
well eventually you are going to get it to work. You should keep trying, and i will help you as much as i can.

---

