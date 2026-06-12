---
title: "No sound after BIOS update"
date: 2008-08-12
forum: Hardware
---

### Post by wildteen88 on 2008-08-12
Last week I decided to update my motherboard's BIOS to the latest version available which was 1232. The motherboard is an ASUS P5B Deluxe.

Before updating my BIOS sound worked flawlessly.

This is the error I get when I go to Sound Preferences using Autodetect setting:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
```

Sound does not work with the LiveCD either, however it did before.

NOTE: I did have this issue before when 8.0.4 was released, so I downgraded to 7.10. When I heard 8.0.4.1 had been released I gave the LiveCD a try to see if the sound worked, which it did. So I upgraded again (clean install).

How can I setup the sound again.

---

