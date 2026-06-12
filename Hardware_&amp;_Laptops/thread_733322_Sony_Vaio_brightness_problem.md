---
title: "Sony Vaio brightness problem"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by Panzermarko on 2008-03-23
Hi!

I've just bought a Sony Vaio NR298 laptop. Naturally brightness control didn!t work, so i installed xbacklight. It worked for awhile, but no i get this error message:

panzermarko@Machine:~$ xbacklight -set 50
No outputs have backlight property


I tried to reinstall xbacklight, but didn't help. What can i do?

---

### Post by BandD on 2008-03-24
I had some issues with screen birghtness as well ith my VAIO FS620.  After a lot of searching I found these two threads which proved to be very helpful for me:

[http://backports.ubuntuforums.com/sh...99#post3594699](http://backports.ubuntuforums.com/sh...99#post3594699)

and

[http://ubuntuforums.org/showthread.php?t=585745](http://ubuntuforums.org/showthread.php?t=585745)

the Basic idea is that the Sony system is sending unexpected numbers (usually 1-7 or something like that, but Sony's numbers seem to be in the tens of millions) to HAL and HAL doens't know how to interpret them.  So the fix, for me was to add
```
value="`expr $value / 19235509`"
```

to the beginning of this script 
```
 sudo gedit /usr/lib/hal/scripts/linux/hal-system-lcd-set-brightness-linux
``` 

as stated in both of those posts.

---

### Post by Panzermarko on 2008-03-24
Thx for the reply, but didn't help. :( I think i messed up something, that xbacklight wants to use.  Any other idea to make xbacklight work again? Perhaps my lcd panel recognization fails, because the error reported by xbacklight shows that x server's primary display don't have a property called backlight. What's more, i don't even have /sys/class/backlight/sony library, and manual backlight adjustment don't work. (just acpi_video0) So what can i do? Do i need to reinstall the system? :confused:

---

### Post by benhur99ph on 2008-03-24
> **BandD said:**
> I had some issues with screen birghtness as well ith my VAIO FS620.  After a lot of searching I found these two threads which proved to be very helpful for me:

[http://backports.ubuntuforums.com/sh...99#post3594699](http://backports.ubuntuforums.com/sh...99#post3594699)

and

[http://ubuntuforums.org/showthread.php?t=585745](http://ubuntuforums.org/showthread.php?t=585745)

the Basic idea is that the Sony system is sending unexpected numbers (usually 1-7 or something like that, but Sony's numbers seem to be in the tens of millions) to HAL and HAL doens't know how to interpret them.  So the fix, for me was to add
```
value="`expr $value / 19235509`"
```

to the beginning of this script 
```
 sudo gedit /usr/lib/hal/scripts/linux/hal-system-lcd-set-brightness-linux
``` 

as stated in both of those posts.

Thanks! It seemed to work for me. Now I can use the screen brightness applet to dim my screen. It also reacts right whenever i unplug my AC adapter. The only thing left now is to make the Fn keys work.

Note: I also used xbacklight before, and I tried using it again after solving the problem with the instruction above and after using xbacklight, the screen brightness wont work. I had to restart my laptop. Maybe xbacklight makes a conflict or something.

---

### Post by Panzermarko on 2008-03-24
Hi again!

Can someone send me the laptop panel's hal entry?

```
lshal | grep laptop_panel
```

Here's mine:

 info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.num_levels = 101  (0x65)  (int)

---

### Post by BandD on 2008-03-24
Here's mine.  I have a Vaio FS620P/W, different model than yours, but here it is anyway:

 info.capabilities = {'laptop_panel'} (string list)
 info.category = 'laptop_panel'  (string)
 laptop_panel.access_method = 'general'  (string)
 laptop_panel.num_levels = 8  ( 0x8 )  (int)  

[note I added a space between the parentheses in the 0x8 part because it was showing a smiley instead of the 8, so the () should be up against the 0 and the 8 w/o a space.]

---

### Post by Panzermarko on 2008-03-24
As far as i know /sys/class/backlight/sony/ directory disappeared. (Right after install i had the directory, but now i don't.) This could be the source of my problems. Any idea?

---

### Post by mjpoetic on 2008-03-31
> **benhur99ph said:**
> The only thing left now is to make the Fn keys work...

Try these threads....

**HOWTO: Adjust brightness on Sony Vaio**
**[http://ubuntuforums.org/showthread.php?p=3873750#post3873750](http://ubuntuforums.org/showthread.php?p=3873750#post3873750)**

[B]Fn keys Sony Vaio
[http://ubuntuforums.org/showthread.php?p=4601018#post4601018](http://ubuntuforums.org/showthread.php?p=4601018#post4601018)
[/B]

---

