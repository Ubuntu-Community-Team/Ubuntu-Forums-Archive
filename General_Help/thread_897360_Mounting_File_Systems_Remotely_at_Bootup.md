---
title: "Mounting File Systems Remotely at Bootup?"
date: 2008-08-22
forum: General Help
---

### Post by rickdane on 2008-08-22
I am planning out my Ubuntu machine for Amazon Web Servics EC2, basically I am using the new EBS which essentially amounts to mounting a filesystem remotely. The way I want to run things is as follows:

- Machine boots up using the absolute minimum filesystem
- Script is automatically run that than mounts the other file systems remotely
- Any other steps that would normally have occurred during bootup will then occur

I have never done anything like this before so I would appreciate any advice on how to approach this. Essentially I am trying to insert this mounting script into the system bootup process but I am not sure how to do this.

---

### Post by negge on 2008-08-22
What do you mean by a remote filesystem? Is it remote like in on another computer on your network or remote like in somewhere on the Internet? If it's the latter it can be quite difficult...

---

### Post by rickdane on 2008-08-22
It is remote like another computer on my network (through Amazon EBS), I already know how to script the actual mounting of the drives, the issue is where to put this script within the bootup process and how to place it there.. I haven't ever deal with something this early in the machine boot before.. thanks

---

### Post by abcuser on 2008-08-22
check this thread: [http://ubuntuforums.org/showthread.php?t=896474](http://ubuntuforums.org/showthread.php?t=896474)

---

### Post by rickdane on 2008-08-22
Thanks for the link, however it does not address my issue specifically.. to further clarify what I am trying to do.. I would like to mount the various parts of the filesystem such as /etc, /bin, /lib, /var.. remotely over what amounts to a local network, I am wondering where in the boot process can I specify this.

---

### Post by ilrudie on 2008-08-22
In Ubuntu starting services at boot time is handled by rc scripts that live int /etc/init.d and are linked into /etc/rc[number].d.  Anything that starts with Sxx where the S is capitalized and xx is a number runs at startup.

---

### Post by rickdane on 2008-08-23
Is /sbin/init running at all during bootup then? I had gathered from other sources (not ubuntu specific) that this was the first script to run upon boot-up

---

