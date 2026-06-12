---
title: "Terminal"
date: 2008-10-02
forum: General Help
---

### Post by 4-PackDad on 2008-10-02
Hey;

Newbie Stuck Again.........

When I try to run commands in Terminal
I'm usually prompted for my password.

Now it's not asking for a password.....

My login 'does' have Admin rights.
but
It doesn't seem to set automatically when I first login to a session.
example
When I look at "Users and Groups"
I never had to "Authenticate" my access before with my password.
Now I have to enter my password.

Did something change with an update...?

So,
How can I run commands in Terminal Now...?

Thnx

---

### Post by Ryadt on 2008-10-02
Use sudo before your command.

---

### Post by Idefix82 on 2008-10-02
To run commands which require root privileges you need to type
```
sudo command
```
if it is just a command in the terminal. If you want to open a GUI program with root privileges, e.g. if you want to modify a system file with gedit, you need the command gksudo:
```
gksudo gedit filename
```
or
```
gksudo gimp picture.jpg
```
and so on.

This mechanism stops viruses and other bad software doing anything important on your computer without you authorising it.

---

### Post by jerome1232 on 2008-10-02
As for why they might not have asked for your password sometimes sudo does have a 15 minute timeout, so if you 'sudo' one task, you can do other admin tasks without re-entering your password for 15 minutes.

---

### Post by 4-PackDad on 2008-10-02
Thanks Guys...

Keep forgetting about "***sudo***"

Had a brain lasp back to 1980 to my early DOS days... Fortran... Cobol... 
even Basic which I loved.

Thanks again...

---

