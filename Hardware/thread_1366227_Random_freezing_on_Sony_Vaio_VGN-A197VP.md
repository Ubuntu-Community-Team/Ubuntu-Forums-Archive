---
title: "Random freezing on Sony Vaio VGN-A197VP"
date: 2009-12-28
forum: Hardware
---

### Post by BBeret on 2009-12-28
Mildly experienced user here.  I've had Ubuntu 9.10 (Karmic Koala) on a Sony Vaio VGN-A197VP laptop for about two months now. I've been experiencing random system freezes every now and then since installation. System settings are mostly default, Compiz is disabled.  Causes: Undetermined. Seems to happen at random while I'm using the machine. Might be more likely to occur under load, although I've both had the system freeze while only moving the mouse cursor over an idle application's window and stay up when deliberately running CPU- and disk-intensive tasks in attempt to reproduce the freeze. Not related to suspend/resume. Doesn't appear to be WM-related.  Typical applications open: Firefox, Pidgin, GVim, Gnome Terminal.   Frequency: Once in about two hours on average, with great variance. Sometimes it might freeze 15 minutes after boot or stay up for 4 hours without freezing.  Symptoms: Screen freezing with a still picture (doesn't update, no corruption), no input being received at all (keyboard, mouse or ACPI power button, magic SysRq key enabled but not responding either), interface lost from network (can't be ping'd or ssh'd, no firewall setup), fans audibly running, no disk activity, no overheating. The machine has to be power cycled to work again.  Reproduction steps: Unknown.  Notes: The laptop is a bit aged and has undergone repair.  So, is there a way out of this gloomy situation? How can this kind of freezing be diagnosed? Feel free to ask for any other details you may need.

---

### Post by Pronker on 2011-03-19
I don't suppose it's relevant for you anymore, but in case anyone else is having this problem so am I. I have a Sony VAIO VPCY11S1E. I haven't had any problems in windows but in ubuntu I've had the same random freezes as described above. I suspect that the problem is related to the wireless direr as I haven't yet experienced problems when this has been switched off. I've tried a different wireless dirver but with the same problem. However, when it freezes there's no flashing capslock/numlock which means that it probably isn't kernel-related. 

Please, if anyone has had this problem and solved it let me know!

---

### Post by angelsneverdie on 2011-05-10
i'm having same issue with my sony vaio y series, vpcy115fx.  Don't remember what it was like under ubuntu 9, but it had this freeze problem in both 10.10 and 11.04.  if anything it might be a little worse in 11.04.  it only seems to happen while using wireless . . .

---

### Post by Pronker on 2011-09-24
I agree, it mainly seems to occur while using wireless. I've tried both the backports driver for atheros and the windoze one @ ndiswrapper but with no help. Another guy mentioned giving grub the "noapic" option during boot (alongside quiet splash or whatever) but it didn't fix the problem. I'm giving up on linux for now.

---

