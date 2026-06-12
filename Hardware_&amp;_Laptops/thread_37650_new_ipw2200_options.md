---
title: "new ipw2200 options"
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by apu95 on 2005-05-28
I upgraded to the new ipw2200 drivers, hoping I could enable monitor mode on them, but alas, it still won't work for me. Anyway, I was toying around and I noticed that they have the experimental LED enabled. I tried it and it worked for my laptop, so I want to enable this on every boot, and that way I know that the wireless pci is turned on.
How would I go doing this? I know that I have to edit some file that is read at boot time and give it the extra instruction.

Oh yeah, to do it within a console, I have to first do

modprobe -r ipw2200

And then I do 

modprobe ipw2200 led=1 mode=0

Thanks,
Apu

---

### Post by f.prisson on 2005-05-28
Try it this way:

```
sudo touch /etc/modprobe.d/ipw2200
``` ```
sudo gedit /etc/modprobe.de/ipw2200
``` Insert a line:```
options ipw2200 led=1 mode=0
``` After saving the file these options should be always applied when the module is loaded.

---

### Post by apu95 on 2005-05-28
:D worked like a charm, thx a lot.
you wouldn't happen to know why i can't switch it to monitor mode? i get a message saying that the argument is invalid whenever i issue the 'iwconfig eth0 mode monitor'.

---

### Post by f.prisson on 2005-05-28
Monitor mode is supported in the latest version of the driver with the new firmware version 2.3 which supports monitor mode.

---

### Post by apu95 on 2005-05-28
[QUOTE=f.prisson]Monitor mode is supported in the latest version of the driver with the new firmware version 2.3 which supports monitor mode.[/QUOTE]
 yeah, that's why i'm asking. i upgraded to the latest drivers and firmware, yet i keep getting that error

---

### Post by Silwenae on 2005-05-28
[QUOTE=f.prisson]Try it this way:

```
sudo touch /etc/modprobe.d/ipw2200
``` ```
sudo gedit /etc/modprobe.de/ipw2200
``` Insert a line:```
options ipw2200 led=1 mode=0
``` After saving the file these options should be always applied when the module is loaded.[/QUOTE]
 Thank you, thank you!  That worked perfectly.

Sometimes it's the little things that make me happy.

---

