---
title: "graphical interface for server"
date: 2008-09-22
forum: General Help
---

### Post by Cool Surfer on 2008-09-22
How do i install graphical interface for ubuntu server edition pl...

what was the command?? install ubuntu desktop ??
its not working.

---

### Post by ianhaycox on 2008-09-22
Try,

```
sudo apt-get install ubuntu-desktop

```

---

### Post by Cool Surfer on 2008-09-22
I ried this and it says packages not available

what next pl...

---

### Post by miesnerd on 2008-09-22
> **Cool Surfer said:**
> I ried this and it says packages not available

what next pl...

i know this might sound stupid, but are you sure you're connected to the internet? can you download other packages? Have you checked your sources list?
If I were looking for a GUI for my server, I wouldnt use ubuntu's desktop. I'd go with fluxbox as it will use way less ram.
For that, you'd sudo apt-get install fluxbox

---

### Post by Cool Surfer on 2008-09-22
anyway t install from ubuntu server cd itself?
I tried pinging from console, n destination host catn be reached, so i guess i am not conected. n even if my adsl settings are incorrect, i wouldnt know how to fix at command prompt...

---

### Post by miesnerd on 2008-09-22
> **Cool Surfer said:**
> anyway t install from ubuntu server cd itself?
I tried pinging from console, n destination host catn be reached, so i guess i am not conected. n even if my adsl settings are incorrect, i wouldnt know how to fix at command prompt...

i dont think the ubuntu-desktop packages are on the server install. In fact, im relatively sure they're not. I'd think you could do it with a desktop install cd, though I've never tried that without having a GUI, and hence, synaptic to do it for me.

if you're connected to ethernet, you should be able to run
dhcpcd eth0 up

---

### Post by ianhaycox on 2008-09-22
I don't believe that the GUI/Desktop packages are on the server CD

If you can't ping your router (usually 192.168.1.1) then check your physical connections first and then restart networking via,

```
sudo /etc/init.d/networking restart
```

and check with

```
ifconfig
```

to see if you have an IP address etc.

---

