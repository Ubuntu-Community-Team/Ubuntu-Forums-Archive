---
title: "USB harddrives disconnect after transfering a few MB"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by Aleksandersen on 2007-02-07
Hi,

I have this odd little problem when I transfer data to any USB storage unit.

:| After a couple of MB have been transferred, all my USB devices (including mice) disconnects; the file transfer is of course interrupted and fails. The only way I can get them to work again is to shut down the coputer and reboot.

---

### Post by ^rooker on 2007-02-07
Please give some details about the hardware involved.
(USB-controller chipset / mainboard / USB-storage device)

I've had a case once where the IRQ-sharing didn't work correctly (on a Shuttle PC) - and it turned out to be an IRQ-sharing problem, due to APIC (had to disable it in BIOS)


--- but what you should definitely do is check the logs.
Anything useful in "dmesg" output?

---

### Post by Aleksandersen on 2007-02-07
Cowon iAudio 6 - 4 GB, LaCie Something-Something - 300 GB, and a Kingston USB stick - 1 GB.

They are all connected trough a Belkin USB hub.

Except for the mice (some wireless Microsoft thing I got with a magazine) which uses the second USB input on the back on my computer. The other input is used by the hub.

---

### Post by ^rooker on 2007-02-08
Try avoiding the hub for trouble-shooting. In my office a faulty hub once caused trouble like you're describing.

That's 3 devices you mentioned, right?
Try attaching only one at a time and see if the problem persists.

---

### Post by Aleksandersen on 2007-02-08
I have tried and most often use only one device at a time.

Though it is hard not to use the hub. The computer is under the table and only have USB ports on the back. I would literally have to disassemble the table to get back there to switch USB cables.

Could it not bee due to drivers or something software related? Or do you think it is the HUB hardware wise?

---

### Post by ^rooker on 2007-02-09
Unfortunately, I'm not equipped with "super cow" powers ;)

So... since you haven't posted ANY output from any logs it's almost impossible for someone to say anything about your problem.
In order to limit the possible causes for this behaviour, I'd really suggest to narrow down the involved hardware. 

If you're saying that the error persists with ALL of the 3 devices behaving the same, although you're using one at a time - I guess it's not caused by one of your USB storage devices.

So what's left? 
Basically, everything else... So *please* take a look at some logs which might tell you about hardware problems:

dmesg
cat /var/log/messages
...

Believe me: It's worth disconnecting the hub and trying - because then you can check that one off your checklist.

---

### Post by Aleksandersen on 2007-02-09
I do not know which part you wanted or what it means:

:popcorn: [http://code.x0f.org/169](http://code.x0f.org/169)

Right at the end every USB device (the mouse which is not connected trough the HUB and the iAudio that where connected trough the HUB) stopped responding.

---

