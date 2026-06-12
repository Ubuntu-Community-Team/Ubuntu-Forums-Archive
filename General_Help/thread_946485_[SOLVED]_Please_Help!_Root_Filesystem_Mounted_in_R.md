---
title: "[SOLVED] Please Help! Root Filesystem Mounted in Read-Only Mode"
date: 2008-10-13
forum: General Help
---

### Post by Liv3dN8as on 2008-10-13
Ok, so I had some other issues with booting but I seem to found my way past those problems with a couple of posts on another thread(thanks). Now when I boot it runs fsck every time and then when it is done it says something like "fsck died with exit status 4" and "root filesystem mounted in read-only mode" and then a prompt.
What commands can I do to fix this? Any outputs needed? 

Please help! And Thanks in Advance!

---

### Post by Liv3dN8as on 2008-10-13
Ok, so I have fixed this after running fsck manually at the prompt it gave me. I could have sworn I tried this once with no luck. Obviously not.

Now I have a new problem. No Networking! I tried this
```
sudo /etc/init.d/networking restart
```

and I get this
```
sudo: must be setuid root
```

I followed some instuctions from this [post=5888774]Post[/post] and now I get
```
sudo: /etc/sudoers is owned by 1000, should be 0
```
I think I am missing something between by and 1000, but I didn't write it down. Sorry.

Please Help!

---

### Post by bodhi.zazen on 2008-10-13
boot to recovery mode -> command line

enter (you will already be root)

```
chown root.root /etc/sudoers
```

But it sounds as if your file system is corrupt. How did you run fsck ? Normally you should not run fsck on a mounted partition , you run it at boot before the partition is mounted or from a live CD.

---

### Post by Liv3dN8as on 2008-10-13
Thanks, that helped. But it still won't connect. And the only way I can get to the NetworkManager applet is to run this ```
sudo nm-applet
``` but it won't connect.

Oh, and actually before I could get the deamon to restart I had to go into /etc/network/interfaces and this is what I found:
```
Y"; description="Office Open XML Presentation Template with Macros Enabled"; na
```
I deleted it and then I got the deamon to run. I'm assuming it is malware? I don't know, never seen anything like it. Now it is still an empty file. Can I fix it?

---

### Post by Liv3dN8as on 2008-10-13
> **Liv3dN8as said:**
> Can I fix it? I did, I think. I entered this into the document```
auto lo
iface lo inet loopback
``` now when I try to run ifup -all, I get this ```
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

Thanks in advance!

---

### Post by cariboo on 2008-10-13
You could add the following lines to /etc/network/intrefaces:

```
auto eth0
iface eth0 inet dhcp
```

Then in a terminal type:

```
sudo dhclient eth0
```

Jim

---

### Post by Liv3dN8as on 2008-10-13
> **cariboo907 said:**
> You could add the following lines to /etc/network/intrefaces:

```
auto eth0
iface eth0 inet dhcp
```

Then in a terminal type:

```
sudo dhclient eth0
```

Jim 
Tried all that and now I get this ```
/lib/dhcp3-client/call-dhclient-script, ...): permission denied
```

---

### Post by Liv3dN8as on 2008-10-13
Any more suggestions? Please Help and Thanks in Advance!!!

My wife will be home soon and I will not be able to pay much attention to my puter.

I am going to mark this as solved because the original problem was solved.
Thanks everyone for your help.
I will post a new thread with my new problem.

---

