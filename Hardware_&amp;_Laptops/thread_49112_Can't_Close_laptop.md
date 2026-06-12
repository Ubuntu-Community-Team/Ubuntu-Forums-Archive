---
title: "Can't Close laptop"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by TRAVISL on 2005-07-15
Just about everything works on my Compaq R3000 laptop except everytime I close the lid it stops somehow.  When I open the lid back up I am faced with a black screen with one of these in the upper left "__"  minus the quotes of course.  I've tried pressing all the keys and it doesn't respond to anything.  I end up having to hold down the power button to restart it or sometimes ctrl+alt+del will let me turn it off and then restart it.  

Any help would be great because I hate not being able to close this thing.  Thanks.
Travis

---

### Post by TheOtherShoe on 2005-07-15
This is Ubuntu's standby feature at work. My laptop usually requires some patience before it will become responsive. You can probably bring your computer back to life more quickly by hitting alt+F7. Closing the lid causes a switch to virtual terminal 12; alt+F7 switches back to the virtual terminal that Gnome uses.

If you want to disable this feature you should be able to do so by removing or renaming /etc/acpi/lid.sh


edit: simplified my suggestion about switching virtual terminals

---

### Post by TRAVISL on 2005-07-16
Thanks the alt+7 works if I do it twice.  The first time it asks for my screen saver password then if I hit it again I have my laptop back.
Thanks.
Travis

---

### Post by starlily on 2007-02-15
I had this problem too, I tried a lot of things, but the fix was really simple.

/etc/acpi/lid.sh is *BROKEN*

I replaced it with a much shorter version I found here on the forums, and all is well.

There are MANY posts about lid.sh being broken in a lot of ways in Edgy. Will someone who knows how please put a fixed version in the release updates? This was one of the very few things that made my install less than perfect.

Lily

---

