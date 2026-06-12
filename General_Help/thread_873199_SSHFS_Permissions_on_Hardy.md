---
title: "SSHFS Permissions on Hardy"
date: 2008-07-28
forum: General Help
---

### Post by stealth17 on 2008-07-28
I am trying to mount a SSHFS on my fresh Hardy install but the files and folders are owned by 10006:10006 but even when I run ```
sudo chown stealth17:stealth17 sshfs/
``` it won't let me change the permissions. My user is in the fuse usergroup as well.

What am I doing wrong?

---

### Post by ktrnka on 2008-07-28
```
sshfs username@host:/share /mount/point -o allow_other
```

-o option allows other users access.

Also edit /etc/fuse.conf remove the # infront of user_allow_other

---

### Post by stealth17 on 2008-07-28
> **ktrnka said:**
> ```
sshfs username@host:/share /mount/point -o allow_other
```-o option allows other users access.

Also edit /etc/fuse.conf remove the # infront of user_allow_other

Didn't seem to help, is there a way to change the file ownership some how?

---

### Post by ktrnka on 2008-07-28
What error are you getting?

---

### Post by ktrnka on 2008-07-28
If you view the man page of sshfs, I see another option for -o

-o uid=N
   sets file owner

---

### Post by stealth17 on 2008-07-28
> **ktrnka said:**
> What error are you getting?

When I try to save a file in gEdit that resides on the sshfs, it says

> [SIZE=2]**Could not save the file /media/sshfs/themes/promo/style.css.**[/SIZE]

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by stealth17 on 2008-07-28
> **ktrnka said:**
> If you view the man page of sshfs, I see another option for -o

-o uid=N
   sets file owner

That fixed it, thanks!

---

### Post by ktrnka on 2008-07-28
Nice!

---

### Post by wigren on 2008-08-01
I'm having trouble understanding the uid=N option. I set it as [email]username@remotehost.com[/email]:/home/usershome /media/Website -o uid=michael (my user name) but that doesn't work, I get: fuse: invalid parameter in option `uid=michael' I get the same thing when I try it with -o uid=wkidfm (the remote user name). I've been at it for a few hours and I'm getting frustrated, so I hope I'm not missing something obvious. I've also tried the -o allow_other option. But I got the same error stealth17, You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again. Thanks.

---

### Post by Dr Small on 2008-08-01
wigren, your uid is not your username, but a number. In the terminal, run:
```
id
```

To find your uid and gid.
Please see this post, of an example of where I was having problems:
[http://ubuntuforums.org/showpost.php?p=5424634&postcount=2](http://ubuntuforums.org/showpost.php?p=5424634&postcount=2)


Dr Small

---

### Post by wigren on 2008-08-01
Dr Small, you're my hero! I used [email]username@remotehost.com[/email]:/home/usershome /media/Website -o uid=1000 and it worked like a charm. This may not be the appropriate post for this question, but I noticed in the link you posted that you've set an alias for all that. Problem is My aliases go away when I reboot. Is there a way to save them?

---

### Post by Dr Small on 2008-08-01
> **wigren said:**
> Dr Small, you're my hero! I used [email]username@remotehost.com[/email]:/home/usershome /media/Website -o uid=1000 and it worked like a charm. This may not be the appropriate post for this question, but I noticed in the link you posted that you've set an alias for all that. Problem is My aliases go away when I reboot. Is there a way to save them?
Sure. save you aliases in ~/.bash_aliases
Then, in ~/.bashrc, uncomment these lines:
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

Save the file, add all the aliases you want to your .bash_aliases file and close the terminal. When you open it again, the aliases should work ;)

Dr Small

---

### Post by wigren on 2008-08-01
Dr Small, again thank you. It all works perfect now.

---

### Post by SabreWolfy on 2008-10-28
> **ktrnka said:**
> ```
sshfs username@host:/share /mount/point -o allow_other
```

-o option allows other users access.

Also edit /etc/fuse.conf remove the # infront of user_allow_other

Don't see a little "medal" icon next to this post to say thanks, so I'll just post this instead. Thanks! :-) Getting a string of question marks for permissions on the mounted filesystem was driving me crazy.

---

