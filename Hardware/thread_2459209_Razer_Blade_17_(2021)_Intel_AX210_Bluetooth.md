---
title: "Razer Blade 17 (2021) Intel AX210 Bluetooth"
date: 2021-03-13
forum: Hardware
---

### Post by andrew-jardine on 2021-03-13
Hey Guys,

I promise that I have tried to do my due diligence on this one and have tried several different ideas -- but so far no luck. This laptop is new (obviously) and I am FINALLY returning to Linux after a couple of years stuck on a mac (*barf*). I don't mind the mac actually, but I just find my Linux machines always perform so much better. Anyway. I have installed Ubuntu 18.04 and have upgraded my kernel to 5.11. I wrestled with the WIFI adapter but was able to get past that issue by add the drivers to the /lib/firmware directory. Next up on my list though is to try to get the bluetooth cookin'.

When I run a 

```
$ dmesg | grep -i blue
```

.. then I get the following output

```

[    2.581117] Bluetooth: Core ver 2.22
[    2.581131] Bluetooth: HCI device and connection manager initialized
[    2.581134] Bluetooth: HCI socket layer initialized
[    2.581136] Bluetooth: L2CAP socket layer initialized
[    2.581138] Bluetooth: SCO socket layer initialized
[    2.587039] Bluetooth: hci0: Device revision is 0
[    2.587042] Bluetooth: hci0: Secure boot is enabled
[    2.587042] Bluetooth: hci0: OTP lock is enabled
[    2.587043] Bluetooth: hci0: API lock is enabled
[    2.587044] Bluetooth: hci0: Debug lock is disabled
[    2.587044] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    2.587045] Bluetooth: hci0: Bootloader timestamp 2019.40 buildtype 1 build 38
[    2.587142] bluetooth hci0: Direct firmware load for intel/ibt-0041-0041.sfi failed with error -2
[    2.587144] Bluetooth: hci0: Failed to load Intel firmware file (-2)
[    2.597169] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.597171] Bluetooth: BNEP filters: protocol multicast
[    2.597173] Bluetooth: BNEP socket layer initialized

```

I am pretty sure the -2 is just an indication that the drive is missing. I think I found the two files online but I have no idea where to put them, or if this is even the right way to solve this problem. Anyone have any advice they can share with me?

Thanks!

---

### Post by jeremy31 on 2021-03-13
If you found the ibt-0041-0041.sfi file, copy it to /lib/firmware/intel/  then reboot

You will likely need [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/intel/ibt-0041-0041.ddc](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/intel/ibt-0041-0041.ddc) too, placed in the same directory

---

### Post by andrew-jardine on 2021-03-13
Hey Jeremy,

OK I think I am getting closer! I did a wget on the files and place the ddc and sdi files in the /lib/firmware/intel directory and then did a reboot. Now when I go to settings the bluetooth is toggling on and off (it seems). When I run the same dmesg command, I am now getting

```

[  134.125688] Bluetooth: hci0: Bootloader timestamp 2019.40 buildtype 1 build 38
[  134.125747] Bluetooth: hci0: Found device firmware: intel/ibt-0041-0041.sfi
[  134.125751] Bluetooth: hci0: Invalid CSS Header version
[  134.125854] Bluetooth: hci0: Intel reset sent to retry FW download
[  134.720620] Bluetooth: hci0: Device revision is 0
[  134.720632] Bluetooth: hci0: Secure boot is enabled
[  134.720636] Bluetooth: hci0: OTP lock is enabled
[  134.720640] Bluetooth: hci0: API lock is enabled
[  134.720644] Bluetooth: hci0: Debug lock is disabled
[  134.720648] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[  134.720655] Bluetooth: hci0: Bootloader timestamp 2019.40 buildtype 1 build 38
[  134.720732] Bluetooth: hci0: Found device firmware: intel/ibt-0041-0041.sfi
[  134.720738] Bluetooth: hci0: Invalid CSS Header version
[  134.720800] Bluetooth: hci0: Intel reset sent to retry FW download

```

Any idea what I should try now?

---

### Post by andrew-jardine on 2021-03-14
> **jeremy31 said:**
> If you found the ibt-0041-0041.sfi file, copy it to /lib/firmware/intel/  then reboot

You will likely need [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/intel/ibt-0041-0041.ddc](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/intel/ibt-0041-0041.ddc) too, placed in the same directory

Hey Jeremy --

I think I hit the wrong button when I hit reply and it looks like I replied to myself :). Putting those files in place worked at getting hte drivers picked up -- thanks for that. I have a new issue though whereby it looks like it is toggling in a loop between on and off. I included some new dmesg output in the other post, but I think the root cause is related to the reference to an invalid CSS header --

```
[  134.720732] Bluetooth: hci0: Found device firmware: intel/ibt-0041-0041.sfi
[  134.720738] Bluetooth: hci0: Invalid CSS Header version
[  134.720800] Bluetooth: hci0: Intel reset sent to retry FW download

```

I did some digging to see if I could find anyone else reporting this issue but the best I could muster was the source code where the line is output. I am a programmer, but C has not been part of my toolkit since college so I am not sure what the error means exactly or what I might be able to change to fix it. 

Have you ever seen this error before? or do you know what the code that is referencing this problem might be referring to?

[https://github.com/torvalds/linux/blob/master/drivers/bluetooth/btintel.c#L933](https://github.com/torvalds/linux/blob/master/drivers/bluetooth/btintel.c#L933)

Thanks.

---

