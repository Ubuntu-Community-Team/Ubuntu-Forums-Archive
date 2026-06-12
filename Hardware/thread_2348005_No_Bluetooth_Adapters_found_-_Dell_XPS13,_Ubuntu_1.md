---
title: "No Bluetooth Adapters found - Dell XPS13, Ubuntu 16.04 LTS (I'm a noob)"
date: 2016-12-30
forum: Hardware
---

### Post by crysikrend on 2016-12-30
Hey there,

So after successfully installing wine on my computer I realised that my bluetooth icon has disappeared from the corner of my screen. On further inspection, no bluetooth adapters are found. When I so ```
service bluetooth status
``` it says it's active and running, nothing suspicious. Not really sure where to start or how it was truly caused, but things like this upset me as I don't know what I've done wrong :( 

Let me know what I can do to help everyone diagnose the problem - I'm still learning how to use the terminal so please dumb it down! :) 

Thanks!
Ashe

---

### Post by #&amp;thj^% on 2016-12-30
What dose this retrun from the terminal:
```
apt policy blueman
```

---

### Post by dan-palmer-bancel on 2017-02-02
> [COLOR=#000000]Hey there,[/COLOR]

[COLOR=#000000]So after successfully installing wine on my computer I realised that my bluetooth icon has disappeared from the corner of my screen. On further inspection, no bluetooth adapters are found. When I so[/COLOR][COLOR=#000000]Code:
service bluetooth status[/COLOR]
[COLOR=#000000]it says it's active and running, nothing suspicious. Not really sure where to start or how it was truly caused, but things like this upset me as I don't know what I've done wrong [/COLOR]:sad:

[COLOR=#000000]Let me know what I can do to help everyone diagnose the problem - I'm still learning how to use the terminal so please dumb it down! [/COLOR]:smile:

[COLOR=#000000]Thanks![/COLOR]
[COLOR=#000000]Ashe[/COLOR]

Hi Ashe

I have the same machine as you, with 16.04 factory installed as the Developer Edition. Today for no apparent reason my bluetooth device simply disappeared - didn't show up in system settings, and neither ```
hcitool dev
``` or ```
rfkill list
``` showed any bluetooth devices either. Very odd as just yesterday evening I was streaming Spotify to my amplifier from this machine.

Athough I have wine installed on my machine as well, I've had it for a while and think your correlation does not equal causation.

After some fiddling, verifying the necessary firmware and kernel modules were present and loaded etc;

```
ll /lib/firmware/ath10k/QCA6174/hw3.0/  total 1.4M
-rw-r--r-- 1 root root 266K May 12  2016 board-2.bin
-rw-r--r-- 1 root root 330K Oct  7 14:15 board-2.bin.wifi-qca6174
-rw-r--r-- 1 root root 8.0K May 12  2016 board.bin
-rw-r--r-- 1 root root 8.0K Apr 25  2016 board.bin.wifi-qca6174
-rw-r--r-- 1 root root 717K Apr 25  2016 firmware-4.bin
-rw-r--r-- 1 root root  78K Apr 25  2016 notice_ath10k_firmware-4.txt

```

```
lsmod | grep -i blue
bluetooth             520192  45 bnep,btbcm,btqca,btrtl,btusb,hci_uart,rfcomm,btintel
```

and rebooting with no success I remembered there's an airplane mode built into this (and many other newer laptops). I rebooted and hit F2 to go into the UEFI menus, went into the *Wireless *menu and unchecked the Bluetooth boxes for both the soft (airplane mode) switch to manage the wireless devices and the device itself to be enabled. Saved and rebooted and as expected still no bluetooth. I then rebooted again, re-enabled both those settings in the UEFI menus, rebooted and voilà! Bluetooth present and working as if nothing had happened.

I think it's highly unlikely that the airplane mode switch was pressed accidentally seeing as it requires holding down ```
Fn + PrtScr
``` together which are on opposite sides of the keyboard. When trying to diagnose the problem I did try using the airplane mode switch and it did turn the wifi off and back on, but not the bluetooth (evidently as no physical adapter was seen by the OS).

In other words, I don't think it's anything you did, and more likely a bug in the firmware, which, being an LTS release is a bit older than it might be. Hopefully an updated firmware will be backported to the LTS repos before too long.

I hope this solves your issue too.

---

### Post by bartvde2 on 2017-07-04
Thank you, disabling Bluetooth in the BIOS, rebooting, enabling it in the BIOS again worked for me as well. Dell XPS 13 Developer Edition

---

### Post by j_ham3 on 2017-12-11
I have had the exact same problem twice. And your solution fixes it. I hope they fix it properly!

---

### Post by vaishakhr on 2018-02-21
Perhaps you found a solution already, but for the benefit of others, I faced the same problem. Bluetooth was working fine for many days and all of a sudden it stopped working. 

Following the advice that was given by someone here - unchecking the box that goes something like 'Switch to Manage' under Wireless settings in UEFI settings (Reboot and long press F2 to enter) did the job for me as well. I also unchecked Wireless in the same menu. This is all that needs to be done. (Two unchecks in the UEFI).

---

### Post by ilanle on 2018-04-11
That worked perfect for me !

---

### Post by hknust on 2018-08-11
It is sad that this issue has not been resolved by Dell after 2 years. Upgraded to 18.04 earlier today and Bluetooth stopped working. I just found this thread after spending 3 hours tinkering with kernel modules/firmware versions -- even upgraded the Bios.

Followed the EFI Bios disable/enable trick and voila: it is working again. Nuts

---

### Post by uncielser456 on 2018-08-11
That's a really helpful tip. It worked on my too! THanks.

---

