---
title: "bluetooth dongle not working, connection time out"
date: 2012-12-26
forum: Hardware
---

### Post by ejbrant_ibo on 2012-12-26
I've searched all around the internet and haven't found a solution for this. I rarely post here, because I usually find the answer to my problem, but I'm really at wit's end. 

I'm using a bluetooth dongle that's coming up as:

Bus 004 Device 002: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device

Bluetooth manager isn't recognizing the adapter. 

sudo hciconfig hci0 up  says:

Can't init device hci0: Connection timed out (110)

Have reinstalled all bluetooth packages, removed dongle, rebooted, installed bluez, searched high and low, and there seems to be no answer short of a bug in the kernel. Any ideas?

---

### Post by ejbrant_ibo on 2012-12-27
Any help out there? I've had this same dongle work in earlier versions of Ubuntu and it works fine in Windows XP, but I can't stand windows!

---

