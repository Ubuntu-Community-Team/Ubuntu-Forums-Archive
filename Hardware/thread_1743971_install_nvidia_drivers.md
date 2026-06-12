---
title: "install nvidia drivers?"
date: 2011-04-29
forum: Hardware
---

### Post by de1337ed on 2011-04-29
Hey guys, I've been using ubuntu without installing any of the additional drivers. If I do click there, it says I should allow the installation of my nvidia 305m driver. I was wondering that if I did this, whether or not my battery life will decrease? Can someone tell me if it will or not? I feel like the nvidia card would eat up more battery. I have switchable graphics, so I wouldn't mind installing it, but only if I can switch back to my intel graphics also. Thank you.

---

### Post by de1337ed on 2011-04-30
*BUMP* please respond, thank you.

---

### Post by Yellow Pasque on 2011-04-30
nvidia doesn't support optimus/switchable graphics at the moment. Installing the nvidia binary driver won't allow you to use the 305m. You may be able to get it running with the vga_switcheroo script and the open-source nouveau driver, but that's still experimental.

Another thing that may help battery life is using acpi_call to shut off the nvidia card. Otherwise, it's turned on and sucking battery even if you're not using it (great design, huh?).

---

### Post by de1337ed on 2011-05-02
alright, so I guess I just won't install the driver. My switchable graphics light isn't illuminated so I'm fairly sure that I'm running on my intel graphics. Is there a way to make sure?

---

