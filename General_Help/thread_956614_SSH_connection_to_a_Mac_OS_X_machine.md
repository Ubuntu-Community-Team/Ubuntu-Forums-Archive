---
title: "SSH connection to a Mac OS X machine"
date: 2008-10-23
forum: General Help
---

### Post by Jugney on 2008-10-23
Hi all,

I need to connect via SSH to a Mac OS 10.4 computer remotely. Under 7.10 I had this working with the following command:

```
ssh -L 5901:localhost:5901 [Mac username]@[IP address of the Mac]
```

I recently tried doing this again (after upgrading to 8.04) and it no longer works. Where I get stuck as it the password stage. It says: 

```
$ ssh -l 5901:localhost:5901 [user]@[IP address]
[user]@[IP address]'s password: 
Permission denied, please try again.
[user]@[IP address]'s password: 
Permission denied, please try again.
[user]@[IP address]'s password: 
Permission denied (publickey,password).
```

I cleared out the known_hosts file, and spent over an hour and a half looking online for solutions to this. Even after tinkering with ssh_config and sshd_config, I'm still getting the same message.

On the Mac, I've opened port 5901 for SSH and have the private IP (of the Mac itself) set correctly. When behind the same router, I'm able to login just fine using the Mac's private IP.

Can anyone help?

Jugney

EDIT: All of my testing has actually been done trying to login remotely while behind the same router (i.e. connecting using the external IP even though we're on the same network during testing. Would this have any impact?)

---

### Post by Jugney on 2008-10-23
I just noticed something that may be significant. When I logged in successfully using the local IP, I noticed the password prompt simply said

```
Password: 
```

This is how it looked in the past when I was able to login remotely as well.

Currently, when I try to log in remotely the password prompt looks like this:
```

[User]@[External IP]'s password: 
```

And this is the screen that always says Permission denied.

Hmmm.....

---

### Post by mschutte on 2008-10-23
Just to clarify something on the code you posted. I notice that there is a capital -L option and the second shows lowercase -l. Maybe an oversight?

---

### Post by Jugney on 2008-10-23
Oops. Yeah, I've tried it both ways with the same result.

---

### Post by Nepherte on 2008-10-23
If you simply want to login with ssh:
```
ssh -l username host ## -l is the username option
ssh username@host    ## without the -l option, but it does the same

```

If you want to create a tunnel over ssh:
```
ssh -L port:host:port username@host ##or with -l of course
```

---

### Post by Jugney on 2008-10-23
None of that is currently working for me.

All I want to do is be able to access and work on files remotely. I used to use SSH to tunnel a VNC connection so I could remote desktop. But at this point I just need file access. Is there a cleaner way to do that?

---

### Post by Nepherte on 2008-10-23
What intrigues me is
```
[user]@[IP address]'s password: 
Permission denied (publickey,password)
```
Are you using a public/private key pair? Does the server expect one?

---

### Post by mschutte on 2008-10-23
Agree with Nepherte, for straightforward file access a simple ssh username@host will suffice.

---

### Post by Jugney on 2008-10-23
I'm not sure. How do I tell?

---

### Post by mschutte on 2008-10-23
When you use a public/private key pair with ssh, you normally create a pair using the ssh-keygen command. Did you create such a key pair?

---

### Post by Jugney on 2008-10-23
To be honest, I followed instructions given online to set up the initial SSH connection 6 months ago, and I don't remember if I did this or not.

---

### Post by Jugney on 2008-10-23
Hmmm, I thought I replied but it didn't come through. Anyway, it has been 6 months since I set up the initial connection and I don't remember all the steps I went through. Is there a way to check? Or to start over fresh?

I uninstalled and reinstalled all the openssh packages, and cleared out the known_hosts file, if that makes a difference.

Jugney

---

### Post by Seq on 2008-10-23
> **Jugney said:**
> Hmmm, I thought I replied but it didn't come through. Anyway, it has been 6 months since I set up the initial connection and I don't remember all the steps I went through. Is there a way to check? Or to start over fresh?

I uninstalled and reinstalled all the openssh packages, and cleared out the known_hosts file, if that makes a difference.

Jugney

Check to see if you have any id* files:

```
ls ~/.ssh/id*
```

---

### Post by Jugney on 2008-10-23
I checked, and nothing came up.

---

### Post by Jugney on 2008-10-24
Any more ideas?

---

