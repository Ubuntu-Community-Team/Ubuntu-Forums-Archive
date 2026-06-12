---
title: "Startup script fails"
date: 2008-07-15
forum: General Help
---

### Post by nloding on 2008-07-15
I have the following file, vm.sh, in /etc/init.d/:

```
#!/bin/sh
Xvfb :1012 -screen 0 640x480x8 &
sleep 60 && DISPLAY=:1012 vmplayer /image/image.vmx
```

I have added it to rc.local and tried, and added it via *update-rc.d vm.sh defaults* and it still failed.  If I check the running processes with ps auwx, I can see both Xvfb and vmplayer running, but I cannot ping the guest OS.

If I remove the vm.sh script from startup, reboot, and execute the shell script itself, everything starts just fine -- I can ping the guest OS.  Or, if I stop rc.local, killall Xvfb, then start rc.local, it works just fine.  I just doesn't want to work on startup.  syslog and vmware.log don't tell me anything is wrong.

Anyone have any suggestions?  My goal to autostart my vmware image on a headless server.  I partially followed [this tutorial]("http://www.linuxfromscratch.org/hints/downloads/files/vmware-player.txt").

---

### Post by aktiwers on 2008-07-15
Did you remember to make it executable?
```
sudo chmod +x /etc/init.d/vm.sh
```Edit: Sorry I read your post too fast.. just ignore my post

Could you show us how you added it in rc.local?

---

### Post by nloding on 2008-07-15
To snip the top part of my rc.local:

```
#! /bin/sh
PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
  if [ -x /etc/rc.local ]; then
    log_begin_msg "Running local boot scripts (/etc/rc.local)"
    /etc/rc.local
    /etc/init.d/vm.sh
    log_end_msg $?
  fi
}
```

Now that I look at it ... I added it to /etc/init.d/rc.local.  I should have put it in /etc/rc.local, shouldn't I?

---

### Post by nloding on 2008-07-16
Bump :)

---

### Post by bodhi.zazen on 2008-07-16
Try putting those commands in /etc/rc.local

Another option : try the new vmware server 2.0 RC1

The new version is a little buggy, but it includes a web interface which may allow you to more easily manage your remote box.

---

