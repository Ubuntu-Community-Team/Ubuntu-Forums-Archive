---
title: "LiveCD on TOSHIBA M30X"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by hypnos on 2005-08-03
Hello everybody!

I'm trying to get working LiveCD on this laptop. Without any success. I have no problems with PCMCIA (disabling at start) which is normal on Toshiba mashines. The launching process goes on. Everything looks fine but when is coming to start X graphic system freeze. And that's all folks  :? 
I've tried to start this CD with disabled framebuffer. It went a little step forward. After this I just only saw the mouse cursor and nothing else. Another freeze.

Does anybody know how to run Ubuntu on this laptop? At the moment I'm using LiveCD but if go through it I'll try to install it. I'm not sure but I think it's a graphic problem.

P.S. Please don't say it's impossible with Toshiba  :wink:

---

### Post by hypnos on 2005-08-13
Problem solved  :) As I though it was a graphic problem. I had to run Ubuntu with few parameters. Now system is already installed and works fine.

```
hw-detect/start_pcmcia=false noapic nolapic acpi=off vga=790
```

Hope this help someone who has such problems just like me  :grin:

---

