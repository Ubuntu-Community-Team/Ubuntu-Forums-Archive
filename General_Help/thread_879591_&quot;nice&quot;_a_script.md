---
title: "&quot;nice&quot; a script"
date: 2008-08-04
forum: General Help
---

### Post by hyper_ch on 2008-08-04
I just wonder if I have a shell script with various tasks within and nice the whole script to 19. Will then each process within be niced to 19 or would I have to nice every single command inside?

---

### Post by tamoneya on 2008-08-04
it depends how you wrote the script.  If the script is spawning other processes then now you have to "nice" every one of them.  If however your script is simpler and just runs all the commands in order in one thread then you are all set in terms of "nice"ing.

---

### Post by hyper_ch on 2008-08-04
hmmm :) thx for the answer ;)

---

