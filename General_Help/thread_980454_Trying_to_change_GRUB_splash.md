---
title: "Trying to change GRUB splash"
date: 2008-11-12
forum: General Help
---

### Post by Oplix on 2008-11-12
I'm trying to use an image for my GRUB background (an image that will be displayed as a background when I select which OS to boot up when I turn my computer on, before I log in).

I've followed some instructions

```
sudo apt-get install grub-splashimages
sudo ln -s /boot/grub/splashimages/my_image.xpm.gz /boot/grub/splash.xpm.gz
sudo update-grub
```

That was copied from Ubuntu's help.

However, I am not using an image from the grub-splashimages package.

I do have it installed though.

So instead I entered

```
sudo ln -s /home/desktop/splashimage/my_image.xpm.gz /boot/grub/splash.xpm.gz
sudo update-grub
```

But, it still doesn't work.

I've tried some of the other method that Ubuntu's help page lists, but I'm not having much luck. 

One of the difficulties I seem to be having is that I can't remove or add files to my boot/grub. I get an error saying I don't have permission. When I look at the permissions tab for the grub folder, it says "You are not the owner of this computer and do not have permission..."

Does anyone know what's going on there?

Furthermore, can anyone help me figure out how to change this image? I can't put the file with the image into the boot/grub folder, so it's sitting in a folder on my desktop.

I'm running Ubuntu 8.10, thanks for helping.

---

### Post by hansdown on 2008-11-12
Hi Oplix.

If you install startup manager from synaptic, you can go to system> administration> startup manager> appearance, and check the box> bootloader themes. You should be able to choose the one you like.

This may help if I gave you the wrong info.

[http://ruslug.rutgers.edu/~mcgrof/grub-images/#1](http://ruslug.rutgers.edu/~mcgrof/grub-images/#1)

---

### Post by Oplix on 2008-11-13
Worked perfectly, thanks!

P.S. I tried changing the USplash with this program, but that didn't work, it wrote out the loading information instead of displaying any image at all.

---

### Post by kestal on 2008-11-13
> **Oplix said:**
> Worked perfectly, thanks!

P.S. I tried changing the USplash with this program, but that didn't work, it wrote out the loading information instead of displaying any image at all.

yeah.. there seems to be a problem with changing the usplash in ibex via startup manager. Hopefully it gets fixed :)

---

