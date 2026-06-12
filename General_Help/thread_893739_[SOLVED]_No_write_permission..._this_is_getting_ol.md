---
title: "[SOLVED] No write permission... this is getting old."
date: 2008-08-18
forum: General Help
---

### Post by zx6r1033 on 2008-08-18
Every time I try to install something, I get an error saying I don't have access, or I don't have write permission to do something. Today I was trying to install Return to Castle Wolfenstein, and it wouldn't let me install. It said I had no write permission. 

How do I make this crap stop?  I mean.. I love Ubuntu, but this is so incredibly old that I am just about ready to abandon it and go back to Window$.

---

### Post by HermanAB on 2008-08-18
Ubuntu configures the FIRST user as an administrator.  I'd guess that you added a new user account and is not using the original first user account anymore.

Read the sudo man page and change /etc/sudoers.

Cheers,

Herman

---

### Post by zx6r1033 on 2008-08-18
> **HermanAB said:**
> Ubuntu configures the FIRST user as an administrator.  I'd guess that you added a new user account and is not using the original first user account anymore.

Read the sudo man page and change /etc/sudoers.

Cheers,

Herman



actually, I am the only user set up on this computer. I could use sudo if I could figure out how to make the .x86.run program run from terminal, but it keeps saying "command not found" when I try it that way. 

I'm starting to get a bit discouraged by these types of things.

---

### Post by zx6r1033 on 2008-08-18
Nevermind... I figured it out. What a royal pain it is to get it to work, though. :(

---

### Post by arsenic23 on 2008-08-18
If you want to try to run it with sudo from the terminal.
Asuming the executable is '.x86.run' exactly, then you cd to the directory containing it and run it like this with sudo:

```
sudo ./.x86.run
```

---

### Post by zx6r1033 on 2008-08-18
> **arsenic23 said:**
> If you want to try to run it with sudo from the terminal.
Asuming the executable is '.x86.run' exactly, then you cd to the directory containing it and run it like this with sudo:

```
sudo ./.x86.run
```

Yep, that's how I got it to go.


Of course, now the game isn't playable. :(

---

