---
title: "Please help - can I reverse CHMOD error"
date: 2008-07-23
forum: General Help
---

### Post by andyase on 2008-07-23
Hi all
I have just attempted to chmod a dir on my server and have totally locked myself out.

Its a remote server, ssh gives access denied, same with root ftp.

Heres what I did (aarrrgghh) went to the dir, I wanted to change permissions on all files in dir. Used Sudo -R 664 /  ... erm I did not realise the / was a big mistake, I thought it would do everything forward of the dir I was in...

Can anyone help...please.

Regards
Andy

---

### Post by ookamisan on 2008-07-23
I have no idea how to solve the problem, but when you chmod directories, you should keep the "executable bit", so better would have been 755 (directories must be executable to access them)

---

### Post by danwood76 on 2008-07-23
I doubt even if you had a hold of the server infront of you you could undo that.
You should obviously know what you're doing when you run commands as root.

You will have to reinstall linux on the system (after data recovery of course) theres no other way to repair it unless you want to spend days hunting through a similar install to make sure all the permissions are corrected.

---

### Post by sdennie on 2008-07-23
To get back to the cause of the problem, you should have run:

```

chmod -R 664 .

```

With "-R" the "." means "starting from right here" whereas "/" means "everywhere".

If it's any consolation, destroying an installation with chmod -R is a common mistake but, generally you only make the mistake once.

---

### Post by ookamisan on 2008-07-23
Maybe you could try something like ```
chmod -R u+x pathtoyourroot/
```
if you can boot a live cd or something (if it is a real root server, some providers might put a cd for you into  the drive (how else to install a server, eh?)) and then you migth run the command. I won't promise that it might work, don't want to try out ;)
It is supposed to change all the rights of the owner to executable and keep the other rights. Maybe you can consult the manpage of chmod for further ideas.

---

### Post by danwood76 on 2008-07-23
The system still wont like it.
If you open up the privileges on a system completely the system will not boot.
Certain files need restriced permissions otherwise they get ignored.

I would doubt that your 'server' is a standalone server it is probably a virtual server in which case the provider may have a backup he can just load to solve your issues.

---

### Post by forger on 2008-07-23
I also suggest to reinstall the server's operating system or ask the support to restore a backup if available..:(

---

### Post by andyase on 2008-07-23
Hi 
Thanks for the replies so far.

It is a dedicated server... if that helps.

Andy

---

### Post by Keith Hedger on 2008-08-03
This wont be of help now but I have done similar things so I created a small app to record/repair permissions so checkout: [http://code.google.com/p/perms/](http://code.google.com/p/perms/) for future use.

---

