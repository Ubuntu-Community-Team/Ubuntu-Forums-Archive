---
title: "915resolution"
date: 2006-09-27
forum: Hardware &amp; Laptops
---

### Post by that_kid on 2006-09-27
Hey guys,

I think I've tried everything (forums, howto's, blogs):( and still havn't figured out what I'm doing wrong!

I have a dell 700m, with dapper 6.06
I installed 915resolution using synaptic
I edited /etc/default/915resolution

full screen works if I manually 
[INDENT]>sudo /usr/sbin/915resolution 7e 1280 800[/INDENT]

... and then reboot or restart X

but If I don't it goes back to 1024x768

any idea?
Thanks!

---

### Post by wieman01 on 2006-09-27
You need to do this everytime the computer boots. Common problem. You have to do this so that it "sticks":

1. Create boot script (Terminal):
> sudo gedit /etc/init.d/915resolution.sh
2. Paste this (Text Editor):
> /usr/sbin/915resolution 7e 1280 800
3. Save the file.

4. Make the script executable (Terminal):
> sudo chmod +x /etc/init.d/915resolution.sh
5. Create symbolic link (Terminal):
> sudo ln -s /etc/init.d/915resolution S20915resolution
6. Then restart the computer.

---

### Post by that_kid on 2006-09-29
Thanks for your help wieman

Your instructions sort of work, but I think that the script may not be running before gnome starts because I have to ctrl+alt+bkspc at login to get the res.

I was wondering if you could help me clear a couple of things up. What did I link the script too?

Where can I find docs on this, I'm new to linux and don't mind rtfm, but googling tends to get me random crap rather than definitive documentation.

any help is much appreciated!

---

### Post by wieman01 on 2006-09-30
There is no documentation on this one... I figured it out myself. One thing: Have you made the corresponding changes in "xorg.conf" as well?

---

