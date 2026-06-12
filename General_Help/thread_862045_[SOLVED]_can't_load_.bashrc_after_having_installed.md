---
title: "[SOLVED] can't load .bashrc after having installed package bash-bashrc.d"
date: 2008-07-17
forum: General Help
---

### Post by igm on 2008-07-17
I recently installed maven, which depends on package bash-bashrc.d. Now my .bashrc isn't loaded anymore. I tried ```
source .bashrc
``` to no avail. My .bash_profile looks okay. I uninstalled bash-bashrc.d and even reinstalled bash. No effect.

What's going on here? Any ideas?

Thank you.

---

### Post by igm on 2008-07-17
Okay, found it. An ls -la in /etc revealed what files have been touched during installation of bash-bashrc.d. I commented out the following in /etc/bash.bashrc

```
# bash.bashrc.d
if [ -d /etc/bash.bashrc.d ]; then
       for f in /etc/bash.bashrc.d/*.sh ; do
               if [ -r "$f" ]; then
                       . $f
               fi
       done
#fi
```

I don't see why this prevented .bashrc from being loaded. My bash scriptfu is not very advanced but all it does is loading .sh files in /etc/bash.bashrc.d/ if this directory exists, ain't it? I actually removed that folder before, so this should not have had any effects at all. Strange.

---

### Post by ibuclaw on 2008-07-17
```
if [ -d /etc/bash.bashrc.d ]; then
```
If /etc/bash.bashrc.d is a directory, then...
```
for f in /etc/bash.bashrc.d/*.sh ; do
```
For every file/folder/link that matches the suffix "*.sh", do...
```
if [ -r "$f" ]; then
```
If the matched file/folder/link is a regular file, then...
```
. $f
```
Load that files functions/values.


It shouldn't have any effect on the bash.bashrc settings, unless it came AFTER the bashrc main settings, then certain variables may get written over in the shell...

Even then, you're ~/.bashrc file takes priority over that.

So maybe you should keep your bespoke functions/aliases in there...

Regards
Iain

---

### Post by igm on 2008-07-17
Thanks, Iain. 

As I said, it works now. Anyways, I have some aliases in .bashrc that weren't overidden for sure (startMyWiki, for example). And source .bashrc didn't make them available either. There has to be something else that was going on, since it didn't work after I removed /etc/bash.bashrc.d and did a *reboot*. After that I am really sure that I did nothing else but commented out the above lines and logged in again.

---

