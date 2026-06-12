---
title: "ThinkPad Edge internal mic WORKING here is how !"
date: 2012-01-20
forum: Hardware
---

### Post by JKoder on 2012-01-20
Hello everyone. After alot  of research of why my thinkpad internal mic does not work in Ubuntu 11.10, i finaly manage to make it work !

i will write a little  howto in case of anyone will need it:

1. Download and run HDA Analyzer.
2. find the correct setting in the GUI that will make your mic working( mine was PIN 4 if i remember it correctly )
3. after found the correct setting EXPORT it to a python script ( Export button )
4. Put this script in /etc/init.d
5. make it executable ( chmod a+x foo.py )
6.update-rc.d foo.py default
This will make it to autostart , so you will have the changes at every reboot !


Hope it helps someone !
Br.

---

