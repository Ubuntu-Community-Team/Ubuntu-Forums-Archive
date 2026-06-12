---
title: "SSH times out?"
date: 2008-07-14
forum: General Help
---

### Post by lmarr28 on 2008-07-14
I'm trying to do a low-level disk image from my iPhone (using MobileTerminal) to my Ubuntu Gutsy system over SSH.  I found a blurb on someone's blog saying that you can run the following command from the iPhone to do this:

```
root@my-iphone> dd if=/dev/disk0 | ssh username@mydesktop 'dd of=iphone-dump.img'
```

However when I execute the command, the iPhone's Terminal app sits idle for about a minute, then comes back with a message saying Connection Refused, Timed Out, etc.  I'm guessing that my Ubuntu system is blocking the SSH port (22), since I can successfully ping my iPhone from Ubuntu and vice versa, but I don't know how to tell...  Can you guys offer any suggestions?  I'm still very new to Linux/Unix, so please excuse my ignorance!

Thanks!

---

### Post by Vivaldi Gloria on 2008-07-14
> **lmarr28 said:**
> I'm trying to do a low-level disk image from my iPhone (using MobileTerminal) to my Ubuntu Gutsy system over SSH.  I found a blurb on someone's blog saying that you can run the following command from the iPhone to do this:

```
root@my-iphone> dd if=/dev/disk0 | ssh username@mydesktop 'dd of=iphone-dump.img'
```

However when I execute the command, the iPhone's Terminal app sits idle for about a minute, then comes back with a message saying Connection Refused, Timed Out, etc.  I'm guessing that my Ubuntu system is blocking the SSH port (22), since I can successfully ping my iPhone from Ubuntu and vice versa, but I don't know how to tell...  Can you guys offer any suggestions?  I'm still very new to Linux/Unix, so please excuse my ignorance!

Thanks!

To begin with, can you do

```
ssh username@mydesktop
```

at all?

Is ssh server installed & configured on your ubuntu box?

---

### Post by lmarr28 on 2008-07-14
I'll have to give that a try when I get home.

I did install OpenSSH, but I haven't done any config yet.  Actually, I was just reading another article on how to do just that.  I'm going to try all of this when I get home and I'll let you know how it works.

Thanks for the quick reply!

---

### Post by Vivaldi Gloria on 2008-07-14
> **lmarr28 said:**
> I'll have to give that a try when I get home.

I did install OpenSSH, but I haven't done any config yet.  Actually, I was just reading another article on how to do just that.  I'm going to try all of this when I get home and I'll let you know how it works.

Thanks for the quick reply!

Make sure that you install openssh-server. You can check that it is successfully installed by sshing itself by:

```
ssh localhost
```

---

### Post by lmarr28 on 2008-07-14
OK, "ssh localhost" worked, but I still can't connect with the iPhone using "ssh username@mydesktop".  The error I get (on the iPhone) is:

ssh: connect to host <*mydesktop*> port 22: Operation timed out

[EDIT:]
For what it's worth, I know SSH is running on the iPhone, since I have no problem SSH-ing to it from my Windows box.

---

### Post by Vivaldi Gloria on 2008-07-14
openssh-server (sshd) keeps its settings in

```
/etc/ssh/sshd_config
```

Now the default settings only allow connections from computers in you lan. You have to change settings so that connections from outside adresses are also allowed. To begin with, read

```
man sshd_config
```

in a terminal to have an idea. Then press ALT+F2 and start

```
gksudo gedit /etc/ssh/sshd_config
```

to edit sshd_config. Find the lines which contain "ListenAddress" in them. Add to the line under them:

```
ListenAddress *
```

to enable all adresses. While you are editing I also suggest you change the default port 22 to something else, for example 22332. Change the line which has "port" in it to

```
Port 22332
```

Lot of script kiddies attack port 22 and changing port will keep your logs simple. 

In the sshd_config file the lines which start with # are commented out. So don't put a # sign in front of the lines you write.

You should also forward port 22332 in your router (or 22, whichever you are using) to your ubuntu computer. Ask if you don't know how to do.

Anyway, after all this you should be able to connect from the phone by using the command

```
ssh -p 22332 user@your_ubuntu's_ip_number
```

The "-p number" means use that numbered port.

---

### Post by lmarr28 on 2008-07-14
Thanks for all of the info!

Actually, I just managed to get it working!  In the command: "ssh username@mydesktop", I replaced <mydesktop> (the computer name) with the actual IP address of my desktop.  I thought that I could use the computer name, since I could ping it with no problems, but I guess SSH can't resolve that host name for some reason.  Oh well.  I'm still going to go through and follow your steps.  Better safe than sorry.

Thanks again!  You've been a bigger help than you know!

---

### Post by Vivaldi Gloria on 2008-07-14
> **lmarr28 said:**
> Thanks for all of the info!

Actually, I just managed to get it working!  In the command: "ssh username@mydesktop", I replaced <mydesktop> (the computer name) with the actual IP address of my desktop.  I thought that I could use the computer name, since I could ping it with no problems, but I guess SSH can't resolve that host name for some reason.  Oh well.  I'm still going to go through and follow your steps.  Better safe than sorry.

Thanks again!  You've been a bigger help than you know!

You're welcome mate. Take care.

---

