---
title: "Direct Rendering on Macbook Pro (GeForce 9600M GT)"
date: 2009-12-06
forum: Hardware
---

### Post by rybarnes on 2009-12-06
I've recently switched over to Ubuntu on my Macbook Pro, and couldn't be happier. The only issue I still have is with direct rendering. I've installed the updated driver (190) from the Nvidia vdpau PPA, but still no luck. I'm sure I'm doing something simple wrong...any help is welcomed!

---

### Post by mikewhatever on 2009-12-06
I find it hard to believe your card would have direct rendering. Can you post the output of <glxinfo | grep "direct rendering">.

---

### Post by rybarnes on 2009-12-07
I feel like I should make a name for the law that states 'if you ask for help, the issue will resolve itself just to embarrass you'. I did nothing to the computer, just booted it up this morning and direct rendering was working. Anytime before right now glxinfo | grep "direct rendering" returned 'Direct Rendering: NO'.

Thanks though!:P

---

