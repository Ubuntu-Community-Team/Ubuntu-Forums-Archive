---
title: "Setting ulimit -n for non root"
date: 2008-09-02
forum: General Help
---

### Post by shareme on 2008-09-02
I can set root limits for ulimit -n just fine its the nonroot user that I need set,

limits.conf lines have no effect on the on-root user account.

Am I missing something how PAM and the limits.conf and sysctl.conf interact?

The idea is to have non-rrot limits of open files higher so that can run and IDE like Eclipse as 1024 is too low.

Thanks

---

### Post by aloshbennett on 2008-09-02
Maybe you missed to add
> session required pam_limits.so
to /etc/pam.d/common-session

---

### Post by shareme on 2008-09-02
no it was added to common-session and login and su

it does apply the root  nofile lines n limits.conf just not o the non-root

---

### Post by shareme on 2008-09-02
I think I have it solved now..

I was able to execute these commands and get correct results:

$cat /proc/sys/fs/file-nr

lsof | wc -l

Thus problem solved

---

### Post by abdusamed on 2010-10-16
Can you please help me... I need to change my ulimit in ubuntu 10.04.1 After reboot, and countless changes nothing seem to change my ulimit.

My username is 'bahie' with the name of 'Abdusamed'. The account type is 'admistrator' not 'Desktop User' 

Below is the edited file can you please check it and if it requires any changes?

```

#/etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

bahie            hard    nofile          8192
* hard nofile 51200
#End of file


```

---

