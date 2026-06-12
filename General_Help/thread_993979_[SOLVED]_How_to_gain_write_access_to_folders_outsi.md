---
title: "[SOLVED] How to gain write access to folders outside the home directory."
date: 2008-11-26
forum: General Help
---

### Post by JasonDFR on 2008-11-26
Hello,

I am using Linux for the first time.

I would like to know how to save files to folders outside of the home directory. Specificly, I would like to save files to the www directory, but I am receiving a message that says:

"Check that you have write access to this file or that enough disk space is available."

There is enough disk space, thus I must not have write access.

I am attempting to transition my work from a windows machine where I was using WAMPy to a Ubuntu machine. I think I am going to love using Linux for dev, but I have hit a roadblock with "write access."

Thanks in advance!

Jason

---

### Post by kanikilu on 2008-11-26
Are you the only user that needs write access to that folder? If so, the easiest thing to do would be to chown the www directory to you and give you write access:

```
sudo chown -R yourUserName www
sudo chmod -R 755 www
```

---

### Post by blazemore on 2008-11-26
Take ownership of the folder:
```
sudo chown -R foo /bar
sudo chmod -R 755 /bar
```
Gives ownership of /bar and all subdirectories to the user foo.

---

### Post by JasonDFR on 2008-11-26
Great! I'm on my way to learning how to use Linux.

Are there any other ways to do the same thing? Anything I should be aware of?

Thanks for the quick help! This forum is very very good.

Jason

---

