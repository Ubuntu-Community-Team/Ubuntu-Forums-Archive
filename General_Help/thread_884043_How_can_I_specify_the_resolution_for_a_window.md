---
title: "How can I specify the resolution for a window?"
date: 2008-08-08
forum: General Help
---

### Post by saz on 2008-08-08
Hey guys!

I wanted to configure thunar to open a specific folder when xfce session starts, and I've done that with no problems using the xfce4-autostart-... command, however I need the newly opened window to be maximized.

can you tell me what parameter should I use?

I'm sorry if my english is a bit confusing, it's a bit rusty :)


thanks

---

### Post by saz on 2008-08-10
any1?

---

### Post by unutbu on 2008-08-10
Perhaps install the package devilspie. 

Make a directory in your home account called .devilspie
Add a file called thunar.ds 

Put this as the contents of thunar.ds
```

( if 
  ( is ( application_name ) "thunar" )
  ( begin 
    ( geometry "800x600+0+0" )
  )
)
```

This will make every window created by thunar to be 800 pixels wide, 600 pixels high, and have its top left corner placed at coordinate (0,0). (The origin is in the upper left corner, with the "right" and "down" directions positive. 

If you run devilspie:

```
devilspie &
```

(or have it autostart with each session), then devilspie will control the geometry of each Thunar window as it is created.

These links will give you further info on devilspie:
[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)
[http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)
[http://foosel.org/linux/devilspie](http://foosel.org/linux/devilspie)
[http://ubuntuforums.org/showthread.php?t=634048](http://ubuntuforums.org/showthread.php?t=634048)

---

