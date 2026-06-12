---
title: "force newly created files to use &quot;users&quot; as group?"
date: 2008-11-02
forum: General Help
---

### Post by Telexen on 2008-11-02
Hello,

I'm a fairly new Ubuntu. I'm running it on a Media Center server. I come from using Gentoo, where I know (with at least the daemon I'm having trouble with) newly created files on my storage drive would be owned by <user>:users. 

I have HellaNZB running and have had problems with the files it's creating being owned by xbmc:xbmc ...'xbmc' is the user for my frontend login, it's what I want for the user, but I want "users" for the group. I have my permissions all setup correctly, the HellaNZB daemon is setting permissions on new files/folders as 775 (again, what I want).

I know this worked correctly in Gentoo, although I don't recall if it used the ownership I want with something like 'touch newfile', but I know the HellaNZB daemon correctly set ownership as 'xbmc:users'. I'm not sure whether this is a general setting for Ubuntu (maybe /etc/profile? I have very little knowledge of it) or if I can set this with my init script for HellaNZB.

So how can I force Ubuntu to set the owner to <user>:users for new files?

In the event it may be needed, here is my init script for HellaNZB, pulled from a Google search.

```

#!/bin/sh
# Authors: Ivo Trompert
#
#
# /etc/init.d/hellanzb
#
### BEGIN INIT INFO
# Provides:                     hellanzb
# Required-Start:               $local_fs $remote_fs $network
# X-UnitedLinux-Should-Start:
# Required-Stop:                $local_fs $remote_fs $network
# X-UnitedLinux-Should-Stop:
# Default-Start:                3 5
# Default-Stop:                 0 1 2 6
# Short-Description:            Hellanzb
# Description:                  Start the hellanzb daemon
### END INIT INFO

case "$1" in
start)
echo "Starting hellanzb"
su xbmc -c 'python /usr/bin/hellanzb -D  -c /etc/hellanzb.conf' || echo "Failed!" ;;
stop)
echo "hellanzb shutdown"
su xbmc -c 'python /usr/bin/hellanzb -D  -c /etc/hellanzb.conf shutdown' || echo "Failed!" ;;
status)
su xbmc -c 'python /usr/bin/hellanzb -D  -c /etc/hellanzb.conf status' || echo "Failed!" ;;
esac

```

---

### Post by Telexen on 2008-11-02
Down to page 14 overnight...ouch.

It appears that setting "users" to the primary group for the user with 'usermod -g users <user>' will do what I want...so there's the answer for those of you who may find this thread later.

---

