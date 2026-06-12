---
title: "dad has done the worst - disrupted update installation"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by ollie232 on 2009-05-21
Hi all,
a little explanation, my dad was using the Dell mini9 ubuntu, he decided to download & install the system updates needed whilst running off the battery...   dad, fell asleep and the mini9 ran out of power during installation. !  
this has obviously caused many problems, we can log in but many programs/ and wireless networking does not work or appear to be running.

How do we get out of this mess?

this is the spec page of the actual computer.
[http://www1.euro.dell.com/content/products/productdetails.aspx/laptop-inspiron-9?c=uk&cs=ukdhs1](http://www1.euro.dell.com/content/products/productdetails.aspx/laptop-inspiron-9?c=uk&cs=ukdhs1)

Many Regards
Ollie

---

### Post by drs305 on 2009-05-21
You don't have wireless, but can you still connect to the internet via wired? If so, try running:
```
sudo apt-get install -f
```
That will try to fix any dependency problems. Then run:
```

sudo apt-get update && sudo apt-get upgrade

```
and tell us what error messages you are getting.

---

### Post by ollie232 on 2009-05-21
e: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


(do i need to hard wire to router?)

Regards

---

### Post by drs305 on 2009-05-21
```
sudo dkpg --configure -a
```

---

### Post by ollie232 on 2009-05-21
we've tried, it's asking for super user privileges, but we don't no what they are?

---

### Post by drs305 on 2009-05-21
> **ollie232 said:**
> we've tried, it's asking for super user privileges, but we don't no what they are?

The "sudo" part of the last command I gave is giving you the 'superuser' privileges. You enter your password - you won't see it as you type but that's a security feature. Type your PW and just press ENTER.

When you what to run something as root, you preface the command with "sudo" for terminal commands or "gksudo" for any graphical app that will be opened. It will ask for the password, which is when you enter the first user on the machine's password (or any user with admin rights).

---

### Post by ollie232 on 2009-05-21
sorry yes -it's actually running now ! 

what happens next?     What is it actually doing?

regards

---

### Post by solitaire on 2009-05-21
It should be sorting out all the installs that went bad when the power failed.

Once it's finished run:
```
sudo apt-get update && sudo apt-get upgrade
```
That will finish all the remaining updates. (make sure it's plugged in to the power socket!) lol

---

### Post by drs305 on 2009-05-21
> **ollie232 said:**
> sorry yes -it's actually running now ! 

what happens next?     What is it actually doing?

regards

If you are referring to the "dpkg --configure -a" command:
> --configure package...|-a|--pending
Reconfigure  an  unpacked  package.  If -a or --pending is given instead of package, all unpacked but unconfigured packages are      configured.


You get this info by typing "man dpkg" in a terminal. Each command has one of these. They are referred to as the "man" pages. So if you want to know what a command does or what options or format the command uses, you simply type "man <command>" in a terminal. So you can type "man apt-get" to see what the *update* and *upgrade* options do.
Examples:  man cp,   man dpkg, man apt-get

---

### Post by ollie232 on 2009-05-21
> **drs305 said:**
> You don't have wireless, but can you still connect to the internet via wired? If so, try running:
```
sudo apt-get install -f
```
That will try to fix any dependency problems. Then run:
```

sudo apt-get update && sudo apt-get upgrade

```
and tell us what error messages you are getting.

after get update.
many failed to fetch http errors after update all of which conclude with could not resolves dell-mini.archive.canonical.com

---

### Post by lykwydchykyn on 2009-05-21
> **ollie232 said:**
> after get update.
many failed to fetch http errors after update all of which conclude with could not resolves dell-mini.archive.canonical.com

Is the wireless working at this point?  You won't be able to do the remainder of the update if it's not connected, naturally.

I'm not familiar with the mini9, I assume it has a wired ethernet port?  You may need to utilize that to finish out the update process.

---

### Post by ollie232 on 2009-05-21
Hi   its only fixed !   thanks for all your help.

---

