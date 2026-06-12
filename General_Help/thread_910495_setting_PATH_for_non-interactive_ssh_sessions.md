---
title: "setting PATH for non-interactive ssh sessions"
date: 2008-09-04
forum: General Help
---

### Post by slaguth on 2008-09-04
Hi,

I'm trying to add an ~/bin to my PATH on a remote server running Linux (I don't know exactly what flavor). After reading the bash manual, I modified ~/.bash_profile to add ~/bin to my path.

$ ssh username@server.net
username@server:~$ echo $PATH
/home/username/bin:/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games:/custom/sys/sbcl/sbcl/bin

Which works perfectly fine. The problem is that when I try to use darcs push over ssh, it can't find darcs on the remote machine because bash doesn't read ~/.bash_profile for non-interactive logins.

$ ssh username@server.net 'echo $PATH'
/usr/local/bin:/bin:/usr/bin:/usr/X11R6/bin

I believe it may be possible to affect PATH unconditionally for all logins, but all the methods I am aware of require modifying a system file like /etc/..., none of which I have write access for (and even if I did, wouldn't want to change).

I've also heard that ssh can be configured with a custom path by modifying ~/.ssh/environment, but I believe this requires setting "PermitUserEnvironment yes" in /etc/ssh/sshd_config, which I also don't have access to.

Are there any other ways to configure a user-specific PATH for non-interactive ssh sessions? Or do I need to go to system admins with this problem?

Thanks in advance.

---

### Post by bingoUV on 2008-09-04
Maybe you already know these things, but

1. You do not necessarily need the PATH variable. You could call your program by giving the full path : ~/bin/programname

2. You could call a particular program with a modified env. Try
```

ssh username@server.net 'export PATH=/home/username/bin:"$PATH" ; echo $PATH'

```

---

### Post by slaguth on 2008-09-07
Thanks for the response.

Unfortunately, according to the manual entry for darcs push, "the command invoked via ssh is always [FONT="Courier New"]darcs[/FONT], i.e. the darcs executable must be in the default path on the remote machine."

So I guess my question is what options are (theoretically) available for changing  the PATH for non-interactive logins via ssh? As I mentioned before, I may not have the necessary access to try some methods, but I would still be open to any suggestions.

If there aren't any other options, I should probably redirect the question to the darcs community... I just thought I could be forgetting something.

Thanks again.

---

