---
title: "Regarding 'passwd' command"
date: 2008-11-15
forum: General Help
---

### Post by lgp171188 on 2008-11-15
I use Ubuntu 8.04 on my laptop and I am learning bash scripting. I want to write a bash script that would automatically set the passwords of all the users to a specified one. When I googled for learning how to do it, nearly all solutions involved the use of 'passwd --stdin' but the binary of passwd in Ubuntu or Debian doesn't seem to support the --stdin flag. Are there any workarounds? I came around some solutions using 'expect' but I would like to write a script without using it:confused:

---

### Post by seydou on 2010-05-12
Better late than never ;-) Just for the sake of others seeking the same advice - use chpasswd for that purpose, see man page for details.

---

