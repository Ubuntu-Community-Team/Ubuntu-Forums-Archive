---
title: "&quot;Connect to server...&quot; from command line?"
date: 2008-10-25
forum: General Help
---

### Post by jhurwich on 2008-10-25
Hey all,
     Just made the switch to Ubuntu (Hardy) and have been so impressed since day one.  Still very much a beginner, but definitely find myself getting better all the time.  At the moment, I'm trying to mount an sftp connection at startup.  I currently do it with Connect To Server->SSH, which works great but I'd really like it to be done automatically.  If I had the command for the connect to server, I could do it, or if anyone has any other suggestions I would really appreciate them.

Thanks,
Jhurwich

---

### Post by kevstar31 on 2008-10-25
Where do you want the mount point to be?
To learn about the commands in a terminal type
man sftp

---

### Post by berriop on 2008-10-25
the command is 
```
ssh ipaddress
```
for more info try:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

to execute it at start up go to System > Preferences > Sessions
then click the Add button and enter the command there

---

### Post by jhurwich on 2008-10-25
I think connect to server has been mounting it to the root directory, but I don't really mind where it ends up as long as I can still access it somehow.

---

### Post by jhurwich on 2008-10-25
berriop:
I've been able to use the command line to connect to the space by ssh, but what I'd like to do is mount the space so I can access it in Nautilus.  Connect to server does this in gnome, but I can't figure out how to do it at startup.

---

### Post by kevstar31 on 2008-10-25
Try this
[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/")

---

### Post by bryonak on 2008-10-25
If the server is on a local, secure network, take a look into NFS.

If you want access over the internet, I recommend SSHFS. It is very lightweight, the drawback is that it doesn't show you the free disc space on your server and sometimes doesn't recognize symlinks.
Just install it via Synaptic, add yourself to the fuse group (system->administration->users and groups), then log out of your GNOME session and back in.
You can add this to your system->preferences->sessions or to a launcher on your desktop/panel/dock/...:
```
sshfs user@server:/server/dir /local/dir
```
where /server/dir is the folder on your server and /local/dir is the folder you want to mount to. You must first create the local folder!

Another more simple solution is to make a launcher on your desktop, where the command is "nautilus sftp://servername"

EDIT: yay, obviously I'm playing redundancy-man ;)

---

### Post by jhurwich on 2008-10-25
Thanks bryonak, went with the nautilus command and it works beautifully.

---

### Post by sdaau on 2011-10-09
Thanks from me too, bryonak - just a note to self: so the syntax is **NOT**: 
```

nautilus-connect-server ssh://127.0.0.1

```
... **NOR**:
```

nautilus-connect-server sftp://127.0.0.1

```


... but it is, instead: 
```

nautilus sftp://127.0.0.1

```

Cheers!

---

