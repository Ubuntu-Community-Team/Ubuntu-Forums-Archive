---
title: "Root password"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by dpj23 on 2009-10-30
My problem is I cannot set the root password... I able to go the user and groups, authenticate, and select properties and enter/change the password.  However it is not accepted when I'm prompted for it...

---

### Post by snowpine on 2009-10-30
There is no "root account" in Ubuntu... only your user account (by default). Use the commands "sudo" (command line) or "gksu" (for GUI apps) to temporarily gain root priviledges.

For example:

```
sudo apt-get update
```

---

### Post by pi4r0n on 2009-10-30
As default Ubuntu has no password set for the root user. To gain root access you have to type in your own user password. 

The manually set a password for the root user, type in the following in the shell:

> sudo passwd

After that you are asked to type in the new root password twice. 

Job done

Ta

pi4r0n

---

### Post by sisco311 on 2009-10-30
The root account password is locked in Ubuntu for a reason.

You can use sudo/gksu and policykit to escalate user privileges. 

See [uhelp]community/RootSudo[/uhelp] for more details.

---

### Post by SuperSonic4 on 2009-10-30
> **pi4r0n said:**
> As default Ubuntu has no password set for the root user. To gain root access you have to type in your own user password. 

The manually set a password for the root user, type in the following in the shell:



After that you are asked to type in the new root password twice. 

Job done

Ta

pi4r0n

ooh a pie

---

### Post by sisco311 on 2009-10-30
> **SuperSonic4 said:**
> I'd edit that out sharpish as it's against forum policy ;)

That's not true. 


[thread=716201]Forum policy on log-in-as-root tutorials[/thread]

> Tutorials explaining how to enable the root account **[COLOR="Red"]for a graphical login or autologin [/COLOR]**will not be supported on the forums and will be moved to the Jail.

---

### Post by aysiu on 2009-10-30
Read the forum policy on root login tutorials.

It'll explain how to do pretty much anything you think you need a root password for.

---

