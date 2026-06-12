---
title: "Read data from serial port"
date: 2012-12-20
forum: Hardware
---

### Post by tzeronone on 2012-12-20
Basically there are two programs that I used. Firstly, realterm in windows to read my serial port. It able to read the data correctly. Secondly, minicom in ubuntu to receive and read my serial port. It able to receive but unable to read correctly. The data that it receives is unreadable. Any one knows why?

---

### Post by Cheesehead on 2012-12-20
Minicon and several other serial port work quite well for me.
Even 'screen' does a good VT100 when I use a null-modem cable.

Have you configured the speed, parity, and stop bits properly? The only problems I ever had with terminal connectivity was when I was *sure* I had them right...but didn't.

---

### Post by tzeronone on 2012-12-20
Yes. I have set it with baud rate 57600 8N1. I expect it to read hexadecimal value. But it gave me "garbage" value...

---

### Post by Wim Sturkenboom on 2012-12-20
minicom can't display binary data; not sure if an application exists for what you want. When I needed one, I rolled my own (very very buggy) tcl/tk application long ago for testing purposes.

---

