---
title: "Can't sudo or login as root"
date: 2005-12-01
forum: General Help
---

### Post by Edit on 2005-12-01
Evening all,

This is kind of embarassing, but I was  changing the permissions of files with chmod and got sick of having to do it every 10 minutes and ran a: 

```
sudo chmod -R ugo=rwx /
```

so I'd never have to worry about file permissions ever again... turns out that's not how it works.

The next time I went to sudo something it said:

```
sudo: must be setuid root
```

and when I try and login as root, it gives me: 

```
su: Authentication failure
```

I've been googling for the past 20 minutes and found that I need to change the permissions of /usr/bin/sudo, and /usr/bin/sh to something a little less than wide open, but whenever I try it, I get this:

```

chmod: changing permissions of `/usr/bin/sudo': Operation not permitted
chmod: changing permissions of `/bin/sh': Operation not permitted

```

Any help/suggestions would be much appreciated :D

-Edit

---

### Post by akiro.yamamoto on 2005-12-01
What are the current permissions of those files....
Use Nautilus...
If all else fails... boot with a linux live cd, any will work(Ubuntu would be best) and change the permissions using su or root or sudo from that on the hard drive files....
Hope that helps or at least gives you some new ideas to solve the problem...
Regards...

---

### Post by gruepig on 2005-12-01
Time for a reinstall. It's probably not what you want to hear, but that's what you need to do.

(Booting from CD will allow you to change the permissions on those files, but it's not just sudo, sh, sudoers, etc. that you're going to have to change. If you've overwritten setuid information, quite a few things won't work.  And even if you could get a working system, you *really*  shouldn't run a system with such open permissions; the default permissions are there for good reason.  You could probably find some way to grab the correct permissions from another system and chmod all your files to match, but that would be quite a trick.)

---

### Post by Edit on 2005-12-01
Thanks for the replies.

I tried booting off my Live CD and managed to get sudo going again, but root was still rooted.  And yeah, you're right, gruepig, along with a lot of other stuff (e.g., networking was totally screwed).

I've reinstalled and am going to get it to a point where I'm happy with it (when I've got my LAMP configuration up and running again, etc) and take a ghost image of the install.

That way, if I decide to do something irreversible it wont be the end of the world (or my install).  

Thanks again for your help.

-Edit

---

### Post by NLFSoftware on 2005-12-05
Hello all

Well I new on Ubuntu and for the first time I working whit Linux in a professional use.

I have the same problem and I solved makeing the next steps:

1º in the console mode change to root user
2º enter the comand chmod 755 /usr/bin

this change all the permisions for the default. For my works just fine I hope hat can save some reinstalings for someone too
:razz: 

Be cool

---

### Post by Paloseco on 2005-12-05
sudo xterm and then passwd

---

### Post by newuser111 on 2005-12-05
read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by BLTicklemonster on 2006-09-05
I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.

---

