---
title: "quick question undervolting"
date: 2012-01-03
forum: Hardware
---

### Post by drklunk on 2012-01-03
Im in the process of undervolting my CPU in 10.04 LTS using this guide: [http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/](http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/)

my uname -r returned 2.6.32-37, no -phc, so I needed to go into gedit to change "GRUB_DEFAULT=0" to the corresponding line's number. my question is do I count only the "linux image" lines or also the "initrd image" lines?

update-grub returned 
> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-37-generic
Found initrd image: /boot/initrd.img-2.6.32-37-generic
Found linux image: /boot/vmlinuz-2.6.32-36-generic
Found initrd image: /boot/initrd.img-2.6.32-36-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic-phc
Found initrd image: /boot/initrd.img-2.6.32-33-generic-phc
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
done


I tried switching "GRUB_DEFAULT" to 2 as well as 4, then ran uname -r again after saving both times and it returned 2.6.32-37 as it did before.


any help is much appreciated

---

### Post by drklunk on 2012-01-13
*bump*
please help, cant figure out what the deal is. Ive done everything correctly but it still doesnt return the proper line. is there any preliminary packages I could be missing?

---

