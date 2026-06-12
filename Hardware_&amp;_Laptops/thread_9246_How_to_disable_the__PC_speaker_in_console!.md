---
title: "How to disable the **** PC speaker in console?!"
date: 2004-12-26
forum: Hardware &amp; Laptops
---

### Post by theh0g on 2004-12-26
Hi,
can anyone please tell me how to disable PC speaker's beeping in terminal window?! It's so **** annoying I can't stand it anymore....beeps every time I press the tab key.

Thanks.

---

### Post by lameaim on 2004-12-26
[QUOTE=theh0g]Hi,
can anyone please tell me how to disable PC speaker's beeping in terminal window?! It's so **** annoying I can't stand it anymore....beeps every time I press the tab key.

Thanks.[/QUOTE]
Open /etc/inputrc as sudo and uncomment/add "set bell-style none". Then logout or reboot.

---

### Post by theh0g on 2004-12-26
[QUOTE=lameaim]Open /etc/inputrc as sudo and uncomment/add "set bell-style none". Then logout or reboot.[/QUOTE]
 I already have that uncommented, but it still beeps. Really irritating. Does anyone have any other idea?

---

### Post by theh0g on 2005-01-06
Bump....

anyone?

---

### Post by castrojo on 2005-01-06
Assuming gnome-terminal, right click, edit current profile, and then uncheck the Terminal bell option.

---

### Post by theh0g on 2005-01-07
[QUOTE=whiprush]Assuming gnome-terminal, right click, edit current profile, and then uncheck the Terminal bell option.[/QUOTE]
 Wow, thanks!!!!

---

### Post by KoS on 2005-01-09
You can also remove the pc speaker module by hand:
rmmod pcspkr
(sudo if needed)

I didn't have time to search for a final solution yet, but I hope this helped a bit...

---

### Post by ruckus on 2005-02-16
Thanks KoS, was driving me around the bend in OOo!

---

### Post by globalspace on 2005-04-17
[QUOTE=whiprush]Assuming gnome-terminal, right click, edit current profile, and then uncheck the Terminal bell option.[/QUOTE]

wow thanks ...
finally this BEEP is out of my head  \\:D/

---

### Post by agds on 2005-05-16
[QUOTE=KoS]You can also remove the pc speaker module by hand:
rmmod pcspkr
(sudo if needed)

I didn't have time to search for a final solution yet, but I hope this helped a bit...[/QUOTE]

Are there any disadvantages to removing this module?

---

### Post by dickohead on 2005-09-19
@ KoS - I COULD KISS YOU!!!! Just changed from Gnome to Xfce, and the bell option wasn't available!!! THANK YOU!!!!!

---

