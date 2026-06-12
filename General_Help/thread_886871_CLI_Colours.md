---
title: "CLI Colours?"
date: 2008-08-11
forum: General Help
---

### Post by dgcarter on 2008-08-11
Silly question, but you know in the Fedora and openSuSE distros, the CLI can be quite colourful, i.e. your username is in red, folders are highlited with green etc...

Is there an easy way to enable that in ubuntu?

Thanks

---

### Post by LowSky on 2008-08-11
I know Terminal can be changed to anything you like. It can even have its own wallpaper. But for an actual command line idk.

---

### Post by Vivaldi Gloria on 2008-08-11
> **dgcarter said:**
> Silly question, but you know in the Fedora and openSuSE distros, the CLI can be quite colourful, i.e. your username is in red, folders are highlited with green etc...

Is there an easy way to enable that in ubuntu?

Thanks

Uncomment colour lines in ~/.bashrc (i.e. delete #).

---

### Post by pauper on 2008-08-11
Read ~/.bashrc thoroughly, make changes.

```
dircolors -p
man bash
```

An example:

```
export PS1='${debian_chroot:+($debian_chroot)}\[\033[00;32m\]\u@\h\[\033[00m\]:\w\[\033[00m\]\$ '
```

[edit:]

The aforementioned variable will make USERNAME and HOSTNAME of green color.

Read "man bash"

/PROMPTING

And put this into /root/.bashrc
```
export PS1='${debian_chroot:+($debian_chroot)}\[\033[00;31m\]\u@\h\[\033[00m\]:\w\[\033[00m\]\$ '
```

Now, any time you become root--USERNAME and HOSTNAME are red.

---

