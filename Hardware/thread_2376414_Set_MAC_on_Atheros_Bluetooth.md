---
title: "Set MAC on Atheros Bluetooth"
date: 2017-11-02
forum: Hardware
---

### Post by SuDuMa on 2017-11-02
I seem to be hitting a wall and could use a second set of eyes on this, or a reason to stop wasting my time and just buy a cheap CSR adapter.

I have a dell inspiron 15 3000 series with a built in bluetooth device connected via USB. The dell model is reported as inspiron 3541.

The bluetooth device identifies as 0cf3:0036 which according to the link below would be using the AR3012 chipset.
[http://forum.osxlatitude.com/index.php?/topic/2925-bluetooth-firmware-uploader/](http://forum.osxlatitude.com/index.php?/topic/2925-bluetooth-firmware-uploader/)

Datasheets:
[https://wikidevi.com/files/Atheros/specsheets/AR3012.pdf](https://wikidevi.com/files/Atheros/specsheets/AR3012.pdf)
[https://wikidevi.com/files/Atheros/specsheets/AR3011.pdf](https://wikidevi.com/files/Atheros/specsheets/AR3011.pdf)

According to the manual below the AR3011 chipset is inline programmable where the one I have seems to only be externally programmable so im guessing the firmware would be a lot harder to get a hold of and want to confirm that this is a dead end before giving up because the way I look at it there has to be a way to streamline the manufacturing process by writing the mac in software by the OEM even if it is in permanent eeprom.

I can hardcode the MAC using my EEPROM reader at least on the AR3011 model but that still doesn't let me do it in software.

[https://fccid.io/PPDT77H056/User-Manual/Manual-1152573.iframe](https://fccid.io/PPDT77H056/User-Manual/Manual-1152573.iframe)

If I can get ahold of the software or the driver referenced in the above link I can at least help out others set the MAC with the AR3011 chipset and it may give me an idea of the hcitool commands to try.

Any help or nudge in the right direction to be able to control the MAC address through software would be greatly appreciated i have some ideas to throw out as well to see if they sound feasible.

Would it be possible to brute-force the hcitool cmd sequences and would there be any repercussions like broken hardware?

Has anyone tried this yet or wrote any tools to do so that im missing and i would imagine I would need an external reader hooked to the EEPROM and constantly read in order to detect what the command was?

Has anyone heard of enabling the master blaster setting on these things before?

---

