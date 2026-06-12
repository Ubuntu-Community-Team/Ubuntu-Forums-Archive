---
title: "Encryption for mounted removable devices such as USB flash drives and SD cards"
date: 2023-05-29
forum: Hardware
---

### Post by jayjayseal on 2023-05-29
Hi,

Is there a way to automatically block access and ask to encrypt removable drives like USB flash drives and SD cards before you can use them?

[/Frantic Secure everything(!) mode off] :lolflag:

---

### Post by TheFu on 2023-05-29
Not before they are used.  But you can setup any storage device with LUKS, if you like.
Two videos and 1 text location, pick what works for you:
[LIST]
[*] Creating Part1: [Https://youtu.be/vk9Z2_rEUak](Https://youtu.be/vk9Z2_rEUak) (nerds should find this very funny)
[*] Accessing Part2: [Https://youtu.be/ELEVo6SbYl0](Https://youtu.be/ELEVo6SbYl0) seems to be it.                 
[*] Text version: [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it)
[/LIST]

---

### Post by jayjayseal on 2023-05-30
Thanks, i have already setup LUKS with TPM so it auto unlocks on boot and this works

It's a shame that something is not already implemented. I noticed in the office when we plug in a USB flash drive it blocks the access and asks for encryption before use. I wanted to implement this for Ubuntu too. I have other people in my house who would possibly plug in USB drives without thinking first. :-)

I might have found a sollution to this. Using USBguard. It automatically blocks incoming USB connections. I'm trying to script something around this...

---

### Post by TheFu on 2023-05-30
Well, anything is possible, given enough time, skill, money.  You could just block any USB access to unknown devices. That's what I do.  In an office, the solution that's been around 25 yrs is to limit physical access to USB ports.  You've probably need all those off-lease computers that have doors with keys to access USB ports or floppy disks.  You can always disable USB ports in the BIOS (assuming the systems don't have crappy BIOS controls).

If you are willing to add more risks ... check out **udev**.  This is what controls USB when something is connected.  All sorts of magic is possible.  Comes down to timem skill, money for the implementation. I think it would take less than a day to figure out for specific hardware.  For example, if the company only approves 1 model of USB storage device and all others are not allowed, you could only support that 1 or 20 or 500 models ... how many depends on someone's willingness to code each USB ID.  

Plus, we have access to the source code for all these things.  You could pay someone to implement what you seek. Just be certain to get the code involved so you don't have to pay the same person next time, if you don't want. You might find someone on fivr (or some other gig-job website) to do it for $100.  Who knows?

---

