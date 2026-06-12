---
title: "Hardware discovery"
date: 2011-07-29
forum: Hardware
---

### Post by williepabon on 2011-07-29
is there a command in Linux to initiate hardware discovery?. I have a video capture card on my system (Bt878) that was discovered once, but now it doesn't show on the device manager. Thanks for the help.

---

### Post by lmarmisa on 2011-07-29
> **williepabon said:**
> is there a command in Linux to initiate hardware discovery?. I have a video capture card on my system (Bt878) that was discovered once, but now it doesn't show on the device manager. Thanks for the help.

Try to select System -> Administration -> Additional Drivers and check if the system shows a driver for your video capture card.

This other command will list the hardware detected on your computer:

```

sudo lshw

```

---

### Post by williepabon on 2011-07-30
> **lmarmisa said:**
> Try to select System -> Administration -> Additional Drivers and check if the system shows a driver for your video capture card.

This other command will list the hardware detected on your computer:

```

sudo lshw

```

My Ubuntu version is 10.04 LTS. the selections it has is System -> Administration -> Hardware Drivers. I would like to know if, after the system already booted up, there is a command to initiate a hardware discovery process. Thanks.

---

