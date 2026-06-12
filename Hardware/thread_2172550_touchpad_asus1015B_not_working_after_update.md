---
title: "touchpad asus1015B not working after update"
date: 2013-09-05
forum: Hardware
---

### Post by sukocohardianto on 2013-09-05
:(

---

### Post by sukocohardianto on 2013-09-05
Elantech TouchPad not move , tab to klick working

---

### Post by sukocohardianto on 2013-09-05
help me please...

---

### Post by sukocohardianto on 2013-09-05
[TABLE]
[TR]
[TD="class: votecell"]              [/TD]
[TD="class: answercell"]     Try this:
  sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
  If it works add both the lines to:
  /etc/rc.local
  But add them **without** the leading sudo. So the lines you'll add to /etc/rc.local will look like:
  modprobe -r psmouse
modprobe psmouse proto=imps
  If /etc/rc.local ends with something like exit 0, make sure to add those lines *before* that exit line.
 
     [TABLE="class: fw"]
[TR]
[TD="class: vt"]            [share]("http://askubuntu.com/a/185362")[improve this answer]("http://askubuntu.com/posts/185362/edit")[/TD]
[TD="class: post-signature, align: right"]                                           [edited Sep 8 '12 at 6:54]("http://askubuntu.com/posts/185362/revisions")          
                      [URL="http://askubuntu.com/users/22949/eliah-kagan"][IMG]https://www.gravatar.com/avatar/631f04176f88084e982e7b343c7973f8?s=32&d=identicon&r=PG[/IMG]
[/URL]         
                      [Eliah Kagan]("http://askubuntu.com/users/22949/eliah-kagan")
            26.1k861143         
     [/TD]
[TD="class: post-signature, align: right"]                                                                       answered Sep 8 '12 at 6:17         
                      [URL="http://askubuntu.com/users/88256/sid"][IMG]https://www.gravatar.com/avatar/0386cd678e4cd186bfdc31dccdb3b72b?s=32&d=identicon&r=PG[/IMG]
[/URL]         
                      [sid]("http://askubuntu.com/users/88256/sid")
            392         
     [/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

thanks

---

