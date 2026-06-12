---
title: "Powershot A630 doesn't work with Egdy"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by Wakinyan on 2006-10-30
Hello,

Since I have upgraded from Dapper to Edgy my camera Canon Powershot a630 doesn't mount when I plug it. I don't understand what happens because it worked very well with Dapper. I tried with gphoto2 and digikam.

lsusb displays :

```
~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 006: ID 04a9:313a Canon, Inc. 
Bus 002 Device 001: ID 0000:0000
```

and $ gphoto2 --debug -L displays :

```
0.394958 gp-camera(2): Freeing camera...
0.395052 gphoto2-port(2): Libération du port en cours...
0.395136 gphoto2-port(2): Fermeture du port...
0.395241 gphoto2-port(0): Impossible de relâcher l'interface 0 (Opération non permise).
0.395362 libgphoto2/gphoto2-filesys.c(2): Clearing fscache LRU list...
0.395445 libgphoto2/gphoto2-filesys.c(2): fscache LRU list already empty
0.395529 gphoto2-filesystem(2): Internally deleting all folders from '/'...
```


I really don't know what happens since I have upgraded but now I can't transfer my pictures.

Thank you for any help :)

---

### Post by Wakinyan on 2006-11-01
No idea ? I really don't know what to do :(

---

### Post by Wakinyan on 2006-11-08
I have reported the bug on launchpad here :
[https://launchpad.net/distros/ubuntu/+bug/70393](https://launchpad.net/distros/ubuntu/+bug/70393)

I have already met few people who encounter the same import issue.

---

### Post by jhuff on 2007-01-01
I am also having a problem with the PowerShot A630.  Have you had any luck getting it to work with edgy?

---

### Post by chanokin on 2007-02-11
Hello there, this is what i've found so far, it's not as good as i had with dapper but it works.

First install (or update)  libgphoto2.

From your 'lsusb' you now know your  idVendor is 049a and your idProduct is 313a.

Now go and edit libgphoto rules

```
sudo gedit /etc/udev/rules.d/45-libgphoto2.rules
```

add a line in that file that it looks like this

```
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="313a", MODE="0660", GROUP="plugdev"
```

So now is the time to show off your pics just run

```
gnome-volume-manager-gthumb
```

and it should automatically import your photos

I don't know why my camera isn't being autodetected when i plug it in, perhaps i need to reboot!

---

### Post by MentallyInept on 2007-02-22
I would just like to say good job on this fix!

I works perfectly for me.

---

### Post by jean-claude on 2007-03-10
This works for me too with one proviso: I have to be root to import with gthumb...

but it does work.

---

### Post by apunc1 on 2007-03-10
i dont know about edgy, but i'm using dapper 
i'm not insulting your intelligence, but when you plug in the camera via the usb (i do it directly), switch it from picture mode to review mode. in dapper it immediately recognizes the camera.  i'm not sure if you or anyone has tried that in edgy. since nobody has mentioned, though i'd offer :)

---

