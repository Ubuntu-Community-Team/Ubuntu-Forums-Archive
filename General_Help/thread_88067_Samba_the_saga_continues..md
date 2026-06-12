---
title: "Samba the saga continues."
date: 2005-11-09
forum: General Help
---

### Post by _Lawless on 2005-11-09
I have two issues.
First one is I cant edit my Samba config file.
When I open it I'm not allowed to make any changes.
I tried to login with root but that is not allowed so I'm at a loss.
(Oh did I mention I'm a Linux noob who is having a blast learning this?)
Anyway, I can see my Ubuntu server on my XP machine, which leads us to issue numer two. The login screen pops up but no matter what user I set up on Linux, it will not accept the username/pw. I even tried root!
Any ideas for this noob that's just not ready to give up?!
This is my 8th distro I've played with in the last month as so far so good.


I finally got remote desktop working and now I can "play" from work...shhhh.
Only problem now is I did an update and screwed up my video settings...another story and probabally another thread down the line.

First things first. :)

---

### Post by kvidell on 2005-11-09
Hello, welcome to the forum :)

I think I can solve all of your problems, but it's been awhile since I played with Samba, so the second solution may be a bit off, you can always use "man" to clarify on my solution if it doesn't work straight off.

Firstly, there is no root account, which is why you couldn't use it.
What you want to do is use "sudo".
So, from a terminal, type:```
sudo gedit /etc/samba/smb.conf
```Replace "gedit" with whatever your favourite editor is.
When it asks you for a password, it's asking you for your user's password.

As for the second one, system users aren't the same as Samba users. So what you have to do is add them to the smb user roll...```
sudo smbpasswd -a username
```This will add your user to the samba access list, and ask you for a password.

That should be it!

Cheers,
- Kev

---

### Post by _Lawless on 2005-11-09
Fantastic!
Soon as get my video issue solved, so I can see what I'm doing using remote, I check it out.

thanks a million!

---

