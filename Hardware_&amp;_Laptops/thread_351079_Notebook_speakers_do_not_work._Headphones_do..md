---
title: "Notebook speakers do not work. Headphones do."
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by wdenhaan on 2007-02-01
Recently, I installed Edgy on my new Acer notebook. For some reason however, the internal speakers do not work. When i plugin my headphones it does produce sound, so i guess the sound card works. 

lspci lists: 
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)

Any ideas?

---

### Post by sirozha on 2007-02-01
> **wdenhaan said:**
> Recently, I installed Edgy on my new Acer notebook. For some reason however, the internal speakers do not work. When i plugin my headphones it does produce sound, so i guess the sound card works. 

lspci lists: 
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)

Any ideas?

Use the speaker icon on your top bar, double click on it, and unmute some of the options there  slide the controls all the way up. It appears that headpohones are internal speakers are not controlled by one master volume control in Ubuntu 6.10.

---

### Post by ivansv on 2007-02-01
for some reason, too lengthy to discuss, some laptops have to install linux oss with acpi=off or there is no sound on linux. laptop mfrs. design the acpi for windows and that corrupts the acpi on linux thus no sound.for more info google acpi and look around.

---

### Post by ivansv on 2007-02-01
should have added this on my previous post. reinstall ubuntu, when you get the boot prompt press F6 for more boot options. you will get a string of boot parameters at the bottom of the screen, simply add acpi=off at the end of the string press ENTER and proceed with a normal install. when you boot into ubuntu you should have sound. works on my laptop and not just with ubuntu but other linux oss as well.

---

### Post by wdenhaan on 2007-02-02
sirozha: I do not have the notebook with me now, but I will try that tonight, but i doubt it will work. I'll keep you posted. 

ivansv: Is there any way to turn acpi off without reinstalling? I'm quite settled, imported all my settings from my previous computer, installed the most important apps i use, etc. Don't want to do it all over again.

---

### Post by wdenhaan on 2007-02-02
I'll add acpi=off to the 'kopt=' line in /boot/grub/menu.lst. I think that should do the job.

---

### Post by ivansv on 2007-02-02
i suppose so but i've never done it that way, after the install.sorry.
doing it after the install might involve recompiling the kernel cause when you install with acpi on the kernel mod -acpi- getsinstalled. i've never compiled a kernel don't want to go there.
might be a good exercise though.

---

