---
title: "Serial Port not recognized"
date: 2008-10-31
forum: General Help
---

### Post by Tictoon on 2008-10-31
so I recently had the need to connect a certain device with a Serial port wire, its kind of like a moniter wire but inverted, with the pins on the Computer and the holes on the wire: [http://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Serial_port.jpg/800px-Serial_port.jpg]("http://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Serial_port.jpg/800px-Serial_port.jpg")

Ubuntu doesn't recognize it, so what do I do?

---

### Post by Tictoon on 2008-10-31
Just wanted to know: is this fixed in Intrepid?

---

### Post by Tictoon on 2008-11-01
Bump

---

### Post by Tictoon on 2008-11-01
no one has had a similar problem ?!

---

### Post by Tictoon on 2008-11-01
guess not?

---

### Post by Tictoon on 2008-11-01
can anyone at least help me diagnose the problem?

---

### Post by Tictoon on 2008-11-02
Bump

---

### Post by Tictoon on 2008-11-02
No replies, wow.

---

### Post by cariboo on 2008-11-02
Have you used setserial to set up the serial port? I don't have one any more, so I can't show how.

Jim

---

### Post by Tictoon on 2008-11-03
How do I do that?

---

### Post by cariboo on 2008-11-07
Setserial will set the active serial port so that you can use serial devices. You will probably have to install it first:

```
sudo apt-get install setserial
```

Then to set the serial port:

```
sudo setserial -av /dev/ttyS0
```

If that doesn't work try /dev/ttyS1-->/dev/ttyS3

You may have to enable the serial port in your BIOS.

Jim

---

### Post by Tictoon on 2008-11-08
Thanks!

---

