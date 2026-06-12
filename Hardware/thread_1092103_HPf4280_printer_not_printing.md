---
title: "HPf4280 printer not printing"
date: 2009-03-10
forum: Hardware
---

### Post by absolutezero1287 on 2009-03-10
My computer recognizes my printer but whenever I try to print something out all I get is a popup saying that its printing but nothing actually comes out.

1) Yes, its connected.
2) Yes, its turned on.
3) Added myself to the lpadmin group and still nothing.

---

### Post by absolutezero1287 on 2009-03-12
Bump. Please help. I have hplip and all that is needed for an HP printer to work. I don't know what the problem is. I could really use a hand.

---

### Post by zagabog on 2009-03-17
I have exactly the same problem with the same model printer on Ubuntu 8.04

---

### Post by absolutezero1287 on 2009-03-17
I have downloaded the hplip gui (hplip toolbox) and it doesn't recognize the printer. When I was using archlinux it was working fine. Can anyone help?

---

### Post by gozzerd on 2009-03-18
On my machine there seems to be a problem currently with hplip recognising my printer (HP C6180), but I can still print from it. Use the Cups set-up admin stuff by opening a browser (firefox?) and typing in the address bar "http://localhost:631". You may be able to get it working fine using the add printer dialogs. Not sure why hplip seems not to be recognizing a printer that cups is printing from. Some sort of a linkage issue somewhere. It was working fine just a couple of weeks ago. Anyway, hplip not working is not decisive. Cups might work anyway.

---

### Post by absolutezero1287 on 2009-03-18
> **gozzerd said:**
> On my machine there seems to be a problem currently with hplip recognising my printer (HP C6180), but I can still print from it. Use the Cups set-up admin stuff by opening a browser (firefox?) and typing in the address bar "http://localhost:631". You may be able to get it working fine using the add printer dialogs. Not sure why hplip seems not to be recognizing a printer that cups is printing from. Some sort of a linkage issue somewhere. It was working fine just a couple of weeks ago. Anyway, hplip not working is not decisive. Cups might work anyway.

That's the thing, CUPS recognizes the printer but when I try to print nothing comes out. Hplip toolbox doesn't recognize the printer.

---

### Post by absolutezero1287 on 2009-03-23
Problem solved:I got the latest version of [hplip]("http://hplipopensource.com/hplip-web/index.html") and installed it. Just chmod +x to make the file executable and run it.

Also, uninstall anything relating to hplip before hand.

---

