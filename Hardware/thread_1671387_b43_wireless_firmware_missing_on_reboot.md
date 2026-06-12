---
title: "b43 wireless firmware missing on reboot"
date: 2011-01-19
forum: Hardware
---

### Post by gwaar on 2011-01-19
So I finally managed to set up my wireless card (Broadcom b4306/2), after having some headaches getting the firmware set up correctly. However, now every time I reboot, networkManager gives me the same error message as it did before I set up the wireless: "device not ready (firmware missing)". I can run b43-fwcutter again, dumping the firmware blobs back where I put them, and the wireless comes back, but I'd rather not do that every time I restart. Any thoughts?

[edit] adding module b43legacy to /etc/modules did the trick. Sorry, I feel like I'm spamming things I immediately find the answers to right after.

---

