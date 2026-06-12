---
title: "Permission problem with NUT."
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by nolim on 2007-10-24
Yes, I have read a lot of guides about it, but it still doesn't work!

```
$ upsdrvctl start
Network UPS Tools - UPS driver controller 2.0.5
Network UPS Tools - mustek UPS driver 0.2 (2.0.5)
This driver is obsolete and has been replaced by the "megatec" driver. It will be removed somewhere in the near future.
Can't chdir to /var/run/nut: Permission denied
Driver failed to start (exit status=1)
```
Also with changing to metatec driver the same problem arise.

```
ls -ld /var/run/nut
drwxr-x--- 2 nut nut 60 2007-10-24 12:03 /var/run/nut
```
That's the wanted result by the guides, but still none.
Only after chmod 777 /var/run/nut it works!

There is another permission problem with /dev/ttyS0,
```
ls -l /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 2007-10-24 12:03 /dev/ttyS0
```
need to change it with chmod to 777  that /etc/init.d/nut will work fine, otherwise
nut reports unavailable ups source. Only after changing permissions to those files each
restart upsc works.

Files: 
> [ups1]
driver=mustek
port=/dev/ttyS0
desc = "Advice e-come 600"

[monuser]
password = myPassword
allowfrom = local
upsmon master
 
MONITOR ups1@localhost 1 monuser myPassword master
SHUTDOWNCMD "/sbin/shutdown -h +0"


thanks for your time.

---

### Post by nolim on 2007-10-25
up!
Almost 1 day, and 10 reviews of this page.

---

### Post by Offoffoff on 2008-01-01
Same here! But I have Ippon Winner 750 (megatec driver is suitable). I want to use USB-cable (I have not free COM-port). I have installed Network UPS Tools, but get the same message like this:
superman@superbox:~$ sudo upsdrvctl start
Network UPS Tools - UPS driver controller 2.0.5
Network UPS Tools - Megatec protocol driver 1.5 (2.0.5)
Carlos Rodrigues (c) 2003-2006

Unable to open /dev/usb/hiddev0: Permission denied

  Current user id: nut (111)
Serial port owner: root (0)
Serial port group: root (0)
     Mode of port: 0660

After changing permissons I am getting this:
superman@superbox:~/Scripts$ sudo upsdrvctl start
[sudo] password for supervisor:
Network UPS Tools - UPS driver controller 2.0.5
Network UPS Tools - Megatec protocol driver 1.5 (2.0.5)
Carlos Rodrigues (c) 2003-2006

tcgetattr(/dev/usb/hiddev0): Invalid argument
Driver failed to start (exit status=1)
Can't start /lib/nut/(null): No such file or directory

---

### Post by WayneSteenburg on 2008-04-26
I also encountered this problem in the Hardy Release.  Changing the owner to nut or the permissions to 777 solved it for me as well.  At least until reboot.  Then the owner and permisions were reset.  A permanent solution for me was to add the nut user to the nut group.  Which was not done at install.  I opened a bug report here: [https://bugs.launchpad.net/ubuntu/+source/nut/+bug/222761]("https://bugs.launchpad.net/ubuntu/+source/nut/+bug/222761") I thought I would post my solution in case it helps someone.

Wayne Steenburg

---

### Post by nolim on 2008-04-29
Solved!

adding the user "nut" to group "nut" and to group "dialout" solved the problem.
```
sudo adduser nut nut
sudo adduser nut dialout
```

Now the ups works on system boot.

---

