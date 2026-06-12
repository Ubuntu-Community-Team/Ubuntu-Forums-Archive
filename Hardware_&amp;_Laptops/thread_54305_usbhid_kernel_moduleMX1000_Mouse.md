---
title: "usbhid kernel module/MX1000 Mouse"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by corruption on 2005-08-04
Has anyone been able to successfully get the usbhid patch for faster mouse polling and higher resolution running? Maybe its my newbie actions, being out of the 'game' as long as I have, but I can never seem to get it right. If anyone's gotten it done, specifically in relations to a Logitech MX-1000, please please please let me know your process! I'm going mad here!

I'm running the vanilla 5.04 kernel, and my only issue at all is that my high-end mouse feels like $3 mouse from Wal-Mart. I'm doing kernel compiling by using my current config, patching, making the changes, and recompiling. Doing so seems to break everything, I'm pretty much at a loss.

---

### Post by corruption on 2005-08-04
Solved my own problem, it was all in creating the initrd.img correctly. Now the mouse is just flyin!

---

### Post by aveline on 2005-08-04
[QUOTE=corruption]Solved my own problem, it was all in creating the initrd.img correctly. Now the mouse is just flyin![/QUOTE]
 care to post the answer so others can find out how to do this?

aveline

---

### Post by corruption on 2005-08-05
The method I used was a basic compilation covered in depth much better than I could do by <a href="http://ubuntuforums.org/showthread.php?t=43065">others,</a> but essentially I moved the <a href="http://omfg.linux.dk/pub/configurable-hid-mouse-polling/archive/chmp-r5-FULL.patch">usbhid kernel patch</a> into the ubuntu source 2.6.10 directory and ran

$ patch -p1 < chmp-r5-FULL.patch

to patch into the kernel. My configuration method was then to keep my current kernel, the default ubuntu kernel layout. I achieved this by

$ sudo cp -a /boot/config-2.6.10-5-k7 /usr/src/linux/.config
$ cd /usr/src/linux
$ make oldconfig        (to retain the current configuration, and it will also prompt you for the rate you wish to adjust the mouse polling to)
$ sudo make-kpkg clean
$ sudo make-kpkg --append-to-version=<custom name> kernel_image modules-image kernel_headers
$ cd ../
$ dpkg -i *.deb

The next step is to create a functioning initrd.img for loading all the modules. For refrence sake, my custom version is -5.k7.usbhid, keep that in mind when applying for yourself

$ sudo mkinitrd -o /boot/initrd.img-2.6.10-5.k7.usbhid 2.6.10-5.k7.usbhid

next, edit in your /boot/grub/menu.lst to include a reference to this newly created initrd.img under the boot option for your new kernel.

Hope this helps someone else, sure was a fight for me!

---

### Post by corruption on 2005-08-09
Edit to this: 
While my new kernel booted no problem, and after removing all the ubuntu nvidia drivers and installing the official nvidia drivers, I was unable to get 3d to work. I fiddled, poked, and prodded everything, and it all seemed to stem down to the fact that it wasnt the original kernel. Thats where good ol' southern fried engineering came in.. I plugged in a ps2 keyboard, shutdown both the usbcore module and the usbhid module, and replaced them with the modified versions from the newly compiled kernel. One reboot later, all my mouse issues were solved, along with all dependancy issues and 3d issues. I'm sure theres a more eloquent way to get to this end result than the long-winded way I went about it, however, it DOES work quite well, and I couldnt be happier!

---

