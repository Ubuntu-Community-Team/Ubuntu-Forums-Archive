---
title: "Mantis installation woes..."
date: 2008-08-06
forum: General Help
---

### Post by robiwan on 2008-08-06
I've tried installing mantis on the 8.04 server edition, and it worked the first time, mysql database created, tables 'n all. Although since I had no clue what the administrator password is on mantis, I figured I must've missed it in the installation so me my 'idiot' did apt-get remove mantis. Sure, db was removed and everything else too. Amongst other things the libphp5 for apache so the removal broke the phpmyadmin installation. Nice going. Ok, reinstalled that so php works again and tried reinstalling mantis. Hah, tough luck! No db created, nothing works. Removed, tried to remove everything that has anything to do with mantis. Doesn't work. How can I clean the system so it doesn't have the 'memory' of the previous installation??

Edit: Used aptitude for removal/purge then installation. For some reason this worked out better.
TIA
/R

---

