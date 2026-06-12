---
title: "sshfs with autofs seems to hang up"
date: 2008-10-03
forum: General Help
---

### Post by oli_ on 2008-10-03
I set up autofs and sshfs like it's described here: [http://www.tjansson.dk/?p=84](http://www.tjansson.dk/?p=84)
When I change into the directory that contains my automount it doesnt work (No such file or directory) - autofs seems to work though, it runs the /etc/auto.sshfs like it's described in the /etc/auto.master file, but that process seems to hang up everytime:
```
oli@Oli:~$ ps aux | grep sshfs
root      6771  0.0  0.0  16300   752 ?        Ss   Oct01   0:00 /usr/sbin/automount --pid-file=/var/run/autofs/_etc_auto.sshfs.pid --timeout=60 --ghost /home/oli/sshfs program /etc/auto.sshfs uid=1000,gid=1000,,
```

My /etc/auto.master file:
```
/home/oli/sshfs /etc/auto.sshfs uid=1000,gid=1000,--timeout=60,--ghost
```

My /etc/auto.sshfs:
```
gtv -fstype=fuse,rw,nodev,nonempty,noatime,allow_other,max_read=65536 :sshfs\#user@host.org\:
```

When the process mentioned above is running I also can't shut down autofs:
```
oli@Oli:~/sshfs$ sudo /etc/init.d/autofs stop
Stopping automounter:
  Couldn't stop automount for /etc/auto.sshfs done.
```

sshfs itself works without any problems (also without asking for a password because of the certificate login):
```
oli@Oli:~$ mkdir test
oli@Oli:~$ sshfs user@host: test/
oli@Oli:~$ ls test/
htdocs  htsdocs  logs
oli@Oli:~$ sudo umount test/
```

How can I fix this?

---

### Post by forkmantis on 2008-11-02
In [this article]("http://www.mccambridge.org/blog/2007/05/totally-seamless-sshfs-under-linux-using-fuse-and-autofs/"), when the author suggests running this as a test:

```
sudo ssh remoteuser@remotehost uptime
```

It struck me that it's the root account running autofs, not your own user account.  This means that your ssh config and keys must be accessible to the root account, not just your user account.  Until now, I've kept all of my ssh configuration in ~/.ssh/config.  To try to get autofs working for me, I decided to make sure my root account had all the configuration information it needed.  I started by creating the .ssh directory and config file as /root/.ssh/config containing:

```

Host <hostname.alias>
  User <remote.username>
  Hostname <fully.qualified.hostname>
  Port <port.i.use>
  IdentityFile /home/<local.username>/.ssh/<passwordless.key.file>

```

Substitute your own <values> in the config above.  Now my root user can ssh to by running "ssh <hostname.alias>" and the correct user, port and key file will be used.

I added a line into my /etc/autofs.sshfs file as follows:

```
<local.mount.directory> -fstype=fuse,rw,nodev,nonempty,noatime,allow_other,max_read=65536 :sshfs\#<hostname.alias>\:

```

Then I reloaded autofs:

```
sudo invoke-rc.d autofs reload
```

and everything works as advertised.

As far as security goes, I tried to lock things down a bit by at least making sure that the key I'm using is limited to the command it needs to run sshfs.  To do this, I prefixed the keys line on the remove server's ~/.ssh/authorized_keys file with:

```
command="/usr/libexec/openssh/sftp-server"
```

I used the technique specified here to find out what to specify as the command:  [http://lists.samba.org/archive/rsync/2003-March/005519.html](http://lists.samba.org/archive/rsync/2003-March/005519.html).  By specifying the sftp-server command, that means that my passwordless key is not allowed to run any other command besides that, which will offer at least some security should someone gain access to your passwordless ssh key.

---

