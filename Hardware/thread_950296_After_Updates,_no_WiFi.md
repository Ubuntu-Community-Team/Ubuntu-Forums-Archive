---
title: "After Updates, no WiFi ?"
date: 2008-10-17
forum: Hardware
---

### Post by boosted on 2008-10-17
I did all the updates, I believe some were kernel updates.  After reboot I have no WiFi.  I was using madwifi and under Hardware drivers there is nothing listed now?  How do I get the wifi back?

---

### Post by iponeverything on 2008-10-17
Let get some log output!

in the terminal type:

```
sudo tail -f /var/log/messages

```

unplug and replug the card and post what you see in the log.

---

### Post by boosted on 2008-10-17
```

pccard: card ejected from slot 0
pccard: CardBus card inserted into slot 0

```

---

### Post by neorab on 2008-10-17
I'm in the same boat as you with my wife's laptop.  If I find the solution for this new kernel I will post it.  In the mean time, using the old kernel continues to work :)

---

### Post by iponeverything on 2008-10-17
> **boosted said:**
> ```

pccard: card ejected from slot 0
pccard: CardBus card inserted into slot 0

```

I have to admit that -- does not help much. Ok. What's the card? Just post the line from the lspci output. We can tackle it from another angle.

.

---

### Post by boosted on 2008-10-17
the card is a D-Link DWA-652 Xtreme N 

lspci :
Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)

---

### Post by iponeverything on 2008-10-17
do a:


```
lsmod |grep ath9k
```

If it does not give you any output do:

```
modprobe ath9k
```

see if anything shows up in /var/log/debug /var/log/syslog /var/log/messages

you can also just boot into the previous kernel.

---

### Post by boosted on 2008-10-17
```

lsmod |grep ath9k
generated no output

```

```

modprobe ath9k
WARNING: /etc/modprobe.d/blacklist-framebuffer line 26: ignoring bad line starting with 'vesafb'
FATAL: Module ath9k not found.

```

I have yet to check the log files you mentioned.

---

### Post by bull205 on 2008-10-17
Not sure what version you are running, but this happened to me too.  I updated last night and my wifi went down. I think it is fixed already, but I am at work and haven't been able to update again.    Check this thread out....

[http://ubuntuforums.org/showthread.php?t=948665]("http://ubuntuforums.org/showthread.php?t=948665")

---

### Post by Nxion on 2008-10-17
I had the same issue with my laptop. After I would update the kernel I would have to reload my drivers. I wrote this guide for my laptop. But I know that works with other version of the card(ARXXXX)
[URL="http://ubuntuforums.org/showthread.php?t=942195"]
http://ubuntuforums.org/showthread.php?t=942195[/URL]

Hope this helps.

---

### Post by boosted on 2008-10-17
I had madwifi installed and working before the update.  So do I need to use your guide and do it all over again?

I tried going to that link and downloading the deb file.  I got the larger one  	  linux-firmware_1.1_all.deb  (3.2 MiB)
Installed and restarted.  No WiFi and the driver isn't listed under Hardware Drivers either.

---

### Post by Nxion on 2008-10-17
> **boosted said:**
> I had madwifi installed and working before the update.  So do I need to use your guide and do it all over again?

I tried going to that link and downloading the deb file.  I got the larger one        linux-firmware_1.1_all.deb  (3.2 MiB)
Installed and restarted.  No WiFi and the driver isn't listed under Hardware Drivers either.


Do you have a madwifi-ng folder? If so, you can probably start from number 8 on my guide and you should be fine. Let me know if you have problems.

---

### Post by boosted on 2008-10-17
I don't see a madwifi-ng folder, but I do have 3 madwifi folders.

one has no files
2nd one has 13 files
3rd has 24 files

---

### Post by Nxion on 2008-10-17
> **boosted said:**
> I don't see a madwifi-ng folder, but I do have 3 madwifi folders.

one has no files
2nd one has 13 files
3rd has 24 files

Where are those folders located? Are they on the root of your hard drive?

---

### Post by boosted on 2008-10-17
they are in

/lib/modules/2.6.24-19-generic/madwifi (no files)
/lib/modules/2.6.24-21-generic/madwifi (13 files)
/usr/src/madwifi (11 Folders 13 Files)

---

### Post by boosted on 2008-10-18
Nxion ?

Anyone.....?

---

### Post by boosted on 2008-10-19
I still have no wifi...  would really like to figure this out and get it going again.  Please, some help me out here.

---

### Post by sidneymccoy on 2008-10-20
I too lost wireless after the updates, and tried a few online suggestions, but the one the worked for me was:  [http://blog.linuxoss.com/2008/05/ubuntu-804-enabling-atheros-ar5007-based-wireless](http://blog.linuxoss.com/2008/05/ubuntu-804-enabling-atheros-ar5007-based-wireless) (or [http://tinyurl.com/442bmn](http://tinyurl.com/442bmn) )

---

### Post by Nxion on 2008-10-20
> **boosted said:**
> Nxion ?

Anyone.....?


Sorry boosted, I had been out of town an no access to the interwebs :)

Going back to what we were doing. I think you should start over. Follow the guide from the beginning. We need to get the new drivers loaded on your system.
[URL="http://ubuntuforums.org/showthread.php?t=942195"]
http://ubuntuforums.org/showthread.php?t=942195[/URL]

Let me know if you have issues.

---

### Post by nixforme on 2008-10-27
That guide is awesome it helped me so much. I was looking all over for a guide and was disappointed. I am so happy I finally got my wireless working. Thanks again!

---

