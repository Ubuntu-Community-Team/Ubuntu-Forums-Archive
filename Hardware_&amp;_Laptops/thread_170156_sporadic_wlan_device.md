---
title: "sporadic wlan device"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by aztektum on 2006-05-04
so i have this us robotics card that i have setup using ndiswrapper on my laptop. the problem is recently it doesn't seem to want to tx/rx and refuses to find my access point (or any access point for that matter.)

it just shows that the driver is loaded, but doesn't do anythin. any ideas on what i can try to troubleshoot this?

---

### Post by Gannin on 2006-05-04
What card are you using?

---

### Post by aztektum on 2006-05-04
usr5410

---

### Post by aztektum on 2006-05-04
woops nevermind. i figured it out. was because it didn't like my static IP settings which were assigned to wlan0 but with a diff. card

---

