---
title: "sshfs not working when called from sleep.d"
date: 2015-12-18
forum: Hardware
---

### Post by s4bba7 on 2015-12-18
[COLOR=#333333][FONT=Lucida Grande]Hello![/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]I'm using sshfs to mount my private share (without password, only RSA key). When I run this command:[/FONT][/COLOR]
```
sshfs <username>@<adress>:/<sharename>/ /home/<username>/<local folder>/ -p <port> -o reconnect,uid=<1000>,gid=<1001>
```
[COLOR=#333333][FONT=Lucida Grande]it mounts share correctly. Then I made file in /etc/pm/sleep.d/50_sshfs and add:[/FONT][/COLOR]
```
#!/bin/bash

case $1 in
        hibernate|suspend)
      grep "/home/<username>/<local folder> fuse.sshfs" /etc/mtab
      if [[ $? -eq 0 ]]; then
         fusermount -u /home/<username>/<local folder>
      fi
                ;;
        resume|thaw)
      sshfs <username>@<adress>:/<sharename>/ /home/<username>/<local folder>/ -p <port> -o reconnect,uid=<1000>,gid=<1001>
                ;;
esac
```

[COLOR=#333333][FONT=Lucida Grande]Before going to sleep or hibernate it unmounts correctly, but after resume or wake up it doesn't mount the share.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Any idea why and how to correct this error?[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Cheers!

//EDIT
Ok, I found that I need to add RSA key to root user. [/FONT][/COLOR]

---

