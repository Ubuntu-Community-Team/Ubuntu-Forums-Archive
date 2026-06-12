---
title: "[SOLVED] CDs and DVDs won't automount in Hardy"
date: 2008-08-30
forum: General Help
---

### Post by xjgnsdof on 2008-08-30
When I insert a CD or DVD, I have to open a Nautilus window before the medium will mount. I notice, however, that it shows up in my "Places" menu. It just doesn't play, open a window, or anything.

What information should I post, if any, to help?

---

### Post by xjgnsdof on 2008-08-31
up

---

### Post by xjgnsdof on 2008-09-01
up

---

### Post by Peter09 on 2008-09-01
type
```
gconf-editor
```
select the **desktop** folder and then the **gnome** folder and then the **volume_manager** folder.
Tick the options that you need (automount_drives for instance).

PC

---

### Post by xjgnsdof on 2008-09-01
I selected automount_drives, automount_media, and autoplay_dvd, but when I plug in a USB drive or insert a DVD, nothing happens.

---

### Post by Peter09 on 2008-09-01
Try logging out and back in again, gnome may need to be restarted to pick the changes up.

PC

---

### Post by xjgnsdof on 2008-09-01
I rebooted, but it still can't automatically mount or play.

---

### Post by Peter09 on 2008-09-01
In gconf-editor go to

apps-> nautilus->desktop 

and tick volumes_visible.

How are you expecting the mounted volumes to be seen?

PC

---

### Post by xjgnsdof on 2008-09-01
I had "show desktop" unticked. When I ticked "show desktop," everything mounted properly.

New problem: I don't WANT to see my desktop, as Compiz renders a different wallpaper on each side of my desktop cube.

---

### Post by porchrat on 2008-09-01
what does your fstab say?

```
sudo cat /etc/fstab
```

lol nevermind saw you solved it...sort of

---

### Post by Peter09 on 2008-09-01
You need to have the volumes_visible box ticked. The fact that you can see them in the Places menu means that they are mounted ( I think?). If you do not have the volumes_visible box ticked in the nautilus application you will not see them on your desktop.

PC

---

### Post by xjgnsdof on 2008-09-01
I unticked "volumes_visible," and I can still automatically mount, unmount, play, and browse the media that I insert. That setting must refer to the visibility of the volume *to me* (in icon form), whereas "show desktop" dictates the visibility of volumes *to Nautilus*. Very deep...

My research on multiple wallpaper is conclusive: you have to untick "show desktop" for Compiz to render wallpaper on each face of the cube/cylinder/sphere. If you show the desktop, then Nautilus will render (only one) wallpaper.

I'd like to thank all of you for your help (especially Peter09, for getting me on track) as this has been a long-standing problem for me.

---

### Post by Peter09 on 2008-09-01
No Problems, glad to help.

PC

---

