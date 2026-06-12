---
title: "Not able to pass a variable from grub to shell environment"
date: 2008-07-25
forum: General Help
---

### Post by elox on 2008-07-25
Hey,

I'm trying to pass a variable (in my case X_DRIVER) from grub to the shell, so I can use it in a script.

```
/vmlinuz-2.6.24-16-generic root=UUID=11266bc9-5c89-41be-a60f-8580b4e98e85 ro quiet splash X_DRIVER=dock
```

I also tried "set X_DRIVER=dock" or export "X_DRIVER=dock".

From my time as a Gentoo user I remember, that you have to allow a variable to pass through to the env.

In Gentoo its: 

```
echo X_DRIVER >> /etc/conf.d/env_whitelist

```

But I can't find a similar mechanism in Ubuntu.

I hope someone can give me a hint, how to solve this.

--
Michael

p.s. Sorry for my bumpy English

---

