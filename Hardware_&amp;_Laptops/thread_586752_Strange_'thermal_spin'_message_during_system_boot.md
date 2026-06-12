---
title: "Strange 'thermal spin' message during system boot"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by tbraun on 2007-10-22
I switched on my laptop (Dell D820 with Ubuntu 7.04), and received the
message that my ext3 partition had been mounted 31 times, and that a
check would be forced. Ok, this is pretty normal.

At around 50% percent of that the progress bar stopped, and I received
the following odd error message, which I had never seen before:

Oct 22 10:03:30 backpack kernel: [   80.912000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Oct 22 10:03:30 backpack kernel: [   81.788000] ipw3945: Max thermal spin reached

Nothing happened for maybe 30 seconds or so. Then the check continued.
I received the message one more time (at around 90%) but the boot
process just proceeded anyway and completed without any further
issues.

Does anyone know where that error comes from? What causes it and is it
something to worry about?

Thank you very much...

---

### Post by Linicks on 2007-10-22
> Error sending LEDS_CMD: time out after 500ms.

That error I think means you have the wireless switch off on the laptop.

> Max thermal spin reached

I see this too, and it is something to do with the wireless card - I haven't a clue what it means, but everybody seems to get that message.

I guess it means all is ready to go.

Nick

---

