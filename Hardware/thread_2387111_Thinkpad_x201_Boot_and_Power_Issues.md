---
title: "Thinkpad x201 Boot and Power Issues"
date: 2018-03-14
forum: Hardware
---

### Post by Lachlan_M on 2018-03-14
I recently bought a used Thinkpad x201 on eBay and installed Kubuntu 17.10. Pretty much everything works out-of-the-box, but there are two problems.


First, it seems to turn off abruptly at times. I'm thinking this could be an overheating issue, and it *does* seem to happen mostly when I use Firefox, which also causes high CPU temperatures (65°C+, versus no more than 50-55° for Chrome). I may try putting on new heatsink paste if the problem persists.


The real problem is that the screen generally refuses to turn on. I press the power button to turn on the computer, and it begins whirring, but the screen stays black. The computer stays on as long as I let it, and eventually I just have to hold down the power button to turn off the computer and try again.


It's possible that the computer is booting properly and it's just the screen that isn't working. But I kind of don't think so, because I've tried typing my password and pressing enter. If the computer booted successfully, that should log me in and load the desktop environment, at which point the Wi-Fi and bluetooth indicators should light up, but they don't.


About one time out of ten, maybe less, the screen turns on and the computer boots properly. When this happens, the screen works perfectly—no dimness or flickering or anything—so it seems like the LCD itself is fine. But I still feel like this may be a hardware issue, because when the screen *doesn't* work, it shows nothing, not even the initial Lenovo boot screen.


So...does anyone have any suggestions?

---

### Post by kurt18947 on 2018-03-17
If you don't get the Lenovo boot screen I'd suspect a defective machine. The vendor can't blame Ubuntu, it hasn't loaded yet. Can you return it? My desktop machine often needs a tap or two of the space bar for the screen to come alive once booted into Ubuntu. I have an X201 upgraded with an SSD and it works very well.

---

### Post by Lachlan_M on 2018-03-17
I had come to the same conclusion after asking some other people. Someone suggested that I give the computer time to boot, then try the caps lock and num lock keys to see if their indicators lit up. Since they didn't, it's safe to say the computer *isn't* booting, so I'm assuming there's an issue with the motherboard.


I contacted the seller on eBay and they said they'd accept the return if I wanted, but said it sounded like it might be a fan issue and pointed out that they *did* say in the listing that the fan was making a funny noise. Which, to be fair, they did, so I said I'd try replacing the fan and then contact them again.


I doubt it will solve the problem, because the fan *does* start running when the computer is turned on regardless of whether it boots, as well as when the computer boots and gets hot, and further testing has indicated that the random shutdowns occur regardless of CPU temperature. But we'll see.


Fortunately the vendor is unlikely to blame Ubuntu---they sold the machine with Mint on it, so I'm sure they're not one of those OH-MY-GOD-WHAT-IS-THIS-NON-WINDOWS-THING-YOU-BROKED-IT people.


Regardless, thank you for your help. :)

---

