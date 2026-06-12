---
title: "[SOLVED] Permission Problem at start up"
date: 2008-10-21
forum: General Help
---

### Post by RJWEcology on 2008-10-21
I'm still getting the same permissions error when I login during startup. 

[http://i472.photobucket.com/albums/rr83/RJWEcology/DSC01395.jpg](http://i472.photobucket.com/albums/rr83/RJWEcology/DSC01395.jpg)

I've tried this:

```
chown -R username:username $HOME

```
to change the attributes to 644 on the file:
Code:

```
chmod 644 $HOME/.dmrc

```

But during the first code, I get this error:

```
rich@Obsidian:~$ chown -R rich:rich $HOME
chown: changing ownership of `/home/rich/.gvfs': Function not implemented
```

What am I doing wrong? Any help would be much appreciated. 

Rich

---

### Post by ajgreeny on 2008-10-21
I think you may need the full pathway to the folder so try 
```
chmod 644 /home/username/.dmrc
```

---

### Post by RJWEcology on 2008-10-21
I'll try that, but what about the first code?

---

### Post by ajgreeny on 2008-10-21
What do you mean by "the first code"?

---

### Post by drs305 on 2008-10-21
You have to run the code with sudo, since it requires root privileges:
```
sudo chown -R rich:rich $HOME

```

---

### Post by RJWEcology on 2008-10-22
This is what I get now:

```
rich@Obsidian:~$ sudo chown -R rich:rich $HOME
[sudo] password for rich: 
chown: cannot access `/home/rich/.gvfs': Permission denied
rich@Obsidian:~$
``` 

Sorry to be a bother but what next?

---

### Post by RJWEcology on 2008-10-22
Bump :)

---

### Post by drs305 on 2008-10-22
> **RJWEcology said:**
> This is what I get now:

```
rich@Obsidian:~$ sudo chown -R rich:rich $HOME
[sudo] password for rich: 
chown: cannot access `/home/rich/.gvfs': Permission denied
rich@Obsidian:~$
``` 

Sorry to be a bother but what next?

It's no bother. Ask until you get it corrected.

You don't really need to run the command with the -R switch. The -R switch is recursive, meaning it is trying to extend the command to all subfolders and files. Try running it as:
```
sudo chown rich:rich /home/rich
chmod 644 /home/nick/.dmrc

```

That should make the necessary changes to eliminate the $HOME error message. Just for your education, you don't need the 'sudo' for the second command since you now 'own' the .dmrc file and can do it without any other permission. If for some reason it doesn't work, run these commands:
```
sudo chown rich:rich /home/rich/.dmrc
chmod 644 /home/nick/.dmrc

```

---

### Post by RJWEcology on 2008-10-23
Thanks for the help but when I tried a restart, the error message still came back? I noticed when I tried "sudo chown rich:rich /home/rich" I wasn't asked for my password?

---

### Post by geirha on 2008-10-23
The warning chown gives on .gvfs is completely harmless. The command worked fine.

sudo remembers the password for about 15 minutes, so if you run something with sudo and type a password, and then run something else shortly after, you don't need to retype the password.

The error message gdm gives you also says that your homedir must not be writable to others. What's the permissions? ```
ls -ld $HOME
```

---

### Post by RJWEcology on 2008-10-23
This is what I got:

```
rich@Obsidian:~$ ls -ld $HOME
drwxrwxrwx 67 rich rich 4096 2008-10-23 11:30 /home/rich
```

---

### Post by geirha on 2008-10-23
Right, it's writable to everyone. That's the problem then.  Change it to one of 
```
chmod 755 $HOME # The default. You have full access, everyone else get read access
chmod 700 $HOME # You have full access, everyone else have no access.

```

---

### Post by RJWEcology on 2008-10-23
Thats it! Perfect! Thanks to everyone who helped :)

---

