---
title: "[SOLVED] virtual cdrom to mount images"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by mdewet on 2008-01-25
Is there an application to create a virtual cd-rom  so that I can mount a cd image?(eg. Daemon for Windows).

---

### Post by yabbadabbadont on 2008-01-25
If the image is an ISO file, you can mount it directly using the "loop" mount option.

Edit: How about some details...  :D  In a terminal window, I would do something like this:
```
sudo mkdir /media/CDImage
sudo mount /path/to/ISO-file /media/CDImage -o loop
```
If you get an error about no loopback support, then run "sudo modprobe loop" and try again.  When you are done using the image, unmount it with
```
sudo umount /media/CDImage
```

---

### Post by lakris61 on 2008-01-25
> **mdewet said:**
> Is there an application to create a virtual cd-rom  so that I can mount a cd image?(eg. Daemon for Windows).

You can create an iso-image of any cd/dvd with the command

dd if=/dev/cdrom of=my-cd.iso

and then mount it with 

mount -o loop my-cd.iso /media/my-cd

The mount point must exist. You may need to be root mount it. Example,
sudo mkdir /media/my-cd
sudo mount -o loop my-cd.iso /media/my-cd


I am sure there are GUI-tools around, and certainly mount options in most file managers. But I haven't really used any.

/Lakris

PS You can also create iso-images from almost anything, directories, other media, etc and then mount it or burn it. Have a look at mkisofs.

---

### Post by kpkeerthi on 2008-01-25
> 
dd if=/dev/cdrom of=my-cd.iso


Make sure your device is unmounted before you run **dd** command.

```
sudo umount /dev/cdrom
```

---

### Post by kplaxmaster on 2008-01-25
> **mdewet said:**
> Is there an application to create a virtual cd-rom  so that I can mount a cd image?(eg. Daemon for Windows).

Simply put... yes.  However, Daemon tools doesn't just mount a cd-rom, but emulates cd-protection schemes as well.

Thus, if you mount a game CD or any other DRM (digital rights management) media device (anything that requires some CD-key to work or any other protection such as SECUROM), you're application won't recognize the CD and ask for the CD even though you already have it mounted.

Cedega is the only linux application I know of (and please, if I am wrong or if you know any others please let me know), that is able to provide cd-protection so that the game knows if the CD is in the drive or not.

But... if you just wish to mount an ISO image (only ISO images are directly supported by the linux kernel, no BIN/CUE/MDF's are supported as they are proprietary and not the universal standard):
```
sudo mkdir /media/temp/
sudo mount -o loop /location/of/iso_file.iso /media/temp/
```

To unmount the image...
```
sudo umount /media/temp/
```

Note that you don't have to mount all your images in the /media directory, but anywhere you have ownership such as your $HOME directory.

---

### Post by kpkeerthi on 2008-01-25
Checkout [cdemu]("http://cdemu.sourceforge.net/") if you want to mount more 'exotic' image formats

---

### Post by mexpolk on 2008-01-25
sudo mount -t iso9660 -o loop [yourisofile] [mount point directory]

---

### Post by kplaxmaster on 2008-01-25
> **mexpolk said:**
> sudo mount -t iso9660 -o loop [yourisofile] [mount point directory]

Note that the option t (type) will usually be assumed or guessed correctly by the kernel.  However, it is usually good practice to include it as one of your options.  I personally never use it, but thats because I am lazy!  However, you should be better than me and include it :KS

---

