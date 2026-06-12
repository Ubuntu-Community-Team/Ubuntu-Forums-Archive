---
title: "Newbie: Add/Remove not working"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by exkend on 2009-01-17
Hello,
 I've just installed Ubuntu 8.10 and within hours I've already come up against a brick wall. I installed some games via Add/Remove: gunroar and nexuiz. After trying them out I tried to remove them again using Add/Remove however I get this error message:
 Changes applied
 
Not all changes and updates succeeded. For further details of the failure, please expand the 'terminal' panel below.

Details: 
  dpkg: unable to stat triggers deferred file `/var/lib/dpkg/triggers/Unicorp`: S tale NFS file handle

I have tried using Synaptic to remove them or anything and I still get denied.

Any help resolving this would be gratefully received

Exkend

---

### Post by kranny on 2009-01-17
Close any apt and dpkg open process and recheck it by using
```
sudo ps -A | grep dpkg
sudo ps -A | grep atp
```
If any result is shown
sudo kill -9 pid# of process
Delete the package from /var/cache/apt/archives than delete the unicorp
```
sudo rm /var/lib/dpkg/triggers/Unicorp
```
and rename the new unicorp
```
sudo mv /var/lib/dpkg/triggers/Unicorp.new /var/lib/dpkg/triggers/Unicorp
```

---

### Post by exkend on 2009-01-18
Thanks for the reply. Unfortunately when I try the second step I get this response:

 rm: cannot remove `/var/lib/dpkg/triggers/Unicorp': No such file or directory
jay@ubuntu:~$ 

Not sure what to do or why this is occuring, anyway thanks again for the assistance.

Exkend

---

### Post by kranny on 2009-01-18
If that doesn't solve your problem try this:
```

$ cd /var/lib/dpkg/
$ sudo mv status status.broken
$ sudo cp status-old status
$ sudo apt-get update
```

---

### Post by exkend on 2009-01-18
Thanks, I tried it and now get this: bash: $: command not found

Anyway I appreciate the help.

---

