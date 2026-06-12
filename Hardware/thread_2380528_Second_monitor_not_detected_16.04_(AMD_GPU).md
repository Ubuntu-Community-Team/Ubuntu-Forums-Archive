---
title: "Second monitor not detected 16.04 (AMD GPU)"
date: 2017-12-18
forum: Hardware
---

### Post by brmbrmcar on 2017-12-18
Hello,

I've been trying to get a second monitor to work on Ubuntu with AMDGPU drivers. Without the drivers, it goes into a weird mirror where both screens are detected as one. With the AMDGPU drivers, Ubuntu doesn't detect the monitor and xrandr says it is disconnected.

---

### Post by Autodave on 2017-12-18
How are both monitors connected: what type of cables?

---

### Post by brmbrmcar on 2017-12-18
My main (working) one is DVI, my secondary one that isn't detected is HDMI.

---

### Post by brmbrmcar on 2017-12-20
I randomly got it to work for a few minutes just on one boot, but then it stopped being detected again.

---

### Post by QIII on 2017-12-20
Hello!

Do you have a spare HDMI cable to rule out that possible hardware fault?

My GPU supportS 4 monitors (2x DVI, HDMI, DP) and I have used it so from time to time.  I think that indicates that the driver supports multiple outputs.

If you are using xrandr to manipulate your settings, you may also be introducing a conflict with the driver.

---

### Post by brmbrmcar on 2017-12-20
It can't be HDMI because it boots no problem with two screens until it is time to login. Unfortunately I only have one HDMI cable anyway.

I have used xrandr, but it just says that HDMI is disconnected just as the standard Ubuntu monitor settings say.

---

### Post by brmbrmcar on 2017-12-21
Never mind it was the cable. No idea how. I'd set this to solved if I knew how to, sorry.

---

### Post by QIII on 2017-12-21
Under "Thread tools" click "Mark this thread as solved".

Cheers!

---

### Post by brmbrmcar on 2017-12-22
Thanks!

---

