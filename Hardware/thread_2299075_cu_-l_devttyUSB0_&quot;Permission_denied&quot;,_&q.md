---
title: "cu: -l /dev/ttyUSB0: &quot;Permission denied&quot;, &quot;Line in use&quot;"
date: 2015-10-15
forum: Hardware
---

### Post by Nickolai_Leschov on 2015-10-15
When I'm running the command:
> [FONT=courier new]
sudo cu -l/dev/ttyS0 dir[/FONT]

to probe my USB modem, I'm getting
> [FONT=courier new]
cu: open (/dev/ttyUSB0): Permission denied
cu: ttyUSB0: Line in use
[/FONT]
instead of connecting to the USB modem. The modem is not in use (indeed, I'm trying to bring it up in Ubuntu). I tried disconnecting it and connecting again; it's still "in use".

My situation is exactly like in this unsolved closed thread: [**monitor usb modem signal strength**]("http://ubuntuforums.org/showthread.php?t=1458569").

---

