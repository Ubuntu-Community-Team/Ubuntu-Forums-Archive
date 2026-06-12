---
title: "KDM not loading/wireless doesn't work after upgrade"
date: 2008-10-24
forum: General Help
---

### Post by mma8x on 2008-10-24
i accidently upgraded to ibex (thought i was just upgrading hardy packages); now kdm initially boots and i get an error message "no greeter widget plugin loaded, check the configuration", at which point i'm dumped to a shell.  haven't been able to find similar problems from other users.  i'm not at home and need amarok for my wedding in 2 days, so any help greatly appreciated...

---

### Post by Yellow Pasque on 2008-10-24
I would report this as a bug on Launchpad. One possible way to work around it would be to install gdm and use that as your login manager (just select KDE4 as your session).

---

### Post by mma8x on 2008-10-24
yeah, i didn't have gdm installed, and was having network issues (don't know if it's related to the upgrade--killing network manager seems to have solved it for now).  i realized that i had put the the intrepid sources in the repos in order to get the new kernel to see if that solved my suspend issues (it didn't) and forgot to take them out.  then when i thought i was upgrading hardy, it of course upgraded to intrepid.  and afaik there's no easy way to downgrade, right?

---

### Post by Yellow Pasque on 2008-10-24
No, downgrading would require a reinstall. Is there any more specific info in the kdm log?
```
cat /var/log/kdm.log | more
```

---

