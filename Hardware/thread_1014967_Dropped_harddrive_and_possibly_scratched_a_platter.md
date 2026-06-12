---
title: "Dropped harddrive and possibly scratched a platter, any recovery software on ubuntu"
date: 2008-12-18
forum: Hardware
---

### Post by john183 on 2008-12-18
I am sure you can all get the idea of my question from the title. 

I would just copy all of the files off, but when i try to open some files the drive will automatically unmount and i have to reboot the computer with the drive attached to get it to work again. 

Will DD work if run from a virtual terminal or am i likely to run into the same issue?

Thanks

---

### Post by damis648 on 2008-12-18
Ouch... looks difficult. In such a situation as yours, I would try dd. If that doesn't work, then you are stuck, unless you want to pay for a special machine to do it, I know my step-dad has one at work, it is a couple thousand dollar machine. Whether you will be able to find one though, I don't know.

---

### Post by logos34 on 2008-12-18
well, there is also ddrescue:

[http://wiki.linuxquestions.org/wiki/Dd_rescue](http://wiki.linuxquestions.org/wiki/Dd_rescue)

---

### Post by Endolith on 2009-01-23
GNU ddrescue is supposed to be faster and better than ddrescue.  Install [FONT=Courier New]**gddrescue**[/FONT], not [FONT=Courier New]**ddrescue**[/FONT].

---

### Post by lykwydchykyn on 2009-01-23
testdisk comes with some recovery type utilities, like photorec.  It's mostly for getting files from deleted partitions, though.

---

### Post by Endolith on 2009-01-23
I'm going to try gddrescue on a drive that died back in ~2002.  :)  Wish me luck!

---

### Post by john183 on 2009-02-24
So... long story short, the drive survived the fall, no damage. I ended up copying everything to a new drive directory by directory. Then used dd_rescue to move it all back. Unfortunately, i forgot that the drive i was using as backup was a 250G not 320G like the original. I had fun spending a week trying to get the computer to recognize that the original was actually 320G not 250G. a quick partition resize in a GParted liveCD session fixed that though. Thank you all for the help.

---

