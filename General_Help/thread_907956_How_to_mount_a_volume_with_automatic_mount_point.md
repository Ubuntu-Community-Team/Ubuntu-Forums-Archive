---
title: "How to mount a volume with automatic mount point"
date: 2008-09-02
forum: General Help
---

### Post by andrei.kouznetsov on 2008-09-02
Hello everybody!

I have a simple question. I know that a simple way to mount a volume is
```

sudo mkdir /media/my_volume
sudo mount ./win_image -t vfat /media/my_volume

```
and then if I want to unmount it, I do
```

sudo umount /media/my_volume
sudo rm -r /media/my_volume

```

Is there a way to mount a volume without creating the mount point manually? For example, I would like to have
```

sudo mount ./win_image -t vfat /media/my_volume

```
to mount the volume and
```

sudo umount /media/my_volume

```
to unmount it. And it would be nice if the system took care of everything else (creating the mounting point and then deleting it).

I can write a script by myself, but there should be something done already, because it seems convenient. I did googling, but could not find anything useful :(.

Thanks

---

### Post by andrei.kouznetsov on 2008-09-02
bump?

---

### Post by danwood76 on 2008-09-02
well you dont have to remove the mountpoint, you could leave it there and then you would be able to just mount and unmount with one line.
Especially if its something you mount that often.

---

### Post by danwood76 on 2008-09-02
There are a few different nautilus (gnome file manager) scripts that do for examle mounting .iso files.
HAL deals with mounting external drives so that should be fine.

Internal drive moiunting should be taken care of in the /fstab file.

Nautilus scripts can be found here:
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

---

### Post by r4wj4 on 2008-09-03
there is one app that automounts drives for you. just go to add/remove applications and type in "Storage Device Manager". its has a gui and is incredibly easy to use.

heres a video on youtube that basically show you how it works.

[http://www.youtube.com/watch?v=o12k3gRkdIc](http://www.youtube.com/watch?v=o12k3gRkdIc)

---

