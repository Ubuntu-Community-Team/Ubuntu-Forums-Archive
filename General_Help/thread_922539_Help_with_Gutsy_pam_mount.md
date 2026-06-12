---
title: "Help with Gutsy pam_mount"
date: 2008-09-17
forum: General Help
---

### Post by drussell13 on 2008-09-17
Hello all, I am having a little bit of trouble with pam_mount using Ubuntu Gutsy. I have used it in the past on SUSE Enterprise and OpenSuse systems without any problems. But it appears to be a little bit trickier in Ubuntu. I can't find any good documentation out there on *Buntu to help me. But basically here is what I have, and please help if you see I'm missing something.

I installed libpam-mount, added the line I need to in order to mount an ncpfs volume in pam_mount.conf. I put in the following into the pam.d services. (Note, I am using ldap to authenticate which requires a sufficient line in auth,account,session, password). So I read up on the documentation on sourceforge and it says if you are using sufficient to do the following...

```
account sufficient  pam_ldap.so
auth    required    pam_mount.so
auth    sufficient  pam_ldap.so use_first_pass
auth    required    pam_unix.so use_first_pass
session optional    pam_mount.so
```

So thats pretty much how I have it, I have pam_mount as the first line in auth as required then pam_mount as the last line in session as optional. When I log in (I'm just testing using ssh (ssh user@localhost)... It doesn't appear as though pam_mount is even being triggered. I even turned on the debug option in pam_mount.conf.

**By the way** I am able to mount the volumes for users just fine using ncpmount, so its definitely something with pam that is causing me fits.

Anyway, please let me know if I can provide anymore information or if anybody has any ideas. Thanks!!

---

### Post by drussell13 on 2008-09-17
Alright, new update... It appears as though pammount is at least being triggered.  When I log in, it is creating the "H" directory under /home/user that I told it to in pam_mount.conf.  However, it is not actually mounting the drive.  I don't see any errors, what log file is it in?  I will post what my pam.d serives look like right now...

common-auth
```
auth    required        pam_mount.so
auth    sufficient      pam_ldap.so use_first_pass
auth    required        pam_unix.so nullok_secure use_first_pass

```

common-session
```
session required        pam_mkhomedir.so skel=/etc/skel/ umask=0022
session optional        pam_mount.so
session sufficient      pam_ldap.so
session required        pam_unix.so try_first_pass
session optional        pam_foreground.so

```

common-pammount
```

auth       required   pam_mount.so use_first_pass
session    optional   pam_mount.so use_first_pass

```

kdm
```
auth       required     pam_nologin.so
auth       required     pam_env.so readenv=1
auth       required     pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
session    required     pam_limits.so
@include common-account
@include common-password
@include common-session
@include common-pammount

```

I feel as though I am close...Please let me know if I can provide any more information.
Thank you!

---

### Post by drussell13 on 2008-09-17
Another update, found the log in "auth.log".... But here is what I am getting.....

```
Sep 17 11:15:07 sshd[7469]: pam_mount(mount.c:182) checking to see if server/user1.students.SMHS is already mounted at /home/user1/H
Sep 17 11:15:07 sshd[7469]: pam_mount(mount.c:397) creating mount point /home/user1/H
Sep 17 11:15:07 sshd[7469]: pam_mount(mount.c:799) checking for encrypted filesystem key configuration
Sep 17 11:15:07 sshd[7469]: pam_mount(mount.c:819) about to start building mount command
Sep 17 11:15:07 sshd[7469]: pam_mount(misc.c:264) command: /usr/bin/ncpmount [server/user1] [/home/user1/H] [-o] [pass-fd=0,volume=/Voldata/students/user1,user=user1.student
Sep 17 11:15:07 sshd[7470]: pam_mount(misc.c:341) set_myuid(pre): real uid/gid=0:605, effective uid/gid=0:605
Sep 17 11:15:07 sshd[7470]: pam_mount(misc.c:376) set_myuid(post): real uid/gid=0:605, effective uid/gid=0:605
Sep 17 11:15:07 sshd[7469]: pam_mount(mount.c:851) mount errors (should be empty):
Sep 17 11:15:07 sshd[7469]: pam_mount(mount.c:100) pam_mount(misc.c:341)                              set_myuid(pre): real uid/gid=0:605, effective uid/gid=0:605
Sep 17 11:15:07 sshd[7469]: pam_mount(mount.c:100) pam_mount(misc.c:376)                                   set_myuid(post): real uid/gid=0:605, effective uid/gid=0:605
Sep 17 11:15:07 sshd[7469]: pam_mount(mount.c:100) Group `user1' does not exist on this machine
Sep 17 11:15:07 sshd[7469]: pam_mount(mount.c:854)waiting for mount
Sep 17 11:15:07 sshd[7469]: pam_mount(pam_mount.c:480) mount of /Voldata/students/user1 failed sshd[7469]:pam_mount(pam_mount.c:123)clean system authtok (0)
Sep 17 11:15:07 sshd[7469]: pam_mount(misc.c:264) command: /usr/sbin/pmvarrun [-u] [user1] [-o] [1]
Sep 17 11:15:08 sshd[7473]: pam_mount(misc.c:341) set_myuid(pre): real uid/gid=0:605, effective uid/gid=0:605
Sep 17 11:15:08 sshd[7473]: pam_mount(misc.c:376) set_myuid(post): real uid/gid=0:605, effective uid/gid=0:605
Sep 17 11:15:08 sshd[7469]: pam_mount(pam_mount.c:360) pmvarrun says login count is 2
Sep 17 11:15:08 sshd[7469]: pam_mount(pam_mount.c:493)done opening session
Sep 17 11:15:12 sshd[7469]: pam_mount(pam_mount.c:535) received order to close things
Sep 17 11:15:12 sshd[7469]: pam_mount(pam_mount.c:536) real and effective user ID are 603 and 603.
Sep 17 11:15:12 sshd[7469]: pam_mount(misc.c:264) command: /usr/sbin/pmvarrun [-u] [user1] [-o] [-1]
```


Thanks in advance for any help on this!

---

### Post by drussell13 on 2008-09-17
Last update...I got it to work.... Whats interesting is everything was right...All I did was tweak my pam_mount.conf file and added the part "ipserver=10.x.x.x" and got rid of the "gid=&"....(I noticed in the logs it was complaining about there not being a group of my user) and after that it worked. Hopefully that will help someone that stumbles across this thread, I struggled with this for 2 days.  But thanks!

---

