---
title: "Gtub menu editing"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by And6ate9 on 2009-01-19
I was wondering if there is a way to indent lines in grub
to make the menu list easier to read when the computer boots?

---

### Post by Herman on 2009-01-19
:) Well the default colors for the GRUB menu are black and white. I can't imagine anybody having a problem with those colors.

I presume you mean when you are using a splashimage?

If that's what you mean then I think I can help you.
```
[splashimage=(hd0,1)/boot/grub/Ubuntusplash.xpm.gz]("http://users.bigpond.net.au/hermanzone/p15.htm#splash")
foreground ffe4b5
background f4a460
``` You can specify any 'foreground' and any 'background' colors you like out of the 256 web-safe color code.
You'll find lists of colors and their codes in the following two links,

[256 Color Chart]("http://www.eloquentvisions.com/html/mycolors.html") - Eloquent Vision

[16 Color and 256 Color chart]("http://www.webdiner.com/annexe/hexcode/hexcode.htm") - Web Diner's 


'**foreground**' means the color of the main upper left faces of all letters and the big text rectangle that has all our operating system titles in it in our GRUB menu.

'**background**' sets the colors used in the lower-right 'shadowing' for all the letters and the big rectangle around our operating system titles and most importantly the hilite (selection) bar that we shift up or down with our arrow keys to select an operating system to boot.

Was that what you wanted to know, or did I misunderstand your question? :)

---

### Post by Herman on 2009-01-19
If you mean you'd like to see a whole different font, I don't think there's any easy way to change that unless you're a C programmer.

When GRUB2 is ready I have a pretty good idea it will have some nice fonts and probably it will be possible then for users to be able to select from a range of fonts.

Check out this cool website, by a GRUB2 developer - [GRUB Graphical Menu Development Journal]("http://grub.gibibit.com/Journal").

GRUB2 sure will be pretty. At this time it's still not (in my opinion anyway), very useful yet though, unfortunately. GRUB Legacy is far more functional. We'll just have to keep waiting and some day GRUB2 will be great! When it matures it will be a lot better than Legacy GRUB, judging from what I've been reading about it.

---

### Post by And6ate9 on 2009-01-19
no no I would like my grub too look like this:

DIstro 1:
    Ditsro kernel xxxxx
    Distro kernelxxxx recover

Distreo 2:
    Distro Kernel XXxxxx
    Distro kernel xxxxxx recover

Other operating syster
    windoze xp

with the lines indented for easy reading

---

### Post by Herman on 2009-01-19
```
Distro 1:
    ___Ditsro kernel xxxxx
    ___Distro kernelxxxx recover

Distro 2:
    ___Distro Kernel XXxxxx
    ___Distro kernel xxxxxx recover

Other operating systems
    ___windoze xp
```:oops: Okay, now I understand what 'indented' means, I didn't realize I had the wrong definition of what 'indented' means until you prompted me again. I first imagined you meant something like 3D font that looks like it was punched into steel ('dented' into it), LOL, I feel silly now! 
 I had to google it.

Okay, the only way I know for accomplishing something like that, (without becoming a C programmer), is to insert a few underscores in front of the words after the 'title' commands. GRUB ignores whitespaces, as you probably have discovered by now.
I think a few underscores would probably work. :)

CORRECTION: 'GRUB ignores white spaces' - I should have said it does in between the command 'title', and the first character, after that you can probably use whitespaces, so you might only need one underscore, followed by a few white spaces, and then your title.

---

### Post by And6ate9 on 2009-01-19
ok thanks I hope grub2 solves this problem also.
lol look man look how I spelled grub.
HOw do I change the titled to say solved?

---

### Post by Herman on 2009-01-19
[Where is Thanks/Mark Thread Solved?]("http://ubuntuforums.org/showthread.php?t=1043078&highlight=mark+thread+solved")

According to the above link, a couple of the functions we've become accustomed to in the Ubuntu Web Forums are down for the moment, and maybe for a while . . .

---

