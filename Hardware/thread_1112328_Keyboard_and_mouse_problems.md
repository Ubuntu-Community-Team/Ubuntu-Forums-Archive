---
title: "Keyboard and mouse problems"
date: 2009-03-31
forum: Hardware
---

### Post by sargeant dread on 2009-03-31
Whenever I start Ubuntu I have to unplug my keyboard and mouse from the USB port on my laptop. After Ubuntu starts I can plug it back in and everything is fine, but is there a way for me to fix this?

---

### Post by sargeant dread on 2009-04-06
Nobody wants to help?

---

### Post by Dark_Stang on 2009-04-06
Does the keyboard work okay before the OS is loaded? Does it work in the BIOS or does it navigate the Grub menus okay?

---

### Post by sargeant dread on 2009-04-07
It works in the GRUB loader and bios but if i try to boot ubuntu it fails to upload unless I unplug it first then plug it in when ubuntu is loaded

---

### Post by Dark_Stang on 2009-04-07
Hm... Do they work if you do the following...
Get ONLY the keyboard working. Do a Ctrl+Alt+F1.
run "sudo /etc/init.d/gdm stop" then
"sudo /etc/init.d/gdm start"
Does the keyboard still work? Does the mouse work?

---

### Post by sargeant dread on 2009-04-07
No such file or directory

---

### Post by sargeant dread on 2009-04-18
anyone else have any suggestions?

---

### Post by coffeeaddict22 on 2009-04-18
Hi,
It's sounding like a nonstandard setup.  You're unplugging the keyboard and mouse from your laptop...  Is this a docked laptop?  Is this your setup all the time, or only intermittently? Are they on separate USB ports or both plugging into the same one?  And if so, what happens if only one is plugged in?
For that matter, are they both USB?

Once they are plugged in and working, what does
```
lsusb
``` tell you about them?

---

