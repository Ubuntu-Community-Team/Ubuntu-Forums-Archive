---
title: "file permissions &amp; icecast"
date: 2005-11-24
forum: General Help
---

### Post by djlosch on 2005-11-24
my mp3s are in my home directory under $HOME/music.

icecast has it's own user named icecast2.  i added my user and icecast2 to the icecast group, and did a chgrp icecast2 on the entire directory of music.  then i chmod 750.  when i went to stream, ezstream cant read the files.  then i made a symlink from /etc/icecast2/music to my $HOME/music folder and when i do a sudo -u icecast2 ls /etc/icecast2/music, i get permission denied.  even if i chmod the whole directory to 777 (bad), i still get the same.  any help?

i shouldn't have to run ezstream as my own user or root.

---

