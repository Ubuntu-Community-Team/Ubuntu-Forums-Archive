---
title: "USB External Drive?"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by gmc on 2005-11-12
Hi Folks, 

     I just put together an external USB harddrive for my laptop. Partitioning and formatting was easy enough (though pretty slow, 200G HD on USB took 1h 15m to format).

     I've run into a little problem though, when I plug the drive into the USB port, it gets mounted as root. This means I can't write files to it as my regular user. I don't have this problem when I plug in my USB pendrive, I can read/write to it.

     Anyone know how to get this USB harddrive to mount so that I can start backing my systems up?

Thanks
Gord

---

### Post by ssam on 2005-11-12
could change the ownership to your username

open a terminal and cd to the usb disk. then run

```
sudo chown -R $USER:$USER .
```

---

### Post by gmc on 2005-11-12
[QUOTE=ssam]could change the ownership to your username

open a terminal and cd to the usb disk. then run

```
sudo chown -R $USER:$USER .
```[/QUOTE]

Yes, this will band-aid the problem, but I'm sort of in the market for a more
complete solution. 

Thanks just the same
G.

---

### Post by ssam on 2005-11-12
you could do
```
sudo chmod o+wrx
```
to make it writeble by everyone.

or you could play around with /etc/fstab to set the disk to be mounted with a perscribed owner and permissions, but that may not play will with auto mount.

linux is strict, you can't write to a disk without permission.

---

### Post by gmc on 2005-11-12
[QUOTE=ssam]you could do
```
sudo chmod o+wrx
```
to make it writeble by everyone.

or you could play around with /etc/fstab to set the disk to be mounted with a perscribed owner and permissions, but that may not play will with auto mount.

linux is strict, you can't write to a disk without permission.[/QUOTE]

I guess. What doesn't make sense is that the USB ramdisk mounts with the proper attributes but the USB HD won't. I guess I'll have to poke around in the /etc directory.

Thanks
G.

---

### Post by ssam on 2005-11-12
is the usb ramdisk in a format that does not have permissions?

---

### Post by gmc on 2005-11-12
[QUOTE=ssam]is the usb ramdisk in a format that does not have permissions?[/QUOTE]

Actually Yes it is. It's formatted as VFAT32, since it's shared between a Windows machine at work and my Linux systems at home. The USB HD is formatted as ext3.

G.

---

### Post by curtis on 2005-11-12
May I know what make/model you have?
I just ordered a 'Maxtor Personal Storage 3100 200GB USB' external hard drive.
I'll post here if I can get it working with all users.
I think it is something to do with /etc/fstab though...

---

### Post by gmc on 2005-11-12
[QUOTE=curtis]May I know what make/model you have?
I just ordered a 'Maxtor Personal Storage 3100 200GB USB' external hard drive.
I'll post here if I can get it working with all users.
I think it is something to do with /etc/fstab though...[/QUOTE]

Actually, this is a kit that I picked up. The USB external case ($49cnd) and 200G Western Digital ($99cnd). I looked at the prebuilt units but found they cost way too
much and I had a bad experiance with Maxtor harddrives earlier this year, which is why I opted for the WD drive.

Over all, I'm pretty happy with this kit, thought don't expect to break any speed records with it. The USB's 480mbit limit really does slow things down.

G.

The Case: [http://www.factorydirect.ca/catalog/product_spec.php?pcode=ME8209](http://www.factorydirect.ca/catalog/product_spec.php?pcode=ME8209)
The Drive: [http://www.sonnam.com/detail.asp?S=321255971&prod_gp=18&prod_code=151&prod_ID=HDD%2DWD%2D200%2D72R8](http://www.sonnam.com/detail.asp?S=321255971&prod_gp=18&prod_code=151&prod_ID=HDD%2DWD%2D200%2D72R8)

---

