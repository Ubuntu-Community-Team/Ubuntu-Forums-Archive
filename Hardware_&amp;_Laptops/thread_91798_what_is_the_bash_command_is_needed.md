---
title: "what is the bash command is needed ?"
date: 2005-11-18
forum: Hardware &amp; Laptops
---

### Post by mrpixels0 on 2005-11-18
when i ran Kaffine today it said my DMA was not turned on for my DVD drive and it gave me a line to enter in a terminal but i have forgotten what that line was and i cannot find any man pages for it on my Kubuntu 5.0.4 cd. 

Doe's anyone know what this command is ?, this is the first Debian Distro i have seen that doe's not let kaffine auto set that parameter :???: .

Thanks in advance for the help.

Edit: Sorry, guys i found the command on some paper, must have forgot that i wrote it down. 


Mrp

---

### Post by daller on 2005-11-18
[QUOTE=mrpixels0]when i ran Kaffine today it said my DMA was not turned on for my DVD drive and it gave me a line to enter in a terminal but i have forgotten what that line was and i cannot find any man pages for it on my Kubuntu 5.0.4 cd. 

Doe's anyone know what this command is ?, this is the first Debian Distro i have seen that doe's not let kaffine auto set that parameter :???: .

Thanks in advance for the help.

Edit: Sorry, guys i found the command on some paper, must have forgot that i wrote it down. 


Mrp[/QUOTE]

Find out what device-name your DVD-drive has (usually /dev/hdc - but it depends on the cable-setup)

try "cat /etc/fstab | grep "cdrom""

Now run hdparm:

sudo hdparm -d1 /dev/hdc (Change to something else, in case you checked fstab!)

Now make it enabled forever:

Add the following to /etc/hdparm.conf

/dev/hdc {
dma = on
}

...DMA should be activated now!

---

### Post by frodon on 2005-11-18
More details here : [http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

