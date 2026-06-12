---
title: "iPad Mini"
date: 2012-12-08
forum: Hardware
---

### Post by hanzukun on 2012-12-08
I got myself an iPad Mini the other day. However, when I connect it to the usb port nothing happens, not on the computer (Ubuntu 12.04) nor on the ipad.

Have someone else experienced this?
I have libimobiledevice installed from the repository and it works with an iPhone 3gs. I've read in the manual that if the usb port can't supply enough power the device will not load, but it should be able to sync anyway. It will only charge if I turn off the computer completely, but then I cannot sync...

[FONT="Courier New"]dmesg[/FONT] shows nothing when I connect and disconnect the ipad mini.

Since dmesg says nothing I want to believe this is a hardware issue, maybe with the evil (?) lightning connector. But still I think there should be some traces that I've connected some device.

I've had no possibility to try this on a Mac or Windows computer with itunes installed yet.

Is it working for other?
Please share your thoughts and experiences!

---

### Post by e.m.fields on 2012-12-16
I've got a new ipad mini. I've had success connecting it on my Ubuntu 12.04 installation, and I get a nautilus popup of two folders: "iPad" and "Documents on iPad". 

I can download saved files etc from various applications under "Documents on iPad", though I haven't yet determined if uploading files onto the device will be recognized by the applications. 

Please post updates.

---

### Post by hanzukun on 2012-12-16
Thank you e.m.fields for that information!

After I read your post I booted up a Live cd (10.12) on my computer, connected the ipad mini and it showed up just like it does for you. Running [FONT="Courier New"]dmesg[/FONT] also shows the device name and serial number. So, yes, it is working on my hardware. Just it is not working on my installation.

However, when I booted up again to my normal environment [FONT="Courier New"]dmesg[/FONT] provided me this information when inserting the ipad (which it didn't do before): [FONT="Courier New"]usb 2-1.2: new high-speed USB device number 6 using ehci_hcd[/FONT]
However, there is no sign of the ipad in nautilus. I have no clue why it's like this, perhaps the easiest way is to reinstall Ubuntu (it's not hard but I prefer not to).

Anyway, thank you for this information, now I know it should work!
If anyone has some idea where to look to fix this without reinstalling, please tell me!

---

### Post by hanzukun on 2012-12-19
Now it works!

I just had to unlock the device before connecting it. So easy!
I haven't tried syncing music, but I can download pictures and videos I've taken with the ipad, that's great!

---

### Post by laimagendelmundo on 2013-11-02
Hello, i got a new mini ipad and i am having simmilar issues. It shows up in Nautilus but when clicking it I keep getting this message: unable to mount iPad. Unhandled Lockdown error (-4). It is unlocked when trying.

---

