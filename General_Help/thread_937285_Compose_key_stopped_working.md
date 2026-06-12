---
title: "Compose key stopped working"
date: 2008-10-03
forum: General Help
---

### Post by 0x656b694d on 2008-10-03
Hi,

I had Compose key working until installed scim (accidentally) and than removed it.

All settings are kept the same as before. How do i get my Compose key back??

I had ```

 Option         "XkbOptions" "compose:ralt,grp:alt_shift_toggle,grp_led:scroll"
```
line in my xorg.conf file, with no luck. Then i ran dexconf and got almost empty xorg.conf with no keyboard settings in it. The same result.

I have evdev-managed keyboard model with two layouts: USA Int. (AltGr dead keys) and Russian.

I 

What can i do?

Thanks!

-Mike

---

### Post by 0x656b694d on 2008-10-04
Okay, i fixed the problem.

I reset the symbolic link (it pointed to scim-bridge):

 /etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/default-xim

---

### Post by rabbit251 on 2008-11-11
Mike, can you be a bit more specific? Where do I find the symbolic link you're talking about? I'm on Hardy. (Which thread do you wanna continue this conversation on, haha.)

---

### Post by 0x656b694d on 2008-11-11
rabbit251, just say
```
$ ls -la /etc/alternatives/xinput-all_ALL
```
Where does it point to?
In my case it was a symbolic link that pointed to something with 'scim' in its name (default-scim perhaps). So i did something like:
```
$ sudo rm /etc/alternatives/xinput-all_ALL
$ sudo ln -s /etc/X11/xinit/xinput.d/default-xim /etc/alternatives/xinput-all_ALL
```

hope this will help!

---

### Post by rabbit251 on 2008-11-11
Thanks, Mike. I followed your instructions, and I think they had a positive impact, though it's hard to tell because I was changing too many things at once. (One note though: before making your recommended edit, the symbolic link on my system read,

/etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/default,

with "scim" nowhere present.)


I finally got my special characters working again after switching to US-international keyboard layout, but not without some quirks. I can only use the default AltGr as my dead key, as manually selecting another compose key or third-level chooser in the layout options has no effect. Moreover, AltGr is only responding as a third-level chooser, not as a compose key.

---

