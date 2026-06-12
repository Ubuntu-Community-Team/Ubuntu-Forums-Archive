---
title: "Cannot launch different language application from XFCE panel"
date: 2008-11-27
forum: General Help
---

### Post by seshomaru samma on 2008-11-27
I'm running XFCE4 on top of a server install , English language.
I would to be able to launch oowriter in both English and Chinese.
I can run Chinese oowriter with this command:
```
LANG=zh_CN.utf8 oowriter
```
But I don't understand how to create a launcher for it on an XFCE panel. If I put that command I get an error :
```
Could not run "Word &#20013;&#25991;"

Failed to execute child process "LANG=zh_CN.utf8" (No such file or directory)
```
How do I solve that?

---

### Post by seshomaru samma on 2008-11-30
solved it by running this command instead
```
bash -c 'LANG=zh_CN.utf8 oowriter'
```
learned it  [here]("http://ubuntuforums.org/showthread.php?t=138015")

---

