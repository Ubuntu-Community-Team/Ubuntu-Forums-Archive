---
title: "Realtek RTS5260 SD Card reader stopped working"
date: 2021-12-17
forum: Hardware
---

### Post by csete on 2021-12-17
I have a Dell XPS 15 9500 with a Realtek RTS5260 SD Card reader.  The reader has been working fine until very recently.  Looking at lspi, I see:

```

6c:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5260 PCI Express Card Reader (rev 01)

```

I'm running latest Ubuntu 21.10:

```

Linux XPS-15-9500 5.13.0-22-generic #22-Ubuntu SMP Fri Nov 5 13:21:36 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```

Is there anything I can do here or do I need to wait for new firmware or kernel to fix this?

Thanks!
Craig

---

### Post by csete on 2021-12-18
For reasons I don't understand, the card reader has started working again.  The class still shows unassigned, but the card reader functions.

---

