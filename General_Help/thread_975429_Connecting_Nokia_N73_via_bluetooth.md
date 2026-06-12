---
title: "Connecting Nokia N73 via bluetooth"
date: 2008-11-08
forum: General Help
---

### Post by Tallman on 2008-11-08
I want to be able to connect my Nokia N73 phone with my laptop via bluetooth.

My laptop does not have bluetooth on board, so I plug in a USB bluetooth adapter. It gets recognized immediately.

After activiating bluetooth on my phone, I tried:

> $ hcitool scan
Scanning ...
	00:1D:FD:72:94:68	n/a
	00:19:2D:40:6D:20	Paul Nokia N73

The second line is my phone.

So:

> $sudo hcitool cc 00:19:2D:40:6D:20

No response from my phone...

> $ hcitool conn
Connections:


What's next?

---

