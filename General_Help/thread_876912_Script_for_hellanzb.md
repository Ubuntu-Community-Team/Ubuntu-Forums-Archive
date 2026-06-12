---
title: "Script for hellanzb"
date: 2008-08-01
forum: General Help
---

### Post by jeepers on 2008-08-01
I'm using hellanzb for my binary downloads...I want to make the "/usr/bin/hellanzb" file executable and atatche (sp) an icon to it.

I think i have to use the /bin/bash script but have no idea how to go about it.

cheers

edit: ive had a go at doing it myself is this O.K.

#! /bin/bash
# NZB Binary Downloader
/usr/bin/hellanzb
echo Start hellanzb

then chmod +x to make it executable.

next if this works, how do i add an icon to it ?.

cheers

---

### Post by justleen on 2008-08-01
that should work, yea..

but, if you want an icon, you just need to create a new app launcher/shortcut..
right click panel > add> custom app launcher
in the command field, you enter the command.

in this case, you can just as easy add "/usr/bin/hellanzb"  in the command field, instead of creating a script with output that you wont see...

---

### Post by rahmath on 2008-08-01
What "justleen" said is right. For this, u done need any kind of shell script. just add the binary as "justleen" said, and use it directly...

thats all..

---

### Post by jeepers on 2008-08-01
Thanks for that...yes i never thought of doing it that way -- did and it works :)

cheers

---

