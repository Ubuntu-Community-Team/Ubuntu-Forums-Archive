---
title: "Is this a safe way to turn off my external LUKS USB drive?"
date: 2016-06-17
forum: Hardware
---

### Post by rocky-oceans on 2016-06-17
Ubuntu (same behavior on 15.04 and 16.04) recognizes and automounts my external hard drive. It asks me for the encryption password and everything works well. But when I right-click on the icon on the launcher and go to safely remove, it says it safely removed it but when I unplug the USB cable the drive is still on. Further, if I reconnect, it does not work. I get the following in my syslog:

```
Jun 17 00:38:05 rocky kernel: [13385.505970] usb 2-3: new high-speed USB device number 8 using xhci_hcd
Jun 17 00:38:10 rocky kernel: [13390.617919] usb 2-3: device descriptor read/64, error -110
Jun 17 00:38:25 rocky kernel: [13405.833667] usb 2-3: device descriptor read/64, error -110
Jun 17 00:38:26 rocky kernel: [13406.049734] usb 2-3: new high-speed USB device number 9 using xhci_hcd
Jun 17 00:38:31 rocky kernel: [13411.161707] usb 2-3: device descriptor read/64, error -110
Jun 17 00:38:46 rocky kernel: [13426.377484] usb 2-3: device descriptor read/64, error -110
Jun 17 00:38:46 rocky kernel: [13426.593449] usb 2-3: new high-speed USB device number 10 using xhci_hcd
Jun 17 00:38:51 rocky kernel: [13431.605382] xhci_hcd 0000:00:14.0: Command completion event does not match command
Jun 17 00:38:51 rocky kernel: [13431.605385] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command

```

The error corresponds to a power issue. The only way to fix it is to unplug the power adapter for the external drive. Then plug it back in, then reconnect the USB cable. But that seems bad.

Note that the drive this is about is the 8TB Western Digital My Book.

So after much searching the following seems to work well:

```
sync &&
sudo umount /dev/mapper/luks-b1d88818-d169-4a7b-a1b0-c97f764377f9 &&
sudo cryptsetup luksClose luks-b1d88818-d169-4a7b-a1b0-c97f764377f9 &&
sudo hdparm -Y /dev/sdb &&
echo 1 | sudo tee /sys/block/sdb/device/delete

```

If I remove my USB by doing those commands, then no system log errors and when I plug the usb back in, it works just like the first time.

But I don't really understand those commands. I kind of just cobbled them together and experimented. Do those commands seem reasonable? Is that the right order? Are any of the commands unnecessary?

Once those commands complete, can I unplug the power supply to my external hard drive immediately or should I wait a few seconds?

---

### Post by xen3 on 2016-06-17
The first command flushes all buffers to (all) disks, which means that any outstanding writes, will be saved to disk. The second unmounts the file share (volume, partition, filesystem) mounted from an opened LUKS container. The 3rd closes the LUKS container itself (you can replace luksClose with just "close") and the 4th puts the drive to sleep. The last command apparently forcibly deletes the drive from the system (it being recognized; this last command is probably unnecessary as it would happen automatically).

Particularly what seems to be important for your drive is the sleep command? Those commands are perfect and there is no need to wait after they complete.

Those commands depend on your USB drive being recognized as the "second" drive in the system (sdb) they will fail if some other drive is connected first (like some flash card).

If you wanted that to work regardless, you would need to replace the sdb with the UUID, if that even works, but perhaps the [FONT=monospace][COLOR=#000000]/dev/disk/by-id/ [/COLOR][/FONT]method would work better. If you look in that directory, you will probably see the name of your drive, and the file (link) with that name is a good and reliable reference to the drive.

But there is nothing you need to improve on that command persé. I assume that the default "safely remove" will already execute umount and cryptsetup close, so the only additional thing you are really doing, is hdparm -Y. Which is the sleep command. That is probably the only thing you are adding here.

Regards.
[FONT=monospace][COLOR=#000000]

[/COLOR]
[/FONT]

---

### Post by rocky-oceans on 2016-06-18
Thank you very much for this reply, xen3. It is very helpful!

I would indeed like to not depend on the device being sdb. I will follow your advice using the device ID. I do not know how to get rid of the hardcoding of sdb in the last command though. The effect of the last command is that the icon disappears from the unity launcher. I like this because it tells me that Ubuntu is aware the the device has been removed.
Also, do I need the first sync command or umount also does a sync? Removing the manual sync might be better because you said that sync does sync for all devices. What do you think?

Finally, any idea why Ubuntu does not do the sleep command itself?

Thanks again for your help.

---

