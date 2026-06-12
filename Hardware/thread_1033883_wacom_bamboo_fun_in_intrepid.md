---
title: "wacom bamboo fun in intrepid?"
date: 2009-01-07
forum: Hardware
---

### Post by higashi on 2009-01-07
i installed Ubuntu Ultimate Edition 8.10 and followed instructions on [this thread]("http://ubuntuforums.org/showthread.php?t=765915&highlight=wacom+bamboo").. i know it says its for hardy, but i didnt know what else to do.

I also read all these things about Xorg, etc. i have no clue what Xorg is or what to do with it so that was kinda useless.

Can anyone tell me how to get my bamboo fun tablet working on intrepid?

---

### Post by Rohan Kapoor on 2009-01-07
> **higashi said:**
> i installed Ubuntu Ultimate Edition 8.10 and followed instructions on [this thread]("http://ubuntuforums.org/showthread.php?t=765915&highlight=wacom+bamboo").. i know it says its for hardy, but i didnt know what else to do.

I also read all these things about Xorg, etc. i have no clue what Xorg is or what to do with it so that was kinda useless.

Can anyone tell me how to get my bamboo fun tablet working on intrepid?
install the package wacom-tools.

```
sudo apt-get install wacom-tools
```

then in the terminal type

```
wacomcpl
```

---

### Post by higashi on 2009-01-07
k after running wacomcpl , i get a pop up thing that says i can select a wacom thing from the list, but my tablet doesnt appear in the list..

---

### Post by Rohan Kapoor on 2009-01-07
Choose the closest one!

---

### Post by higashi on 2009-01-07
The list is blank tho! D:

---

### Post by Rohan Kapoor on 2009-01-08
That strange. Try unistalling, reboot and reinstalling the wacom-tools. Then reboot and try the wacomcpl again.

---

### Post by higashi on 2009-01-10
i did, the same thing happened.
i type "wacomcpl" in the terminal, then get this

```
me@gmy-desktop:~$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"

```

, then i get pop up with a blank list...

---

### Post by Rohan Kapoor on 2009-01-11
That's definately not right! Have you installed all the dependencies properly?

---

### Post by Rohan Kapoor on 2009-01-11
> **higashi said:**
> i did, the same thing happened.
i type "wacomcpl" in the terminal, then get this

```
me@gmy-desktop:~$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"

```

, then i get pop up with a blank list...
That's definately not right! Have you installed all the dependencies properly?

---

### Post by impact on 2009-01-11
> **higashi said:**
> i installed Ubuntu Ultimate Edition 8.10 and followed instructions on [this thread]("http://ubuntuforums.org/showthread.php?t=765915&highlight=wacom+bamboo").. i know it says its for hardy, but i didnt know what else to do.

I also read all these things about Xorg, etc. i have no clue what Xorg is or what to do with it so that was kinda useless.

Can anyone tell me how to get my bamboo fun tablet working on intrepid?

I have a Bamboo Fun and it just works in Intrepid, no installation needed. The only thing that doesn't work are the 4 extra buttons on the pad itself and the eraser.

---

### Post by higashi on 2009-01-11
Impact, well.. lucky you i guess. x]   but mine seems to require installation. i plugged it in and, nothing.

Darth-vader, i did exactly what you told me to do, step by step,, :\

---

### Post by Rohan Kapoor on 2009-01-11
> **higashi said:**
> Impact, well.. lucky you i guess. x]   but mine seems to require installation. i plugged it in and, nothing.

Darth-vader, i did exactly what you told me to do, step by step,, :\
That's very strange!! There may actually be a bug in the wacomcpl command! I'll look into this and let you know when/if I find something!

---

### Post by igknighted on 2009-01-11
see if this helps: [http://ubuntuforums.org/showthread.php?t=967147](http://ubuntuforums.org/showthread.php?t=967147)

EDIT: There were major changes to the way devices like graphics tablets are handled in Ubuntu between 8.04 and 8.10, so do NOT use any guides for older versions.  Many times they will work fine, but this is not one of those cases.

---

### Post by anthony_barker on 2009-01-12
I bought the Wacom bamboo for my daughter and it worked on ubuntu 8.10 on an msi wind u90x out of the box.

Buttons are not mapped or the eraser.

Pen works fine in all graphics apps
2 user defined pen side switches seem to work like mouse clicks as well

I have not installed wacomcpl or changed her Wacom.fdi as I am worried about messing it up.

---

### Post by Rohan Kapoor on 2009-01-12
> **anthony_barker said:**
> I bought the Wacom bamboo for my daughter and it worked on ubuntu 8.10 on an msi wind u90x out of the box.

Buttons are not mapped or the eraser.

Pen works fine in all graphics apps
2 user defined pen side switches seem to work like mouse clicks as well

I have not installed wacomcpl or changed her Wacom.fdi as I am worried about messing it up.
If you will follow the post by igknighted, you should be fine! However the OP's problem is that it's not being detected at all.

---

### Post by higashi on 2009-01-14
Yes! Thanks So Much!! :D
i got my tablet working  (apparently it was already working!?!?  just that i was testing with the mouse, not the pen. i feel like such an idiot) ... but at least now i got my mouse working and stuff...

just one thing--  my scroll weel doesn't work. how can i fix that?

also, if i have gimp over certain programs (such as amsn) , it seems that gimp always stays on top. it doesnt let me focus on amsn at all. its quite frustrating.

& how do i get the eraser to work?
& how can i configure the buttons?


AAAAAAAAAAAAAAAAAH WHY CANT IT JUST WORK HOW IT DID ON HARDYYYYYYYY?!  D':

---

