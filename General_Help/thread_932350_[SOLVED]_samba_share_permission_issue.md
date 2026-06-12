---
title: "[SOLVED] samba share permission issue"
date: 2008-09-28
forum: General Help
---

### Post by tarun.winlin on 2008-09-28
I wanted to access a file on my Ubuntu box from my Windows laptop on my home network.
I installed samba.
I want to share my '/media/data1/Movies' folder. This is actually a partition which is formatted under NTFS (Ubuntu box is dual boot). Here is how I mount it using the /etc/fstab file

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
<snip>
#Data partition 1 - Local HDD 366GB Partition
UUID=F0542B64542B2D32 /media/data1 ntfs-3g rw,suid,dev,exec,noauto,nouser,async,dmask=027,fmask=137 0 0
<snip>

```

I mount it using 'mount /device/data1' & it mounts fine.

Here is how I created the share using the /etc/samba/smb.conf file
```

# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
<snip>
[Movies]
path = /media/data1/Movies
valid users = sambauser,tarun
read only = no
browsable = yes

```#

Also, I did the following commands:
```

'smbpasswd -a tarun'
'smbpasswd -a sambauser'

```

But when I open my laptop and enter the IP for my Ubuntu box, I get to a point where it asks for the username & password but does not accepts the one's I created, it says 'permission denied'.

I noticed something, when I change the /etc/fstab file to the following it starts working fine
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
<snip>
#Data partition 1 - Local HDD 366GB Partition
UUID=F0542B64542B2D32 /media/data1 ntfs-3g rw,suid,dev,exec,noauto,nouser,async 0 0
<snip>

```

Any idea why??

---

### Post by Jeroensum on 2008-09-28
The 'problem' is in the f(ile)mask and d(irectory)mask options. These options effectively mask out certain permissions. The same as umask does except these settings are effective for the whole filesystem.

Example file listing:
rwxrwxrwx  file1.txt 

When setting fmask to 077 you will deny the group and other settings to be used/read. The filesystem will see the permissions as: rwx------ (or 700), disallowing groupmembers and everyone else to use the file.

Also see the mount man page and this post:
[http://ubuntuforums.org/showthread.php?t=7702](http://ubuntuforums.org/showthread.php?t=7702)

In your case the mask completeley masks out 'other' thereby denying the sambadeamon to read the file.

---

### Post by Nepherte on 2008-09-28
Are the users 'sambauser' and 'tarun' part of the group that own the map /media/data1(/Movies)? If not, you should add them to it. You will also have to change the dmask and fmask permissions to dmask=007 and fmask=117 if you want to be able to write to it.

---

### Post by tarun.winlin on 2008-09-28
> **Nepherte said:**
> Are the users 'sambauser' and 'tarun' part of the group that own the map /media/data1(/Movies)? If not, you should add them to it. You will also have to change the dmask and fmask permissions to dmask=007 and fmask=117 if you want to be able to write to it.

Ok, makes sense, I changed my dmask=022,fmask=033

Directory
  R    G   O
4+2+1 4+1 4+1 = 7 5 5
dmask = 777-755 = 022

File
  R   G O
4+2+1 4 4  = 7 4 4 
fmask = 777-744 = 033

R: root
G: group
O: others

How can I verify 'sambauser' and 'tarun' part of the group that own the map '/media/data1'. I pasted the output of the file '/etc/fstab' file earlier.

What If I want a non-owner to access the file. I think I should be able to do that because I want only read access for which I have the fmask defined.

---

### Post by tarun.winlin on 2008-09-28
I think I found what the problem was. I added this to my IPTABLES rules..
/etc/iptables.rules

```

*filter

#  Allows all loopback (lo0) traffic and drop all traffic to 127/8 that doesn't use lo0
-A INPUT -i lo -j ACCEPT
-A INPUT -i ! lo -d 127.0.0.0/8 -j REJECT
<snip>
# Allow 192.168.1.102 to access SMB share on this box
-I INPUT -s 192.168.1.102 -p tcp --dport 139 -j ACCEPT
<snip>

```

And, that did it !! Sorry guys for bothering you !! Thanks for the help.

---

