---
title: "nvidia-xconfig screwed display"
date: 2010-01-03
forum: Hardware
---

### Post by techrascal on 2010-01-03
hi
i was getting an error that "glx" coud not be found so i went to the terminal and typed "nvidia-xconfig" to sset x-server  settings.
but now my display has become of the llowest possible resolution (4:3) and i cant change it through display settings .
can anyone tell me how to get back to the original settings in which my display was of normal resolution(16:9) because i have no clue which files to edit.

i am using ubuntu 9.04 on a sony vaio
output of "lspci -nn | grep VGA"

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 9300M GS [10de:06e5] (rev a1)

thanks

---

### Post by techrascal on 2010-01-03
hey..
i got it done.
on rebooting i got an option of reconfiguring my graphics to default , i chose that and now its done.
silly mistake i made..
thanks

---

