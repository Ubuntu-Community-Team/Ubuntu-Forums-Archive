---
title: "unetbootin error"
date: 2008-08-27
forum: General Help
---

### Post by dbzkid on 2008-08-27
i have a problem booting on to my usb stick i used unetbootin to install ubuntu 8.04 live with an iso that i downloaded from the ubuntu site, now the thing is it dosnt boot in to my dell desktop but it boots up on to my eee pc, and i did try diffrent usb sticks (im trying to install it on to a pny 4 gb attche, i also used an 8 gb sandisk cruzer with no avail) now it does give me an error, it says 
initrd.gz exceeds size (sorry guys i cant exactly remember what it said ill post exactly what it says in my next post)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)

has anyone ever seen this/ or know how to fix it? (i have used unetbootin befor and it worked perfectly this time its just actin  up)

---

### Post by Taxman415a on 2008-08-27
Couple things to check. Try verifying the image's integrity. Choose that option from the boot menu when booting on the eee pc and if you get errors, then maybe there were problems in the download of your original image or in the unetbootin transfer process. You can check original image with md5sum and compare the md5 hash against what is on the Ubuntu servers where you downloaded it from. 

Otherwise yeah I guess we need the detailed error message and more info on where in the boot process it happens. I take it your dell doesn't have a working cd drive to boot from and that's why you're trying this route? You know you can also use unetbootin to just boot directly from the 8.04 live iso image. Just pick that as the option in the menu.

---

### Post by dbzkid on 2008-08-27
well my dell does have a working cd drive, and i have booted that image from a cd on my dell and i even tested it in virtual box and the image worked (couldent test boot off usb on virtual box) but yeah ill send a picture of the screen that i get, thanks for the reply verry much (im doing off of usb because its a hassle to carry around a cd all the time:lolflag:)

---

### Post by dbzkid on 2008-08-28
okhere is exactly what it says

Loading /ubnkern.............................................
Loading /ubninit..........................................................
.........................................................ready.
[    0.000000] initrd extends beyond end of memory (0x1f688500 > 0x1f688000)
[   37.830317] Kernel panic - not syncing: VSF: Unable to mount root fs on unknown-block(104.1)

I dont know why it says that i selected default and it gave me that, but even if u select any option it gives m e that same thing:confused:
plz anyone if u know plz help

---

