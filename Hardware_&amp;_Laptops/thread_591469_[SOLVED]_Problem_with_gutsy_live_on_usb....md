---
title: "[SOLVED] Problem with gutsy live on usb..."
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by Erraticorder on 2007-10-25
I'm having problems getting gutsy to boot on my usb thumb drive.  I use the [http://ubuntuforums.org/showpost.php?p=1229101&postcount=158]("http://ubuntuforums.org/showpost.php?p=1229101&postcount=158") method that worked perfect for me with fiesty.  I was able to install grub and boot into the live desktop with only two folders on my usb drive; casper and boot.

With gutsy it just drops into initramfs.  I've tried a couple of different things and the only thing that worked is when i used the initrd.gz and vmlinuz from the fiesty live cd with the filesystem.squashfs from gutsy.  The desktop loads up no problem but since the kernel is different none of the drivers work like my mouse, sound, wireless, etc..

Has anyone ran into this problem?  I've tried it on several different computers with no luck.

---

### Post by Erraticorder on 2007-10-25
Success!!!
Ok after searching for awhile I found a way to get it to work.

1.  Follow steps from K0LO in link above.
2.  Delete all folders except for /media/(usb drive)/boot and /media/(usb drive)/casper
3.  Now you have to gzip initrd.gz and change the casper script
```

mkdir temp
cd temp
gzip -dc /media/(usb drive)/casper/initrd.gz | cpio -i
wget pendrivelinux.com/downloads/casper
mv -f casper ./scripts/
find . | cpio -o -H newc | gzip -9 > initrd.gz
mv -f initrd.gz /media/(usb drive)/casper/
cd ../ && rm -r temp

```

After you should be able to boot into gutsy from your usb drive using grub.

---

