---
title: "SOLUTION FOUND: slow Bluetooth xfers"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by chasmza on 2005-09-01
Good news for bluetooth users:

I have seen many unspecific complaints on a number of Windoze and Linux forums of dismal Bluetooth file transfer performance, particularly from PC to mobile device.

My Cambridge Silicon Radio USB dongle (ID 0a12:0001) with kernel 2.6.10-5-386 transmitted files to a Sony Ericsson k700i at an estimated rate of about 20-50 kbps.  Yes folks, thats **bits** per second - 10 minutes for a 2MB file!.

First you will need your remote device's 48 bit hardware address, which you can get by activating bluetooth on both your pc and phone and running:

```
hcitool scan
```

The fix is to run this command once your file transfer has started (don't worry, unless the file is smaller than 100k you'll have plenty of time to start it  :)  ).

```
sudo hcitool sr 00:00:00:00:00:00 slave
```
[INDENT]Change 00:00:00:00:00:00 to your phone's hardware address[/INDENT]

I find it sometimes fails, but succeeds the second or third attempt.  If your dongle has an activity LED, you may notice it becomes brighter as the transfer rate increases to about 100-300kbps. 

I guess either my hardware or the bluetooth stack is not good at being master.  Either that or my phone is not good at being slave, but it does explain why transfers initiated from my phone were always quicker.


I hope somebody out there finds this useful.  It's not often I discover a solution like this. I usually find answers on great forums like this one, so I'm only too happy to return the favour.

---

### Post by fragman44 on 2008-07-14
THANKS! i went from 10 minute 1mb transfers to my moto q 9m, and now it takes less than a minute. great job

---

