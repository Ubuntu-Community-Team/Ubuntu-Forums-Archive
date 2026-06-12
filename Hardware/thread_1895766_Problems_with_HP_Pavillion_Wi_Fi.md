---
title: "Problems with HP Pavillion Wi Fi"
date: 2011-12-15
forum: Hardware
---

### Post by Jayhawker on 2011-12-15
Is there any problem by chance with WiFi in HP laptops? I've a Pavillion and a note book and there is no way to get they recognize my router. Instead, they can recognize others. But when running using Windows, the WiFi works perfectly. 

Is there any way to make HP WiFi works with Ubuntu?

Thanks a lot

---

### Post by Jayhawker on 2011-12-16
Any help, please!


> **Jayhawker said:**
> Is there any problem by chance with WiFi in HP laptops? I've a Pavillion and a note book and there is no way to get they recognize my router. Instead, they can recognize others. But when running using Windows, the WiFi works perfectly. 

Is there any way to make HP WiFi works with Ubuntu?

Thanks a lot

---

### Post by Jayhawker on 2011-12-21
Doesn't anyone know the problem with Ubuntu WIfi and HP Pavillion Laptop? Mine detects many others but mine?

Thanks

---

### Post by TBABill on 2011-12-21
Did you try changing the encryption on your own network to see if it's a matter of settings, or are you thinking it's a driver issue?

---

### Post by Jayhawker on 2011-12-21
Sorry, but I don't know how to change encryption? How I manage it, please?

Otherwise, maybe it is a driver matter.

Thanks


> **TBABill said:**
> Did you try changing the encryption on your own network to see if it's a matter of settings, or are you thinking it's a driver issue?

---

### Post by soap1 on 2011-12-27
you need to install the b43 driver.  Open up your terminal and type in 
sudo apt-get install firmware-b43-installer

[FONT=Verdana]That should help but if you need more information you can check out 
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
[/FONT]

---

