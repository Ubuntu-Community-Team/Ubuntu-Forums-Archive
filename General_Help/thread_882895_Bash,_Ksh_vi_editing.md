---
title: "Bash, Ksh vi editing"
date: 2008-08-07
forum: General Help
---

### Post by supradave on 2008-08-07
As we all know, we can set -o vi in Bash and have vi command-line editing.  In Ksh, when you'd do a multi-line command-line script, you could go back to it, press v and edit it in vi, with each line on it's own line.  In Bash, you get the same behavior, except that when you press v and go in to vi, your multi-line command-line script ends up on one line.

Is there any way other than 
export EDITOR="vi -c '%s/;\<space>/<ctrl>v<enter>/g'"
to get this behavior?  The EDITOR string could cause problems with other files, so setting that would not necessarily be a good thing to do.

Thanks,
Dave

---

