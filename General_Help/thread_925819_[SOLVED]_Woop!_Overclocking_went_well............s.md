---
title: "[SOLVED] Woop! Overclocking went well............sort of..."
date: 2008-09-21
forum: General Help
---

### Post by Thyssenkrupp on 2008-09-21
So, i got a new heatsink, and overclocked my Dual Core from 2 Ghz, to 2.66, then to 3.0 Ghz, and its running at 28-32C, thats a ok/good temp right??

I just need a way of seeing my cpu temp whilst im in ubuntu,

is there any software/command that will show me my cpu temp??

acpi -t
acpi -v

they dont work.

need help!!



EDIT: I also need to know a command for seeing the frequency my cpu is running at. thanks again!

Thanks in advance!

Jak

---

### Post by rudihawk on 2008-09-21
28-30 is a great temp... :)

as for the commmands - I am not sure hey.

---

### Post by tgalati4 on 2008-09-21
For more detailed temperature/voltage information, you need to install lm-sensors.

For cpu frequency, there is a gnome panel widget that displays it.  Search "frequency" in synaptic.

---

### Post by Thyssenkrupp on 2008-09-21
Thanks. will do that.

Can i just ask you,

run this:
sudo dmidecode | grep "Current Speed" | head -n 1

that give me a cpu freq of 3.0ghz, which is what ive OCed it too, does it give oyu an accurate/precise reading??

---

### Post by -Zeus- on 2008-09-21
shows up correct to me.

---

### Post by Thyssenkrupp on 2008-09-21
Awesome. thanks!!

Ill mark thread as solved,

thanks again!

---

