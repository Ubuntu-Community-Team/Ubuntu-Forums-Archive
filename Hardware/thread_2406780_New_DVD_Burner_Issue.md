---
title: "New DVD Burner Issue"
date: 2018-11-25
forum: Hardware
---

### Post by uzzo23 on 2018-11-25
Hello all, I just installed a new DVD burner in my linux machine and I'm now getting an error in BIOS saying that it doesn't recognize the new drive. I was hoping someone here might could help me with it. So here is the exact error I am getting.

> Drive 2 not found: Serial ATA, SATA-2 Alert! Failed to detect one or more drives during POST. Strike the F1 key to continue, F2 to run the setup utility Press F5 to run onboard diagnostics.

---

### Post by Autodave on 2018-11-26
Doesn't sound like a Linux problem at all if the BIOS isn't seeing it.  Have you gotten both cables attached securely at both ends?  Does the drive light flash at all when machine is booted? Do you hear it spinning?  Can you open the tray and put a disc in?  Does it spin when you close the tray?

---

### Post by uzzo23 on 2018-11-26
> **Autodave said:**
> Doesn't sound like a Linux problem at all if the BIOS isn't seeing it.  Have you gotten both cables attached securely at both ends?  Does the drive light flash at all when machine is booted? Do you hear it spinning?  Can you open the tray and put a disc in?  Does it spin when you close the tray?

I don't think it's a Linux problem either. I can proceed from the BIOS error after boot up. I can go to the disk management tool and eject the tray from there. So I think Linux is recognizing it. I would've just called the manufacturer tech support number. But I know one of the first questions they're going to ask me is what OS I'm running. That's when the problems are going to start. I don't think any of these hardware manufacturers train their tech support team how to deal with Linux. That's why I thought I'd start here first. So to answer your question. Yes, the tray will extend and retract and the little light comes on but that's about it. I didn't pay attention to see if the disk was spinning or not.

---

### Post by Autodave on 2018-11-26
You need to listen to see if the disk actually spins. If it does not spin, check the power connection (small connector).  If connections are good, try another power cable if there is a free one close by. If not, can you remove the disc and just hold it close to another power connector that will reach?  You will need both connectors hooked up. If still no spinning, then I believe that you have a bad drive.

---

### Post by uzzo23 on 2018-11-26
> **Autodave said:**
> You need to listen to see if the disk actually spins. If it does not spin, check the power connection (small connector).  If connections are good, try another power cable if there is a free one close by. If not, can you remove the disc and just hold it close to another power connector that will reach?  You will need both connectors hooked up. If still no spinning, then I believe that you have a bad drive.

Thanks Dave, so I just fired it up and got as close as I could get to the tower to listen. It sounds as if it's spinning, I ejected it manually and then pushed it back in. I'm pretty sure it's spinning, I also saw the little green light flickering like it was reading the disc.

---

### Post by Autodave on 2018-11-26
Light flashing and drive spinning, but BIOS doesn't see it: sounds like a bad drive.  I am assuming that this is a SATA drive: have you tried connecting it to another port on the motherboard?  You do not have to connect it to the next numerical one.

---

### Post by uzzo23 on 2018-11-26
> **Autodave said:**
> Light flashing and drive spinning, but BIOS doesn't see it: sounds like a bad drive.  I am assuming that this is a SATA drive: have you tried connecting it to another port on the motherboard?

Yes sir, you would be correct, it is a SATA drive. I haven't tried connecting it to another port but the burner it is replacing was working. It just got to where it wouldn't eject anymore. You would have to hit the button 20 times to get it to eject.

---

### Post by uzzo23 on 2018-11-26
I have reached out to the manufacturer with an online request. Hopefully they'll be able to diagnose it when they get back to me. It's a shame because it's getting hard to find different brands these days. I was a Lite-On guy for years but the last 4 or 5 I've owned has given the same trouble with ejection issues. This one that I just bought and installed is a Piodata. Never heard of them but thought I'd give it a shot. I guess problems with these things aren't limited to one brand.

---

### Post by Autodave on 2018-11-27
They all can and will have problems eventually.  They just keep getting cheaper and cheaper in price......and also quality.

---

### Post by uzzo23 on 2018-12-16
Well, I finally got my replacement drive yesterday from Newegg and installed it this morning. I got the same exact error. So at this point I'm thinking that it's highly unlikely I got 2 defective drives in a row. So I started doing a little research and found this video. Same error, different drive. I didn't get the little pop up notices as he shows in the video but it worked. No errors at bootup now. I just thought I'd come back and update so hopefully it'll help someone else out in the future.

[https://www.youtube.com/watch?v=cOGauarOLFM](https://www.youtube.com/watch?v=cOGauarOLFM)

---

