---
title: "pidgin permission issues, after install from source"
date: 2008-11-05
forum: General Help
---

### Post by eotakos on 2008-11-05
I'm running on hardy, and that's why i installed the latest version of pidgin from source (if you're wondering)

the thing is that users other than me( the sudo entitled user), can't run the program. initially, they couldn't execute the pidgin file, so i changed it's permissions, but it seems that it wasn't enough. This is the output.

rm: cannot remove `/usr/local/pidgin-2.5.2/pidgin/.libs/7320-lt-pidgin': Permission denied
gcc: ../libpurple/.libs/libpurple.so: Permission denied
rm: cannot remove `/usr/local/pidgin-2.5.2/pidgin/.libs/7320-lt-pidgin': Permission denied

what could have i done wrong with the installation? ... i just followed the instractions... you know - ./configure , make , sudo make install!

thanks for any suggestions

---

