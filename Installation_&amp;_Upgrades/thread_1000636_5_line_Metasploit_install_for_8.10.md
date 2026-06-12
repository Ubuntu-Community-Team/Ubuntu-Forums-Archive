---
title: "5 line Metasploit install for 8.10"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by clyphox on 2008-12-03
Hi all, guess its upgrade time, i just installed 8.10 as _still_ 1 year in and ubuntu is the only distro that supports my hardware, congrats ubu

Anyway i just installed metasploit (current/trunk) and read some really outdated steps elsewhere on the forum. This is a simpler and effective install for those who care:

5 commands:

#       1      install the basics required for GTK+webrick+autopwn
> apt-get install ruby libopenssl-ruby rdoc rubygems subversion libpango1-ruby libglib2-ruby libgdk-pixbuf2-ruby libgtk2-ruby libatk1-ruby libglade2-ruby sqlite


#       2   decide where u wanna keep the files, your choice.. i used :
> mkdir /usr/local/share/framework-current && cd /usr/local/share/framework-current

#       3  sync the current "trunk" version
> svn co [http://metasploit.com/svn/framework3/trunk/](http://metasploit.com/svn/framework3/trunk/)

#       4 for those too lazy to make aliases/path adjustments, use symlinks
> cd /usr/local/sbin
    # NB...  "rm msf*"   if u installed these previously...

#       5 create the symlinks

> for a in /usr/local/share/framework-current/trunk/msf* ; do ln -s $a; done



Its worth noting the permission of the files (and symlinks). I won't tell u how to fix these.

My logic is if you don't know how to fix permissions you should _not_ be running metasploit.. -rant

Good luck and play friendly ):P

---

### Post by Happypants on 2008-12-03
Your directions gave me an error on the "do" line so you might want to fix that (or tell people how to in another post).

Edit: Got it working using this: [http://blog.surfwerks.com/?p=81](http://blog.surfwerks.com/?p=81)

---

### Post by clyphox on 2008-12-03
Ohh i didn't know that the ubuntu rubygems version (currently 1.8.7) "isn't compatible" as that site says, then again I've not tested all the features like autopwn etc... but everything seems to work hehe... but then again  -untested   /me starts installing virtualbox+fast-track

Just tested the last line too btw, syntax is fine so pls post your error if u get one please.

---

### Post by Happypants on 2008-12-04
```
bash: syntax error near unexpected token `do'

```

Dunno if I'm just missing something or what, but I keep fiddling with it and it keeps spitting that error at me.

---

### Post by mujahied on 2010-03-27
here is the total guide to install this [http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu)

---

