---
title: "Jaunty: Do I need ~/.ICEauthority ?"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2009-05-08
Hi,
When trying to boot (after a regular shutdown) in my fully updated Kubuntu Jaunty, it failed to load kdm saying it couldn't access ~/.ICEauthority.

I opened a terminal and found that the above file was owned by root. Changing the ownership to my (regular) user solved the problem. The ONLY "exceptional" act during my former session (prior to boot) was to (successfully) install wine.

I've checked another PC with the same Kubuntu version and found that this computer booted fine WITHOUT having that file at all in ~.

Can somebody clarify:
1. Do I need this file or can I remove it?
2. If I need, what should be he permissions?

Thanks a lot upfront

Michael Badt

---

### Post by HyRax on 2009-05-08
[list=1]
[*]No, it's not required. Anything missing will be recreated by the application in question as though you were using that app for the first time.
[*]Anything in your /home directory should have the same basic permissions, and then it's up to you to change them to suit your own needs, ie: Owner has read, write and executable, Group has read and execute, and Other has no permissions at all, ie: drwxr-x--- is what your /home/jbloggs directory will be. Everything under it should inherit the same permissions.
[/list]

---

### Post by lovinglinux on 2009-05-08
> **HyRax said:**
> [*]Anything in your /home directory should have the same basic permissions, and then it's up to you to change them to suit your own needs, ie: Owner has read, write and executable, Group has read and execute, and Other has no permissions at all, ie: drwxr-x--- is what your /home/jbloggs directory will be. Everything under it should inherit the same permissions.
[/list]

When I create a new folder in home, the permissions are automatically set to drwxr-xr-x, so I assume is the default permission. Is there something wrong with my system?

---

### Post by HyRax on 2009-05-08
> **lovinglinux said:**
> When I create a new folder in home, the permissions are automatically set to drwxr-xr-x, so I assume is the default permission. Is there something wrong with my system?

Hard to say - you may have changed the settings without realising it, or installed something that changed it. You can change the directory alone back to what it should be with:

```

$ sudo chmod 750 /home/jbloggs

```

...or to recursively change everything in that directory in one hit:

```

$ sudo chmod -R 750 /home/jbloggs

```

...but double check that it's only files WITHIN your Home directory that are getting rwxr-xr-x because you may find that the /home/jbloggs directory itself is drwxr-x--- which means the difference in permissions within the directory are irrelevant because "Other" users won't be able to get that far anyway.

---

### Post by mibadt on 2009-05-08
Thanks all!

Michael Badt

---

