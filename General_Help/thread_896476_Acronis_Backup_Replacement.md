---
title: "Acronis Backup Replacement"
date: 2008-08-21
forum: General Help
---

### Post by NoVista on 2008-08-21
I am still in search of a good program, (with a GUI if possible),  to make complete partition images, compress them, validate the image file, and allow me to boot up via a cd if needed to initiate the program to restore the image.

Over the years I have not found what I call a good one yet.
I feel like there's a good one out there staring me in the face, and I don't see it.
I need a recommendation.

---

### Post by merlin051 on 2008-08-21
you want an open source version of Arconis basically then?

you forgot network support ;)

Arconis is an awesome utility

---

### Post by NoVista on 2008-08-21
It is, however I have seen it fail with perfectly good verified images when using the cd to boot and run the program.
I don't think it really fully supports ext3, although it works well, most of the time.

I still need a replacement, that works ALL the time. :(

---

### Post by coffeecat on 2008-08-21
> **NoVista said:**
> I am still in search of a good program, (with a GUI if possible),  to make complete partition images, compress them, validate the image file, and allow me to boot up via a cd if needed to initiate the program to restore the image.

There is a good program, but without a GUI, that comes as standard - it's tar, using the -j or -z compression options. I've used it for years now to make backup images of my Linux installations, and I have restored/cloned them several times with this with success. The only thing missing is your requirement for validation. And there is a bootup CD to restore the image. It's called Ubuntu live CD. :wink:

I've come across howtos where it is recommended to include the --exclude option, as in --exclude=/dev, and threads where people are having problems. Personally, I find the --exclude option an unnecessary complication. Perhaps the problems are down to using --exclude - I don't know. All I do is mount the partition I want to backup from a live CD (or another distro on another partiton), cd into it and:

```
sudo tar -czvf /media/USBdrive/filename.tar.gz *
```And for restore, mount the restore partition, and:

```
sudo tar -xzvf /media/USBdrive/filename.tar.gz /media/destination_partition
```Don't tar from 'within' an installation with --one-file-system. It appears to create a perfectly good .tar.gz file, but you can't restore from it.

---

### Post by qstraza on 2008-08-21
check [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/) its not gui, its livecd or usb, easy to use;>

---

