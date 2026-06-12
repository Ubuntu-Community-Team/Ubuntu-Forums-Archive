---
title: "[SOLVED] Terminal GUI"
date: 2008-08-01
forum: General Help
---

### Post by scottuss on 2008-08-01
Hi all,

I have in my startup script some lines to enable my wifi. I also know the command required for disabling the wifi.

However I would now like to create a GUI to turn it on / off by calling these terminal commands.

Any suggestions?

Thanks in advance

---

### Post by AndrewTheArt on 2008-08-01
[_Zenity_]("http://live.gnome.org/Zenity") is probably what you'd want to use. I believe it come installed by default in Hardy (I might be wrong of course)

Sample usage is here - 

[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-1/)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

In your case, I'd use radio buttons -

```
#!/bin/bash

ans=$(zenity --list --text "Wireless State Manager" --radiolist --column "Option" --column "Description" TRUE "On" FALSE "Off")

if [ $ans = "On" ]; then #turn on wireless here
else # turn off wireless here
fi
```

---

### Post by scottuss on 2008-08-01
Hi thanks for that, your example was exactly what I wanted :guitar:

---

