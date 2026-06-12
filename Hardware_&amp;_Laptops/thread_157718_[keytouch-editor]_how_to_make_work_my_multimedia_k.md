---
title: "[keytouch-editor] how to make work my multimedia keys of my latop ?"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by patrick295767 on 2006-04-09
toshiba laptop satellite ...??

 
I did : 
[http://keytouch.sourceforge.net/keytouch_editor/node3.html](http://keytouch.sourceforge.net/keytouch_editor/node3.html)
  
with # keytouch-editor /dev/input/eventX output-file
  
And no way, the touchs are not seen by the keytouch-editor ... 

Help !!

Thank you

Patrick

---

### Post by karthik085 on 2006-04-09
You can configure xorg - keyboard - Option "xkbmodel" - set to whatever model that fits your keyboard.  
Does Preferences->Keyboard Shortcuts->for some multimedia keys help?

---

### Post by scunc_dvl on 2006-12-08
I never got keytouch-editor to respond, but keytouch itself works almost good enough with my PeriPower KB835U as a Microsofft Multimedia keyboard, through keytouch (which wouldn't let me cancel when I ran it, it forced me to pick a keyboard :/). 

keytouch itself finds those extra keys, - apparently keytouch-editor cant :(

I left it at that,... Weirdly, my keyboard comes up in *lsusb* as
[INDENT]ID 0a81:0103 Chesen Electronics Corp. Keyboard[/INDENT], probably what it is internally but I'll never know why, keytouch-editor should be bugfixed so I can support this piece :P

---

