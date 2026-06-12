---
title: "Problems making a persistent live USB flash drive"
date: 2008-07-26
forum: General Help
---

### Post by xenolalia on 2008-07-26
Hi!  I've been trying for some time to make my 8 GB flash drive into a persistent live USB flash drive.  I've tried numerous tutorials, very few of which have worked (I think that there might be something slightly unusual about my flash drive, but that's for another post :wink:).  Anyways, I finally found a tutorial that seems to be working: [http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/).  I have adapted the tutorial (slightly) to fit my needs.  I've made two partitions on my flash drive (in accordance with the tutorial), but instead of using the first partition as the ubuntu partition and the second partition as the casper-rw partition, I use the first partition for the casper-rw partition and the second for the ubuntu partition.  I also deviated slightly from the recomended partition sizes laid out in the tutorial, but aside from that, I follow the tutorial down to the letter.

When I first boot from my flash drive, it seems to work.  I hit enter to select "Run Ubuntu in Persistent Mode saving and restoring changes," and it seems to load okay.  But once it seems like it's done loading, I get a blue screen with a grey box with text in it that says:

"Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but is not owned by user 106 and group 114.  Please correct the ownership or GDM configuration and restart the GDM."

There is a little red "OK" box (I hit the enter key to select it), but I get a long scrolling error that reads "User not known to the underlying authentication module."  I'm a complete Linux novice, and any help getting this to work would be much appreciated!

Thanks in advance!

---

### Post by xenolalia on 2008-08-01
Sorry!  I forgot to add that any other misc. suggestions as to making a persistent live USB flash drive would be much appreciated.  I tried installing ubuntu directly to the flash drive, but I got some strange errors . . .

Oh -- and none of the methods listed here:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

worked either.  I'm kinda' stuck.

Thanks!

---

