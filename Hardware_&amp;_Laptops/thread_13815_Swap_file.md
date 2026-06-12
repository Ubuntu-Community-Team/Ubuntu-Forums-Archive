---
title: "Swap file"
date: 2005-02-02
forum: Hardware &amp; Laptops
---

### Post by Cecil on 2005-02-02
Sorry if this is the wrong forum. How do I set-up the swap file? I have a separate partition for it, but I don't know how to set it up.

---

### Post by crane on 2005-02-02
What are you using to set it up?

---

### Post by Cecil on 2005-02-02
I don't know what to use. I'm still too used to using WindowsXP. Basically, during setup of Ubuntu, I created an extra partition and made it's mount point, /swap, though, obviously, there's more to it than that. Do I have to re-create the partition in a certain way? And, what utility would I use to do so? Sorry about this, I'm a complete newbie when it comes to Linux.

---

### Post by malegria on 2005-02-03
Here's how to do it. Find out what partition it is. If it's the 3rd one, then it's name is most likely 'hda3'

If that is so, follow these instructions:
Open a terminal.
type: sudo fdisk /dev/hda
When it says "Command (m for help):, type the letter 'p'
You will see how your hard disk is layed out.
Now press the letter 't'  (This allows you to change the partition type, in your case to 'Linux Swap')
Once you press 't' put in the partition number of the partition you want to make 'swap.' It will most likely be '3.' If so, type in '3' [type this if the partition to make swap is the 3rd one. if not, just change the number]
You will now see:
Hex code....., when you do type '82' (this makes the partition a swap)
Now press 'p' again to make sure you did it  right.
Once you're sure you did it right, type 'w." This will write the changes to your disk.

Now you want to turn the swap on. 
type: sudo swapon /dev/hda3 
[type this if the partition to make swap is the 3rd one. if not, just change the number]

There you go.

---

### Post by Cecil on 2005-02-03
[QUOTE=malegria]Here's how to do it. Find out what partition it is. If it's the 3rd one, then it's name is most likely 'hda3'

If that is so, follow these instructions:
Open a terminal.
type: sudo fdisk /dev/hda
When it says "Command (m for help):, type the letter 'p'
You will see how your hard disk is layed out.
Now press the letter 't'  (This allows you to change the partition type, in your case to 'Linux Swap')
Once you press 't' put in the partition number of the partition you want to make 'swap.' It will most likely be '3.' If so, type in '3' [type this if the partition to make swap is the 3rd one. if not, just change the number]
You will now see:
Hex code....., when you do type '82' (this makes the partition a swap)
Now press 'p' again to make sure you did it  right.
Once you're sure you did it right, type 'w." This will write the changes to your disk.

Now you want to turn the swap on. 
type: sudo swapon /dev/hda3 
[type this if the partition to make swap is the 3rd one. if not, just change the number]

There you go.[/QUOTE]OK, thanks a lot! :D I'll do it right now.

---

### Post by kyle on 2005-02-03
I am having troubles turning it on...or at least i think i am.  The first part of it wen just fine, i did not have any troubles.  When i typed in: 

kyle@kyle:~ $ sudo swapon /dev/hda
Password:
swapon: /dev/hda: Device or resource busy

Does this mean that it is on?  It is quite possible that i am stupid and that it is already  on and i just didn't know that  :D .  Thanks for the help

---

