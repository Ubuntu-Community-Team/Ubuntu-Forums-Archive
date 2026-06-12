---
title: "Using a serial connection in Ubuntu"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by sdamron on 2006-06-17
Hello fine folks...
I need to use a serial connection to a couple of Sun Netra servers, headless they are.

I look under /dev and I see no serial device, how can I use a serial connection?

Thanks.

---

### Post by ranf on 2006-06-17
COM1: is /dev/ttyS0 
COM2 is ttyS1 and so on.

One serial communication program is `minicom'.

---

