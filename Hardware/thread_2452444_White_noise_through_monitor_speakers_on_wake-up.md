---
title: "White noise through monitor speakers on wake-up"
date: 2020-10-22
forum: Hardware
---

### Post by lefty74 on 2020-10-22
When Ubuntu resumes from sleep, I sometimes hear white noise from my monitor speakers. Sometimes this is accompanied by screen flicker. I can clear both by switching to a different TTY and back (CTRL+ALT+F1 then F2), which suggests it is a driver / software issue, not a hardware breakdown. Can anyone help diagnose and fix this?

Ubuntu 20.04
Graphics card: Nvidia TITAN RTX/PCIe/SSE2
Nvidia driver version: 440.100
CUDA version: 10.2.
Connected by DisplayPort to BenQ BL2420PO monitor.

---

### Post by lefty74 on 2020-10-22
The audio device appears in settings as:
HDMI / DisplayPort - TU102 High Definition Audio Controller

---

### Post by CelticWarrior on 2020-10-22
Welcome.

You may try a newer Nvidia driver if it supports your card.

---

