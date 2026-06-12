---
title: "GRUB Error 17"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by hRob on 2009-09-17
i need some help ppl! I was dualbooting ubuntu 8.04 and XP.. i had to remove the ubuntu installation.. so i did something really stupid! i went to disk management in XP and formatted the ubuntu drive.. when i reinstalled the system boots with the GRUB error 17.. can somebody tell me wat i have to do to get back my xp? please ppl, i need some help desperately! :)

---

### Post by bumanie on 2009-09-17
Insert installation disk, choose repair and in console type FIXBOOT, FIXMBR and answer yes to any questions asked in console. After that you should be able to boot windows and all trace of grub should be gone.

---

### Post by hRob on 2009-09-17
@bumaine : is it enuf if i do the same thing if i get an error 15 message? it removes grub totally from xp right? after that i can just format the disk space from mem mgmt again right?

---

