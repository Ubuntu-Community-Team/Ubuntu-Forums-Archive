---
title: "Redirect LPT to IP? Zebra Thermal Printer - FedEx.com"
date: 2008-09-30
forum: General Help
---

### Post by TyBauz on 2008-09-30
Is there any way to redirect a LPT port to a network address in Ubuntu? The FedEx.com page will only print to LPT ports for some reason. My Zebra ZP500 is connected to a stand alone USB print server on my network.

In Windows I redirected the LPT port to the IP of the printer as a work around. This worked perfectly. In Ubuntu it seems I need to redirect parallel:/dev/lp0 to socket://xx.xx.xx.xx:9100

I can print directly to the Zebra printer on socket://xx.xx.xx.xx:9100, but the FedEx web page does not allow me to select the printer (other than thermal or laser/inkjet)

Redirecting the port might not even be the best solution. If anyone has any better ideas for a work around (firefox plug-in?) I would appreciate it. 

I am using Ubuntu 8.04 (AMD 64), FireFox, and FedEx.com.

Thank you!

---

### Post by dcstar on 2008-09-30
> **TyBauz said:**
> Is there any way to redirect a LPT port to a network address in Ubuntu? The FedEx.com page will only print to LPT ports for some reason. My Zebra ZP500 is connected to a stand alone USB print server on my network.

In Windows I redirected the LPT port to the IP of the printer as a work around. This worked perfectly. In Ubuntu it seems I need to redirect parallel:/dev/lp0 to socket://xx.xx.xx.xx:9100

I can print directly to the Zebra printer on socket://xx.xx.xx.xx:9100, but the FedEx web page does not allow me to select the printer (other than thermal or laser/inkjet)

Redirecting the port might not even be the best solution. If anyone has any better ideas for a work around (firefox plug-in?) I would appreciate it. 

I am using Ubuntu 8.04 (AMD 64), FireFox, and FedEx.com.

Thank you!

Try creating a soft link called "lpt1:" (or whatever works) to the existing parallel port device.

---

### Post by TyBauz on 2008-10-01
I'm not sure how to create a soft link but am checking in to it. Would the soft link just forward the data from the LPT port to a network address? If so I think that would be perfect.

---

### Post by adrianne42 on 2009-11-16
Ubuntu is best linux OS with high graphical resolution....
[RIGHT][[COLOR=#ffffff]_fedex tracking track number ground_[/COLOR]]("http://fedextracking.org")[/RIGHT]

---

### Post by TyBauz on 2009-11-16
> **adrianne42 said:**
> ubuntu is best linux os with high graphical resolution....
[right][[color=#ffffff]_fedex tracking track number ground_[/color]]("http://fedextracking.org")[/right]

pointless

---

