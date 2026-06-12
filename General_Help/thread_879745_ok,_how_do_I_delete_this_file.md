---
title: "ok, how do I delete this file?"
date: 2008-08-04
forum: General Help
---

### Post by Zafrusteria on 2008-08-04
I have a file that looks a little corrupt :-) any ideas how to delete it?

```

$ ls -la
ls: cannot access objects: Permission denied
total 0
drwxrwxrwx 3 root root  72 2008-08-04 13:34 .
drwxrwxrwx 3 root root 112 2008-08-04 14:18 ..
?????????? ? ?    ?      ?                ? objects
```

I have tried as root to 
```

sudo rm objects 
sudo chmod 777 objects 
sudo chown root:root objects
```

I just get an error message saying
```

rm: cannot access objects: Permission denied
chmod: cannot access objects: Permission denied
```

I also created an root shell and tried from there. I didn't expect it to work and was right.

It was in /usr/lib/vmware/messages/binary directory and stopped vmare from running as it needed to write something to the file. I got around this my moving the vmware directory somewhere else on the same file system. Then with recursion turned on copied it back.  All but the corrupt file went back, after a bit of messing around :-) So I am up and running again. Almost forgot the FS is reiserfs over a 3 disk raid 5 array with lvm over the top of that just for good measure.

But this is now bugging me :confused:

Thought someone out there might like to solve this puzzle. Fdisk, format etc does not count as an answer!!!

---

### Post by tamoneya on 2008-08-04
what about ```
sudo ls -la
```

---

### Post by Zafrusteria on 2008-08-04
The problem is root does not have permission to do anythingto the filke either :-)

```
$ sudo ls -la
ls: cannot access objects: Permission denied
total 0
drwxrwxrwx 3 root root  72 2008-08-04 13:34 .
drwxrwxrwx 3 root root 112 2008-08-04 14:18 ..
?????????? ? ?    ?      ?                ? objects
```

---

### Post by tamoneya on 2008-08-04
okay well thats pretty interesting.  Why dont you pop in the liveCD and mount the drive and then rm it from there.

---

### Post by Zafrusteria on 2008-08-04
I hadn't thought of that. Now, I just need to figure out how to mount the RAID5 and LVM parts from the live CD or a system rescue disk. :-)

---

### Post by tamoneya on 2008-08-04
is it a hardware or software raid?

---

### Post by Zafrusteria on 2008-08-04
it is software raid. I configured it when as I did the last complete install with the ALT install CD.

---

### Post by tamoneya on 2008-08-04
okay thats pretty similar to my setup.  I just use the scan option in mdadm.  It auto detects my RAID 5 config and lets me mount /dev/md0.  This is in the 8.04 liveCD.

---

### Post by bingoUV on 2008-08-04
Anything in dmesg after "ls -la" ?

---

### Post by Zafrusteria on 2008-08-05
nope :) nothing gets added to the the output of dmesg.

---

