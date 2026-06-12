---
title: "Cant connect Wifi WPA2 TC4200"
date: 2011-07-22
forum: Hardware
---

### Post by Honzacz on 2011-07-22
Hi, I got problem with my HP TC 4200 tablet.
I installed Ubuntu 11.04, i love it, but my Wifi doesn't work well.
Wifi card on TC 4200 can't connect to AP with WPA2 (before i had Win. XP and it worked well).

Now, i can find wifi allright, but when i try to connect to AP with WPA2, there opens window for password.
After entering it try to connect, fails and opens same window again and again. I got proper password.

When i tried if tablet is able to connect to AP with WPA 1, it did with no problem.

Anyone knows what can i do? Any idea about some testing tools? 
Thanks!!

---

### Post by Honzacz on 2011-07-22
After closer searching forum i realized, WiFi is still problem on linux, and ubuntu 11.04 is somewhat bugged. I** wonder if older and more stable version of ubuntu would be better?** Maybe 10.10??

But most of other threads here are about situation, **when wifi doesn't work at all, but on my notebook it works with WPA but not WPA II.**
Any idea?

---

### Post by Favux on 2011-07-22
Hi Honzacz,

It would help both you (to google with) and others if you posted what type of wireless chipset you have.  If you're not sure post the line that has it in the output of *lspci* in a terminal.

That said it sounds sort of like an old issue I had with my Broadcom where Network Manager wouldn't work on WPA2 with ccmp enabled.  So I had to manually edit in with gconf-editor:  [http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)

I don't know how Natty handles that level of wireless configuration currently and I know gconf-editor isn't available through the menus like it used to be.  But you can still get it by entering *gconf-editor* in a terminal, if it is installed.

---

### Post by Honzacz on 2011-07-24
Thank you!
I tried command u mentioned this is result
```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
10:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)

```

---

### Post by Favux on 2011-07-24
OK, this is your wireless chipset:
> 02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

So you have B and G but not N, it looks like.  Now you have something to search with.  There are several large wireless threads often beginning with a how to on fixing problems.  You might want to post on one of them with the diagnostics they request.  Then one of the wireless gurus could help you.

---

### Post by Honzacz on 2011-07-24
Thanks a lot.
I used gconf editor u mentioned in your thread. I can start editor, but i got different lines in wireless security and when i switched it for your it didnt helped. Also when system reopens window with ssid and password, password seeems to be OK and not hex, so it is probably different issue.

So I am going to look for some thread about wifi here, when i know type of card..

---

