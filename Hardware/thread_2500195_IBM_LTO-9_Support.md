---
title: "IBM LTO-9 Support"
date: 2024-08-26
forum: Hardware
---

### Post by christian-issen007 on 2024-08-26
Hi,
We just upgraded a bunch of CentOS Server to Ubuntu 22.04 and are now trying to configure LTO-9 drives but running in to issues. 

Of some reason does IBM Software division support Ubuntu 22.04 and 24.04, but when it comes to Hardware division we got issues where IBM only support 18.04 and 20.04. 
But when we try to compile the lin_tape driver for Ubuntu 22.04 with kernel level 5.15.xxx we got following issue

```

root@ubuntu22:~/rpmbuild/SPECS# rpmbuild -ba lin_tape.spec 
Executing(%prep): /bin/sh -e /var/tmp/rpm-tmp.V8xg9t
+ umask 022
+ cd /root/rpmbuild/BUILD
+ cd /root/rpmbuild/BUILD
+ rm -rf lin_tape-3.0.67
+ /bin/gzip -dc /root/rpmbuild/SOURCES/lin_tape-3.0.67.tgz
+ /bin/tar -xof -
+ STATUS=0
+ [ 0 -ne 0 ]
+ cd lin_tape-3.0.67
+ /bin/chmod -Rf a+rX,u+w,g-w,o-w .
+ RPM_EC=0
+ jobs -p
+ exit 0
Executing(%build): /bin/sh -e /var/tmp/rpm-tmp.Npc2CY
+ umask 022
+ cd /root/rpmbuild/BUILD
+ cd lin_tape-3.0.67
+ make KERNEL=5.15.0-119-generic SFMP=0 driver
make -C /lib/modules/5.15.0-119-generic/build M=/root/rpmbuild/BUILD/lin_tape-3.0.67 PWD=/root/rpmbuild/BUILD/lin_tape-3.0.67 clean
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-119-generic'
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-119-generic'
mkdir bldtmp
make KERNEL=5.15.0-119-generic compileclean lin_tape.ko
make[1]: Entering directory '/root/rpmbuild/BUILD/lin_tape-3.0.67'
rm -f *.o
export PWD
make -C /lib/modules/5.15.0-119-generic/build M=/root/rpmbuild/BUILD/lin_tape-3.0.67 PWD=/root/rpmbuild/BUILD/lin_tape-3.0.67 modules
make[2]: Entering directory '/usr/src/linux-headers-5.15.0-119-generic'
  CC [M]  /root/rpmbuild/BUILD/lin_tape-3.0.67/join.o
  CC [M]  /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_config.o
  CC [M]  /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.o
/root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c: In function 'lin_tape_drive_ioctl':
/root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:2034:55: warning: passing argument 2 of 'scsi_ioctl' makes pointer from integer without a cast [-Wint-conversion]
 2034 |                         rc = scsi_ioctl(drv->dev_obj, command, (void*)arg);
      |                                                       ^~~~~~~
      |                                                       |
      |                                                       uint {aka unsigned int}
In file included from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_ioctl.h:47,
                 from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:23:
./include/scsi/scsi_ioctl.h:48:58: note: expected 'struct gendisk *' but argument is of type 'uint' {aka 'unsigned int'}
   48 | int scsi_ioctl(struct scsi_device *sdev, struct gendisk *disk, fmode_t mode,
      |                                          ~~~~~~~~~~~~~~~~^~~~
/root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:2034:64: warning: passing argument 3 of 'scsi_ioctl' makes integer from pointer without a cast [-Wint-conversion]
 2034 |                         rc = scsi_ioctl(drv->dev_obj, command, (void*)arg);
      |                                                                ^~~~~~~~~~
      |                                                                |
      |                                                                void *
In file included from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_ioctl.h:47,
                 from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:23:
./include/scsi/scsi_ioctl.h:48:72: note: expected 'fmode_t' {aka 'unsigned int'} but argument is of type 'void *'
   48 | int scsi_ioctl(struct scsi_device *sdev, struct gendisk *disk, fmode_t mode,
      |                                                                ~~~~~~~~^~~~
/root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:2034:30: error: too few arguments to function 'scsi_ioctl'
 2034 |                         rc = scsi_ioctl(drv->dev_obj, command, (void*)arg);
      |                              ^~~~~~~~~~
In file included from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_ioctl.h:47,
                 from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:23:
./include/scsi/scsi_ioctl.h:48:5: note: declared here
   48 | int scsi_ioctl(struct scsi_device *sdev, struct gendisk *disk, fmode_t mode,
      |     ^~~~~~~~~~
/root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c: In function 'lin_tape_changer_ioctl':
/root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:5603:51: warning: passing argument 2 of 'scsi_ioctl' makes pointer from integer without a cast [-Wint-conversion]
 5603 |                 rc = scsi_ioctl((*chgp)->dev_obj, command, (void*)arg);
      |                                                   ^~~~~~~
      |                                                   |
      |                                                   uint {aka unsigned int}
In file included from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_ioctl.h:47,
                 from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:23:
./include/scsi/scsi_ioctl.h:48:58: note: expected 'struct gendisk *' but argument is of type 'uint' {aka 'unsigned int'}
   48 | int scsi_ioctl(struct scsi_device *sdev, struct gendisk *disk, fmode_t mode,
      |                                          ~~~~~~~~~~~~~~~~^~~~
/root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:5603:60: warning: passing argument 3 of 'scsi_ioctl' makes integer from pointer without a cast [-Wint-conversion]
 5603 |                 rc = scsi_ioctl((*chgp)->dev_obj, command, (void*)arg);
      |                                                            ^~~~~~~~~~
      |                                                            |
      |                                                            void *
In file included from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_ioctl.h:47,
                 from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:23:
./include/scsi/scsi_ioctl.h:48:72: note: expected 'fmode_t' {aka 'unsigned int'} but argument is of type 'void *'
   48 | int scsi_ioctl(struct scsi_device *sdev, struct gendisk *disk, fmode_t mode,
      |                                                                ~~~~~~~~^~~~
/root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:5603:22: error: too few arguments to function 'scsi_ioctl'
 5603 |                 rc = scsi_ioctl((*chgp)->dev_obj, command, (void*)arg);
      |                      ^~~~~~~~~~
In file included from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_ioctl.h:47,
                 from /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.c:23:
./include/scsi/scsi_ioctl.h:48:5: note: declared here
   48 | int scsi_ioctl(struct scsi_device *sdev, struct gendisk *disk, fmode_t mode,
      |     ^~~~~~~~~~
make[3]: *** [scripts/Makefile.build:297: /root/rpmbuild/BUILD/lin_tape-3.0.67/lin_tape_scsi_tape.o] Error 1
make[2]: *** [Makefile:1911: /root/rpmbuild/BUILD/lin_tape-3.0.67] Error 2
make[2]: Leaving directory '/usr/src/linux-headers-5.15.0-119-generic'
make[1]: *** [Makefile:84: lin_tape.ko] Error 2
make[1]: Leaving directory '/root/rpmbuild/BUILD/lin_tape-3.0.67'
make: *** [Makefile:123: bldtmp/lin_tape-5.15.0-119-generic.ko] Error 2
error: Bad exit status from /var/tmp/rpm-tmp.Npc2CY (%build)




RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.Npc2CY (%build)

```

If I downgrade to kernel version 5.14.21 I got the driver working but our security team don't want to downgrade the kernel.
So I wonder have anyone else tried and get lin_tape driver working with Ubuntu 22 or 24? 

I know IBM only support RedHat and SuSE (of some reasons?), but SuSE 15 SP6 has just upgraded the kernel version from 5.14 to 6.4 so I guess IBM in mean wild will support the new scsi_ioctl.c version but it will probably go a few weeks until IBM support that version, and I really looking for a solution now. 

Really looking forward to see if anyone else has solved this issue. 

Thanks
Christian

---

