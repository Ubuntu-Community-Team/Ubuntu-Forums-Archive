---
title: "SMBUS - the root of all my problems?"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by nalmeth on 2006-01-29
In case you have not heard from me about this, I will summarize whats up and wrong.

I have a Sony Vaio PCG-FX215 laptop, that sort of works and sort of doesn't. I installed breezy on it, to find that wireless did not work, and my 2 batteries can't hold a charge for very long...
The batteries, I assumed, must just be shot. 
Regarding the wireless, the card I have is a D-Link DWL-G650, which has support in the kernel. I first tried ndiswrapper with a windows driver, and found out that the card is actually not detected when in the slot. So I then tried the card in another laptop, with XP, and it operates just fine. I did ALOT of probing in the terminal, and quite simply, the connection between the card or its slot and Ubuntu is just not there. Period.  

So there are only a few possibilities as to what is wrong here.

-The wireless slot/bus/etc is physically damaged. This is unlikely, because it apparently worked before (on windows) and it has been sitting in a closet for a long time, not being moved

-The firmware for the wireless port is too old to interact with Ubuntu. I tried to contact sony, and after giving up a lot of personal information just for a technical inquiry, the message failed to be sent. I get the feeling Sony doesn't want to make it easy to get support. :( 

The third possibility only arose recently. For whatever reason, after an update with dapper, I failed to get an internet connection, and thus could not aquire updates to fix this new problem. 
So I downloaded the Kubuntu Flight 3 Live CD and the Ubuntu Flight 3 Install CD.

When I booted the Kubuntu LiveCD, a new error message appeared that I had never seen before. Here is the sequence:

```
Failed to mount /selinux/ No such file or directory

initializeing modules...
starting kernel event manager...
detecting and activiating hardware...
[I]vt596_smbus SMBUS error 
upgrade BIOS or use force=1[/I]
```

I looked into this and could only find this information about smbus:
[http://en.wikipedia.org/wiki/SMBus](http://en.wikipedia.org/wiki/SMBus)

Unfortunatley it doesn't look like smbus is directly related to wireless, so this may be a false alarm, but there may be a chance that the wireless issue its deeply rooted to this. SMBUS is aparently more related to battery usage though, and maybe fixing this problem could make my batteries operate properly. 

I don't know how to "upgrade BIOS or use force=1". I have a feeling I would need to get a new BIOS directly from sony, and I assume that force=1 would be entered with some varation of smbus to force its activation during boot.. Or something along those lines.

Can anybody fill me in on any info about what's going on here? I can't seem to find any relevant information anywhere, or anyone with a similar problem. Getting frustrated with this POS laptop, but would be very happy to see it fully functional.

Thank you for any thoughts 

nalmeth

---

