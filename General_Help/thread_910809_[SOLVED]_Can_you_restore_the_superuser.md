---
title: "[SOLVED] Can you restore the superuser?"
date: 2008-09-04
forum: General Help
---

### Post by JaxsonTheDog on 2008-09-04
So I accidentally took the superuser out of the administrators group, and now I can't execute any sudo commands.

Is there any way to restore the superuser permissions, or am I headed for reinstalland?

Thanks.

---

### Post by iaculallad on 2008-09-04
> **JaxsonTheDog said:**
> So I accidentally took the superuser out of the administrators group, and now I can't execute any sudo commands.

Is there any way to restore the superuser permissions, or am I headed for reinstalland?

Thanks.

On your terminal, to add a user to the admin group:

```
sudo useradd -G admin your_username
```

or you could paste your:

```
sudo cat /etc/sudoers
```

---

### Post by mb_webguy on 2008-09-04
That might be a bit difficult for him, iaculallad, considering the bit about "now I can't execute any sudo commands".

;)

---

### Post by drs305 on 2008-09-04
If you can't use the *sudo* command in a normal session, reboot to a root prompt in 'Recovery' mode.

If you are no longer in the *admin* group (more likely):
```
adduser [COLOR="DarkRed"]**yourusername**[/COLOR] admin
```

If, as you stated, root no longer belongs to admin (less likely):
```
adduser [COLOR="DarkRed"]**root**[/COLOR] admin
```

---

### Post by iaculallad on 2008-09-04
> **mb_webguy said:**
> That might be a bit difficult for him, iaculallad, considering the bit about "now I can't execute any sudo commands".

;)

Yes, OP could disregard the **sudo** on my post and try booting on recovery mode. My mistake.

---

### Post by JaxsonTheDog on 2008-09-07
> **iaculallad said:**
> Yes, OP could disregard the **sudo** on my post and try booting on recovery mode. My mistake.

Okay, I didn't love having to find and install a keyboard and monitor (since the box is headless) but your suggestions about using recovery mode worked great.

Thanks for the help.

Jax

---

