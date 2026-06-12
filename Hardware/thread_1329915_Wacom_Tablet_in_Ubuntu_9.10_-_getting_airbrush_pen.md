---
title: "Wacom Tablet in Ubuntu 9.10 - getting airbrush pen's button assigned to right click"
date: 2009-11-17
forum: Hardware
---

### Post by wentzr on 2009-11-17
Now, The USB wacom tablet (intuos3) and standard pen works out of the box, with no configuring in 9.10. it's great but i use the airbrush pen and need to configure the button to right click.


First place i went to was /dev/input to do an xxd to find out which event the wacom is assigned to. This used to be the way before 9.10. Wacdump gives me nothing, and none of the event0-7 give me any feedback from the tablet when trying an xxd from /dev/input

Could someone please help me out? I know there aren't a ton of users using the airbrush pen, but I do, and I love it and would love for it to work in ubuntu!!! 

thanks a ton.

Rob

---

### Post by Favux on 2009-11-17
Hi Rob,

If you go to [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") you'll get a little explanation of what's going on.  Basically it's a question of the names of things.  There are a couple of other ways to do it other than using the modified .fdi.  But I think that's probably the simplest way to use wacomcpl and get your stylus button set.

---

### Post by wentzr on 2009-11-18
> **Favux said:**
> Hi Rob,

If you go to [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") you'll get a little explanation of what's going on.  Basically it's a question of the names of things.  There are a couple of other ways to do it other than using the modified .fdi.  But I think that's probably the simplest way to use wacomcpl and get your stylus button set.


interesting. i don't completely follow but will take a stab at this fdi business tomorrow if 'm not too busy. Isn't there just a way to find out what ubuntu thinks the button's input device number is and just use what it's already called and assign it to right click in xorg.conf??

Thanks for the reply. I'd be interested in hearing about the other ways to do it as well.

---

### Post by Favux on 2009-11-18
Hi wentzr,

Not that I know of for a stylus button.  You can get ToolID, ToolSerial (for using two stylus with one tablet in xorg.conf), and TabletID.  I'm pretty sure stylus button would be code level stuff.

Starting with Jaunty you are "suppose" to go to the HAL/.fdi method and not use the xorg.conf for Wacom stuff anymore.  The basic idea is it gives you USB hot plugging.

I should also mention that wacdump doesn't work after X starts.  The linuxwacom X driver wacom_drv.so grabs the input and wacdump can't see it.  You can use xidump as in "xidump stylus" etc.

---

### Post by wentzr on 2009-11-18
> **Favux said:**
> Hi wentzr,

Not that I know of for a stylus button.  You can get ToolID, ToolSerial (for using two stylus with one tablet in xorg.conf), and TabletID.  I'm pretty sure stylus button would be code level stuff.

Starting with Jaunty you are "suppose" to go to the HAL/.fdi method and not use the xorg.conf for Wacom stuff anymore.  The basic idea is it gives you USB hot plugging.

I should also mention that wacdump doesn't work after X starts.  The linuxwacom X driver wacom_drv.so grabs the input and wacdump can't see it.  You can use xidump as in "xidump stylus" etc.

wow. this was cake. wacomcpl is pretty killer.. dunno why I didn't know of it before! Thanks a ton. my tablet buttons are all working now too, nice bonus although I hardly ever use em!

---

### Post by Favux on 2009-11-18
Hi wentzr,

Good, glad you're set up.  You're welcome.

---

