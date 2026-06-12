---
title: "new ATI Driver (8.30.3) anbody tried with edgy (xorg 7.1)"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2006-11-03
Anybody tried this driver, this is new since saturday, the last one i installed on saturday was 8.29.x... maybe they got them straightened out... 

anybody tried them?

thanks.

---

### Post by skyfisher on 2006-11-03
I tried the drivers this morning on my trusty X500 workhorse, but it was lights off for me. GDM failed to load, so eventually I went back to .29 and all is well again.

---

### Post by hardyn on 2006-11-03
hmm backward, and not forward... thats not cool...

mabey ill give it a go this weekend.

Arlen.

---

### Post by Ferrat on 2006-11-03
I got 8.30.3 running under Edgy with good preformance

Read my post there [http://ubuntuforums.org/showthread.php?t=292208](http://ubuntuforums.org/showthread.php?t=292208) on the ATi part

---

### Post by hardyn on 2006-11-04
are you able to suspend and shutdown without horrible graphics corruption and system hang? the main problem i had with the 8.29 drivers?

thanks.

---

### Post by hardyn on 2006-11-04
didn't work for me... shutdown and suspend crashes, just like 8.29...

intereting note though, while running the 8.30 drivers, glxgears would only give me about 450 fps... running the radeon drivers, i am getting ~3000 fps? this doesn't sound right... and yes i checked the ati drivers were actully running...

any comments.

---

### Post by neo_reloaded on 2006-11-05
I have everything working with driver 8.30.03 on my thinkpad.
Card is fireGL T2

Suspend/shutdown works fine. I just noticed that if I try running a glxinfo or any fgl* command, I get a floating point error and core dump - this happens after a suspend.

---

### Post by tubo on 2006-11-06
i also run 8.29 and suspend to ram works fine.

tubo

---

### Post by hardyn on 2006-11-17
i guess i will put this just for the FYI...

adding vga=788 or vga=791 to the end of the boot string in grub takes care of the suspend problems... and makes the ubuntu boot screen look alot better.

---

