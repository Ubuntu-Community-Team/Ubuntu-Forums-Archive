---
title: "the &quot;right way&quot; to do file permissions?"
date: 2008-08-20
forum: General Help
---

### Post by akahige on 2008-08-20
I just upgraded to the -19 kernel from the repos (along with the usual blizzard of other updates) and have been experiencing weird issues. For whatever reason, when I decided to drop back to the -18 kernel (which was rock solid for months of uptime) I got the following error:

> “User’s $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User’s $HOME directory must be owned by user and not writable by other users.”

Thanks to [a post here](http://fingersnaps.wordpress.com/2008/07/18/homedmrc-file-is-being-ignored-ubuntu-permission-got-messed-up/), from someone who apparently suffered the exact same issue, I was at least able to get back into my desktop. However -- and I've run into this in the past -- when the suggested fix is to chmod -R 755 your home directory, it very subtly messes with all kinds of things, like making all my text files executable, or jacking with code that needs to be compiled.

So I'm wondering... is there a "right way" or a "better way" to deal with these chmod issues?

---

### Post by LUS93 on 2008-08-20
Execute the chmod commands only on the problem files? Bulk chmod/chown is almost never the right answer. It's like driving a tac with a sledge hammer.

Recursively setting $HOME 755 on a multi-user box isn't a great idea.

---

### Post by Nepherte on 2008-08-20
The somewhat default permissons of a directory is 0755 and 0644 of a file.
[list]
[*]For a directory, this gives you total rights for the owner of the directory, read + execute rights for everyone else.
[*]For a file, it gives you read and write rights for the owner, read rights for all the rest.
[/list]
This is not always the case, some information sensitive files require stricter permissions.

To change permissions in a terminal:
```

chmod xxxx <filename|directory>
```
where xxxx is the four digit permissions number.

In your case you just have to do this:
```
chmod 0644 ~/.dmrc
```

---

### Post by akahige on 2008-08-20
Thanks for the replies.


> **Nepherte said:**
> The somewhat default permissons of a directory is 0755 and 0644 of a file.
[list]
[*]For a directory, this gives you total rights for the owner of the directory, read + execute rights for everyone else.
[*]For a file, it gives you read and write rights for the owner, read rights for all the rest.
[/list]
This is not always the case, some information sensitive files require stricter permissions.

By default, you mean that generically speaking those are the permissions that get most files are created with, right?

Would you think that going back and changing things to 644 is better than leaving things at 755?



[QUOTE=Nepherte]
To change permissions in a terminal:
```

chmod xxxx <filename|directory>
```
where xxxx is the four digit permissions number.

In your case you just have to do this:
```
chmod 0644 ~/.dmrc
```[/QUOTE]

This may be an obvious question, but what does the ~/ do (or signify)?

---

### Post by Liv3dN8as on 2008-08-20
I too have been having this problem for over two weeks off and on. It is starting to get really annoying. I have tried everything everybody has suggested and I just don't know what to do. I really don't want to do an install. Please help!

---

### Post by Denestria on 2008-08-21
> This may be an obvious question, but what does the ~/ do (or signify)?

It means your home directory as in  /home/akahige/.dmrc

---

### Post by pauper on 2008-08-21
> **akahige said:**
> This may be an obvious question, but what does the ~/ do (or signify)?

Here tilda expands to the path to home directory of the current user (= "echo
$HOME"). For regular non-privileged user default setting is /home/$LOGNAME.
For root user with its own environment--/root directory.

Read "man bash". Search for /Tilde Expansion.

---

### Post by amitkher on 2008-08-21
"chmod -R 755 your home directory" is generally a bad suggestion. The right way is never touch default permissions unless necessary. When necessary, just change the permissions of the files that are directly affected e.g. $HOME/.dmrc file in your case.

A blind chmod might make many things to stop work properly. Some files (e.g. ~/.ssh/authorized_keys) expect to have a specific permission (600 in this case) and they don't work otherwise. Unless you want to write a research paper on permissions of Ubuntu files, just let the default file permissions the way they are.

---

