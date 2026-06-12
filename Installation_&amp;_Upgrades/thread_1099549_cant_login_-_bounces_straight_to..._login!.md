---
title: "cant login - bounces straight to... login!"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by Mujaheiden on 2009-03-18
i don't know what happened, but I cant login anymore to my box.

I was fiddling with my cups drivers for printing, when they failed to work, so i decided to reboot, and after that i cant get into the whole system for a few hours already.

Each time i login, i don't get a password error, but i get a quick black screen (changing resolution?) after which im being returned to the general login screen.

If, on the other hand, i try a wrong login, i get the wrong username reply, so im not crazy.

i did boot with the step by step mode, and the root only terminal, and after some googling, i managed to get my internet working, to perfor an apt-get update -f and apt-get install, but all requirements were already satisfied.

this looks similar to [http://ubuntuforums.org/showthread.php?t=1076605](http://ubuntuforums.org/showthread.php?t=1076605) although i just have plain 8.10 ubuntu.

if i CTRL-F2 to other screens - when i have the straight login screen, i also cant login, after accepting my login, the cursor moves one position down to again ask for my username - without error notice.

WHATS UP????

---

### Post by lykwydchykyn on 2009-03-18
Did you check the space left on your drives when you were at the root prompt?  Sometimes this can happen if a partition fills up.

boot to the root prompt and check 
```

df -h

```

If the root partition is full, you can usually clear out some space with apt-get clean.  If the home partition is full, you'll need to clean out some of your files.  Deleting ~/.thumbnails often clears a lot of space harmlessly.

If it's not that, check out the contents of ~/.xsession-errors, /var/log/auth.log, and /var/log/syslog.

---

### Post by vijaym on 2009-03-18
I have just had the same problem. was trying to get my printer to work, fiddling with cups and now it does the same as the OP
have checked the partitions and there is more than enough space

any ideas?

---

### Post by Mujaheiden on 2009-03-18
thanks for your quick response. i checked it and got lots of gigs left.

i could start my apapche, so i was able to get the logs from my client (attach), but they dont tell me a lot ...

---

### Post by Mujaheiden on 2009-03-18
okay, ive just removed cupsys and hpijs, but no avail

---

### Post by lykwydchykyn on 2009-03-18
Can't remember if you said you tried this, but have to tried just loggin in as root and resetting your user's password?
```

passwd username

```

I'm checking out the log files now.

---

### Post by Mujaheiden on 2009-03-18
its dont get a password error, so i dont think thats needed

---

### Post by Mujaheiden on 2009-03-18
wow! if i do passwd myusername, i get a segmentation fault! but i can still continue in the root terminal
passwd root does work, without errors.

---

### Post by Mujaheiden on 2009-03-18
than ks for putting me on the password trail! Theres something i dont understand with cups and the passwords, see [here]("http://ubuntuforums.org/showpost.php?p=6641615&postcount=13").

So I did ```
apt-get remove libpam-smbpass
``` from my root terminal and im back!

btw im removing my systemlogs, because i think posting them could be a security hazard

---

### Post by lykwydchykyn on 2009-03-18
Ok, don't post this file, but check to make sure /etc/shadow exists, and that it's ls -lh output looks something like this (dates will be different):
```

-rw-r----- 1 root shadow 1.4K 2008-12-23 09:32 /etc/shadow

```
Next, make sure root is the only UID 0.  This command should return a single line starting with "root":
```

cat /etc/passwd |grep ":0:"

```

Can you recall what you did configuring cups?  any config files you might have edited?

EDIT: Cool!  glad to see you're fixed.  Yes, remove the syslogs.  I don't think there should be anything terribly worrisome in them since you're using private IPs, but it never hurts to be cautious.

---

### Post by vijaym on 2009-03-18
good stuff. 

sudo apt-get remove libpam-smbpass

worked for me as well.

---

### Post by Mujaheiden on 2009-03-19
only problem for me now is that samba users cant access my system anymore, and sudo smbpasswd -a mujaheiden gives a

```
tdb(/var/lib/samba/secrets.tdb): transaction_read: failed at off=540702821 len=24
tdb(/var/lib/samba/secrets.tdb): transaction_read: failed at off=540702821 len=24
tdb(/var/lib/samba/secrets.tdb): transaction_read: failed at off=540702821 len=24
tdb(/var/lib/samba/secrets.tdb): transaction_read: failed at off=540702821 len=24
tdb(/var/lib/samba/secrets.tdb): transaction_read: failed at off=1650750572 len=24
pdb_generate_sam_sid: Failed to store generated machine SID.
PANIC (pid 32258): could not generate a machine SID
BACKTRACE: 6 stack frames:
 #0 smbpasswd(log_stack_trace+0x2d) [0xb7f7118c]
 #1 smbpasswd(smb_panic+0x80) [0xb7f712e9]
 #2 smbpasswd(get_global_sam_sid+0x6f3) [0xb7f12417]
 #3 smbpasswd(main+0x645) [0xb7ee24e0]
 #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b77685]
 #5 smbpasswd [0xb7ee19d1]
smb_panic(): calling panic action [/usr/share/samba/panic-action 32258]
smb_panic(): action returned status 0
Segmentation fault
```

I guess thats the missing libpam-smbpass

so im going to try to remove the cups thing, because that secondary.... grmbl...

AH: I located the exact problem, so instead of removing the libpam-smbpass

this should suffice; sudo rm /var/lib/samba/secrets.tdb

(See [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/303458/comments/13]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/303458/comments/13"))

---

### Post by mnord00 on 2009-03-30
I had the same problem. It started when I replaced the Network card in my Lexmark printer. Nothing would print so I deleted the printer in Cups and then added it back in. When I rebooted I got the same issue as you. I followed the solution at the above post and it worked. I rebooted into repair mode, Choose Drop to root and at the command typed; rm /var/lib/samba/secrets.tdb  I was able to log in with no more problems at this writing. (I haven't tried printing to my Lexmark yet)

---

### Post by snipehunter on 2009-08-25
I recently had the cannot login problem. Only I had made the problem worse by having set my menu.lst file to a 0 second timeout.  Basically, I couldn't get to recovery mode.  I solved the problem through the use of a live cd.

This bug report really helped. 
[https://lists.ubuntu.com/archives/ubuntu-server-bugs/2009-March/011217.html](https://lists.ubuntu.com/archives/ubuntu-server-bugs/2009-March/011217.html)

After commenting out the appropriate line, I was able to login and my cups/samba still work.  Not sure about what that line does, but I am back on line.

---

