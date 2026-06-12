---
title: "Package manager problem"
date: 2008-09-08
forum: General Help
---

### Post by fifthwind on 2008-09-08
Hello,

I've got a problem when trying to use the package manager. Every time I try to use it, it says:

[COLOR="Navy"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR]

When I run the command above, I see that the package manager is stuck in an endless loop trying to download and install the fonts in the restricted extras. 

Is there a way to safely halt this process, so I can get in and use the package manager?

Thanks

---

### Post by indytim on 2008-09-08
Check you running process list in terminal mode:
```

$ ps aux

```

To kill a process:
```

$sudo kill -9 <process id #>

```

IndyTim

---

