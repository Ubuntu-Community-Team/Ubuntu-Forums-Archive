---
title: "apsire 1362LMi probs with sempron and wlan"
date: 2004-11-07
forum: Hardware &amp; Laptops
---

### Post by duister on 2004-11-07
Hi :p

I already installed ubuntu on my workstation and recently bought a budget laptop, the Aspire 1362LMi.

This laptop has the sempron 2800+ processor ( I think it's a K8 then, instead of k7, at least that is what i've read)

Now, CPU freq in gnome gives me very weird stats from 0 to 134,something and 1083.something. The fan runs more then under windows. someone who has a laptop with sempron and fixed this problem?

Allright, on to the next problem ;) I have a wireless lan and it's not detected in gnome by the "wireless link monitor" i also don't see any modules that are load. The line in lspi -v about this device is:

[COLOR=Red]0000:00:0b.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
        Subsystem: Acer Incorporated [ALI]: Unknown device 006e
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at 20000000 (32-bit, non-prefetchable)
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00004400-000044ff
        I/O window 1: 00004800-000048ff
        16-bit legacy interface ports at 0001
[/COLOR]

Now, i know this card has the Chipset: INPROCOMM IPN 2220 Wireless LAN Adapter. I also know a driver excists for this card. Driver for use with ndiswrapper it says..(so that's actually a windows driver) Is there a more native linux solution?

Thanks a lot for any response :p

edit: misspelled name of the laptop:corrected

---

### Post by duister on 2004-11-08
Now...  wlan is working perfect with the ndiswrapper. Frequency scaling of the cpu is a whole different cookie.

i tried it with the powernow-k8 modules, and it works, but somehow it starts working after and hour when i tunred on my laptop... pretty weird huh ;)

dmesg gives me this:
powernow-k8: vid trans failed, vid 0x3, curr 0x4
powernow-k8: transition frequency failed

but after an hour it works. probably acpi implementation of this laptop sucks. 

Now what works is almost everything but for the powermanagement. The modem works, the geforce5200fx works, wireles lan works, everything is fast, but powermanagement is pretty important for a laptop. so i think i'll quit this test, and go back to windows for the laptop.

I'll still use linux for my workstation, but linux, myself, or my laptop is not ready to run a different OS then windows ;)

I already payed for the windows tax anyway , hehe, cheers people.

---

### Post by duister on 2004-11-20
[QUOTE=duister]Now...  wlan is working perfect with the ndiswrapper. Frequency scaling of the cpu is a whole different cookie.

i tried it with the powernow-k8 modules, and it works, but somehow it starts working after and hour when i tunred on my laptop... pretty weird huh ;)

dmesg gives me this:
powernow-k8: vid trans failed, vid 0x3, curr 0x4
powernow-k8: transition frequency failed

but after an hour it works. probably acpi implementation of this laptop sucks. 

Now what works is almost everything but for the powermanagement. The modem works, the geforce5200fx works, wireles lan works, everything is fast, but powermanagement is pretty important for a laptop. so i think i'll quit this test, and go back to windows for the laptop.

I'll still use linux for my workstation, but linux, myself, or my laptop is not ready to run a different OS then windows ;)

I already payed for the windows tax anyway , hehe, cheers people.[/QUOTE]


Found the solution: 

applied with the follwoing patch::

diff -r -u old/powernow-k8.c new/powernow-k8.c
--- old/powernow-k8.c 2004-11-15 21:02:20.988038920 -0600
+++ new/powernow-k8.c 2004-11-15 21:37:06.077057208 -0600
@@ -279,7 +279,7 @@
return 1;
}

- while (rvosteps > 0) {
+ while ( (rvosteps > 0) && ( (data->rvo + data->currvid) > reqvid ) ) {
if (data->currvid == 0) {
rvosteps = 0;
} else {

Micha³

---

### Post by doublejoon on 2005-02-18
Okay I have the same laptop. Could you explain your solution   (dummy terms)

---

