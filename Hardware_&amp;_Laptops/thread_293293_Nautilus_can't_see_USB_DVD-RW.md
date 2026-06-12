---
title: "Nautilus can't see USB DVD-RW"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by russelld on 2006-11-05
Hi
[COLOR="Red"]What processes I can restart to get Nautilus to see external USB DVD-RW without ending the current session? [/COLOR]

I use a USB DVD-RW burner and frequently Nautilus can't see it.
To fix this I have to  either reboot or reinitialise the machine.
This is a tedious hassle as either way I loose a running session.

[COLOR="Blue"]How the machine is initalised:[/COLOR]
[LIST=1]
[*]Log into  console (crtl-alt-F1)
[*]Stop lots of processes by going to level 1 which shuts down lots of processes

```
sudo init 1
```

[*]Then restart multiuser level 3

```
init 3
```

[*]Then log back into session.

[*]Nautilus will now see the external usb DVD-RW
[/LIST]

---

