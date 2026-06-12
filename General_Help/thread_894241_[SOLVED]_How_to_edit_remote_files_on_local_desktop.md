---
title: "[SOLVED] How to edit remote files on local desktop using gedit editor?"
date: 2008-08-19
forum: General Help
---

### Post by abcuser on 2008-08-19
Hi,
I have two computers:
- server: "IBM mainframe zServer" using Suse Linux Enterprise Server
- desktop: my PC using Ubuntu 8.04 Desktop

Bash script files are located on server that doesn't have X-window installed. Server just supports text based environment. But I am so used to use Gnome gedit tool which supports highlighting of sh code (menu View | Highlight Mode | Scripts | sh).

Is there any way I could easily use gedit tool on desktop to edit bash script files on server without copying files from server to desktop and back again?
Thanks,
Abcuser

---

### Post by Vivaldi Gloria on 2008-08-19
I use sshfs to mount a remote directory as a local one. I use the command

```
sudo sshfs user@remote.machine:/remote.dir /where/to/mount -o allow_other
```

Now the remote directory becomes no different than a regular local directory.

---

