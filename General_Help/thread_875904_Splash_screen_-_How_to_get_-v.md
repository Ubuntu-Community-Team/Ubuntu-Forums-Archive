---
title: "Splash screen - How to get -v ?"
date: 2008-07-31
forum: General Help
---

### Post by Kooothor on 2008-07-31
Hi folks, 

On 6.0 ubuntu used to be verbose when it shutdown.
Like telling you what he is doing before going to sleep.

Is there any way to have the same thing on Hardy ?
Because I watch the computer go off, but it's just a black screen with "Ubuntu" and a progress bar.

It would be nice to have some output to pass the time :)

PS : (same as for the powerup thing)

PPS : Gentoo is very nice on this point, with its system of Grenn/Yellow/Red point)

---

### Post by justleen on 2008-07-31
in your /boot/grub/menu.lst
its set to -quiet -splash by default
remove -quiet : get boot/shuwdown info + splash
remove both: get "oldskool" non-GUI output..

---

### Post by Kooothor on 2008-07-31
Thanks for your response justleen, I get the first part, 

in
> **"/boot/grub/menu.lst]
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d7d3fb0b-8ec2-4eaa-bf7a-ec6cf55a14c7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
[/quote]

I just have to remove the "quiet", isn't it ?

But I don't understand clearly what you say after...:confused:

[QUOTE=justleen said:**
> get boot/shuwdown info + splash
remove both: get "oldskool" non-GUI output..

---

### Post by bks on 2008-07-31
> **justleen said:**
> in your /boot/grub/menu.lst
its set to -quiet -splash by default
remove -quiet : get boot/shuwdown info + splash
remove both: get "oldskool" non-GUI output..

Alternatively you can use Add/Remove to get Startup Manager. It's basically a GUI front end for the menu.lst file.

[Here's a pic.]("http://xtankibuntu.files.wordpress.com/2007/10/startupmanager.jpg")

---

### Post by Kooothor on 2008-07-31
thx bks, will do that !

edit : and it works.

---

