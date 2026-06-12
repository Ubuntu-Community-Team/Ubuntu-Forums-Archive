---
title: "Pavilion DV6 disable ATI card"
date: 2012-01-31
forum: Hardware
---

### Post by doktoreas on 2012-01-31
Hello everybody,
My laptop (unfortunatly for me) has got 2 video cards, INTEL and ATI. I wanna use only the Intel but I have not figured out the better way because, also after BIOS update, there is not an option to choose the video card.
It's ok to add to the blacklist-local.conf those lines:
```

blacklist fglrx
blacklist radeon

```

Thanks!
Luca

---

### Post by Mark Phelps on 2012-01-31
The link below says how to switch between GPUs:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

