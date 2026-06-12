---
title: "no more lovin' from xsane"
date: 2009-09-30
forum: Hardware
---

### Post by renkinjutsu on 2009-09-30
xsane suddenly forgot the scanner i have in my HP C4100 all-in-one printer.. everytime i start it, a dialog pops up telling me ```
"Failed to open device 'v4l:/dev/video0': Invalid argument."
```
Now, i figure it has something to do with the new webcam i bought, as it uses /dev/video0.. so i went ahead and unplugged the webcam from the computer (and even restarted) .. xsane still doesn't see my printer! It dares to say "no devices"!

lsusb detects my printer.. and i print just fine with CUPS! What's wrong, xsane?

---

### Post by renkinjutsu on 2009-09-30
bump^
anybody?

---

### Post by coldReactive on 2009-09-30
Did you try **gksudo xsane** (Not Kubuntu) with ALT+F2?

---

### Post by renkinjutsu on 2009-09-30
good call..
it works that way.
but how do i run it as a regular User? i tried deleting the .sane folder in my home dir. No workee


btw, i love that IBM commercial (your avatar)

---

### Post by coldReactive on 2009-09-30
Try this: [Click Here](http://ubuntuforums.org/showpost.php?p=2151505&postcount=26)

but if you get something *like*: pixma:bunch_of_numbers

you'll be out of luck like me.

---

### Post by renkinjutsu on 2009-10-01
hmm.. there isn't even a group 'scanner'
is that the case for the usual install?

---

