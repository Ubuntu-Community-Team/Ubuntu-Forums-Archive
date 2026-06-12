---
title: "Installing an external drive on USB"
date: 2009-09-10
forum: Hardware
---

### Post by haughtonomous on 2009-09-10
This is probably a numpty question, but I'm at a bit of a loss. I'm using Gutsy Gibbon (7.10 with Gnome), and I've bought a Seagate Barracuda  320Gb SATA II external drive in a USB caddy, which I've plugged into a spare port. In Hardware Manager I can see it dangling off a USB interface, but I've no idea what to do next in order to use it. I guess I have to put a filesystem on it by formatting it, and then mount it, but can anyone advise how to do the formatting? Do I have to boot from a live CD and do it that way, or can I do it from within my real OS? How do I determine the device path (eg /dev/s??) to use? I can't currently see the device from Places/Computer, even as a USB device or unmounted filesystem - should I be able to at this stage?

All help welcome - I've not installed external drives with Linux before, and my Googling has revealed lots on how to put Ubuntu onto an external device but not the reverse!

Regards,

Neil Haughton

---

### Post by jerrrys on 2009-09-10
this may help

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

more here

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=Jrm&num=50&q=mounting+external+drive+USB+ubuntu&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=Jrm&num=50&q=mounting+external+drive+USB+ubuntu&aq=f&oq=&aqi=)

---

### Post by haughtonomous on 2009-09-11
Thanks. I managed to figure it out for myself in the end - the hardest part was establishing the device path (/dev/sda1, it turns out). What confused me was that the device appeared to be listed as /dev/sdg1 in Hardware Manager, but I was looking at the wrong tab. Anyway, fdisking /dev/sda1 and building a file system on it then mounting it did the trick. Pretty straight forward, really.

One thing that puzzles me is that although Gutsy apears to do a clean shutdown, now everytime I boot up it fails with a reported fsck failure on one of the other partitions (ReiserFS, internal drive). A second reboot starts fine. This happens every time I switch on, and has only started since I added the USB external drive. Could there be some hiccup in the shutdown process which the new drive causes, that in turn causes startup to fail first time, each time?

---

