---
title: "no sound in compaq cq45 205 au"
date: 2009-08-01
forum: Hardware
---

### Post by vikashtiwari on 2009-08-01
hi all i installed ubuntu 9.04 on my compaq cq45 205au which has an IDT high definition sound card ..when i clicked on sound icon in preferences it showed many option..  i downloaded alsa driver added option line in config file but still sound is not working ..plz help

---

### Post by vikashtiwari on 2009-08-01
open etc/modprobe.d/alsa-base.conf  and add following lines at the end of the file .. restart the pc sound will work


options snd slots=snd-hda-intel,snd-hda-intel
options snd-hda-intel model=dell-m4-2
# 5Dex.Jpa__qQ4asA:SBx00 Azalia (Intel HDA)
alias snd-card-1 snd-hda-intel
# l4dC.vfAxXUx5zd4:RS780 Azalia controller
alias snd-card-0 snd-hda-intel

---

