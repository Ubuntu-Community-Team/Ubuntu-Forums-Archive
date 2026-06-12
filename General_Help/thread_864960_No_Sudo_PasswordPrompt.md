---
title: "No Sudo Password/Prompt"
date: 2008-07-20
forum: General Help
---

### Post by JoshHendo on 2008-07-20
Hi Everyone,

I am looking for a way to have it so that when a command is run as Sudo, it doesn't prompt for a password. I am thinking either there needs to be a way to turn it off, or make it so there is no password (but it may still prompt).

Security of the machine is NOT an issue. It is a media center that I have built, and I need a few scripts to run as root when I login. I am planning to do this using the sessions manager, though now I think of it maybe there is a way to run scripts as root upon login with out a sudo password.

Basically, I want it to mount a network share, and link to it in the relevant files in the home folder so Elisa can connect to them, and I have set it up so elisa will start automatically on the TV screen.

If there is any way to do this easily, possibly using no sudo prompt, or any other way, that would be great.

Thanks, Josh.

---

### Post by RealPSL on 2008-07-20
Actually the answer to this is in most sudoers files. It is generally not considered secure to let "ALL" commands be run without a password so I will show you how to run one.

First you will need to edit the sudoers file with 

```
sudo visudo
```

Add the line

```
my_user_name ALL=(ALL) NOPASSWD: /bin/cat
```

This will allow my_user_name to run the /bin/cat command with sudo without prompting for a password. Please make sure that the files that you choose to do this with are secure and owned by root without write access to anyone else.

---

