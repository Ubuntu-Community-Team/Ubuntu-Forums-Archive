---
title: "Laptop Screen Goes Blank When I Boot Up"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by Noodels on 2007-08-27
Okay, I just put ubuntu on my laptop, and after installing the driver for the nVidia graphics card I was told to reboot, 'Fair enough.' was my initial reaction. When the laptop boots back up and the ubuntu loading bar finishes I get a black screen, and the ubuntu boot noise goes by, and it's like it's working fine without the screen. How do I get my screen back, I kinda need it to see what I'm doing, help?

---

### Post by Lord Illidan on 2007-08-27
What type of graphics card do you have?

---

### Post by Steve1961 on 2007-08-27
> **Noodels said:**
> Okay, I just put ubuntu on my laptop, and after installing the driver for the nVidia graphics card I was told to reboot, 'Fair enough.' was my initial reaction. When the laptop boots back up and the ubuntu loading bar finishes I get a black screen, and the ubuntu boot noise goes by, and it's like it's working fine without the screen. How do I get my screen back, I kinda need it to see what I'm doing, help?

Can you open a virtual terminal by hitting the ctrl-alt-F1 keys.  If you can try typing:

sudo nano /etc/X11/xorg.conf

then change the section:

Driver         "nvidia"

to

Driver         "nv"

Then hit ctrl O to save and ctrl X to exit.  Then type

sudo shutdown -r now

to reboot

---

### Post by Kenobi on 2007-08-27
an alternative is: choose "text mode" in GRUB when booting up, and then you can enter command line stuff.

I had exactly the same problem a week ago and see how we solved it [here: ]("http://ubuntuforums.org/showthread.php?t=533741") Good news I even got the new nvidia drivers working (finally) :)

---

### Post by Noodels on 2007-08-27
> **Lord Illidan said:**
> What type of graphics card do you have?

Didn't I say? It is nVidia.

> **Steve1961 said:**
> Can you open a virtual terminal by hitting the ctrl-alt-F1 keys.  If you can try typing:

sudo nano /etc/X11/xorg.conf

then change the section:

Driver         "nvidia"

to

Driver         "nv"

Then hit ctrl O to save and ctrl X to exit.  Then type

sudo shutdown -r now

to reboot

This worked and I am very grateful, although will this have any effect on my plans to install Beryl/Compiz/Fusion?

> **Kenobi said:**
> an alternative is: choose "text mode" in GRUB when booting up, and then you can enter command line stuff.

I had exactly the same problem a week ago and see how we solved it [here: ]("http://ubuntuforums.org/showthread.php?t=533741") Good news I even got the new nvidia drivers working (finally) :)

I didn't need to turn to this but I'm grateful anyway, thankyou!

---

### Post by Steve1961 on 2007-08-27
> This worked and I am very grateful, although will this have any effect on my plans to install Beryl/Compiz/Fusion?

yes it will have an effect.  basically the nv driver is only a 2d driver supplied with xorg.  However, now that you're up and running again you can uninstall the nvidia driver and try again.  What version nvidia card do you have? To find out just type lspci -v in a terminal, and the search the forums to see if someone else has overcome the problems you had.

---

### Post by Noodels on 2007-08-28
> **Steve1961 said:**
> yes it will have an effect.  basically the nv driver is only a 2d driver supplied with xorg.  However, now that you're up and running again you can uninstall the nvidia driver and try again.  What version nvidia card do you have? To find out just type lspci -v in a terminal, and the search the forums to see if someone else has overcome the problems you had.

Okay, I have a "nVidia Corporation NV17 [GeForce4 420 Go] (rev a3) (prog-if 00 [VGA])", I'm not sure what most of that means but it looks like GeForce4 420 Go is the keyword I am looking for, thankyou. Now I know how to tell what memory my graphics card has too (didn't know how to do that in windows) .

---

