---
title: "Gnome power Manager no battery tab."
date: 2010-05-07
forum: Hardware
---

### Post by BrockStrongo on 2010-05-07
Hi All,
    I've had a hard time getting gnome power manager to recognize that a battery is present. If I run acpi, the battery discharge time shows up, but no options are present in gnome power manager to change any battery actions. (when to suspend, shutdown et.)
    If I run sudo gnome-power-manager the battery options are present.

So, 1) is there a way to change the permissions that gnome power manager runs under?
2) is there a way to kill gnome power manager? ( it doesn't show in top)

I know this is a long post, but any help would be greatly appreciated.
Thanks

---

### Post by BrockStrongo on 2010-05-09
I still can't figure out how to get gpm to run with root privileges. I tried to install kpowersave (as this worked as an alternative in the past) but it depends on hal. I'm wondering if this problem is related to the removal of hal? 
Anybody else run into this.
Anybody else ready to move back to karmic or jaunty?

---

### Post by BrockStrongo on 2010-05-09
Seems like a similar problem. Thanks for taking a look. I will try adding sudo before the gpm command, but, won't it require a password? I tried adding a custom start up process called root power with the command sudo gnome-power-manager and nothing happened at startup. I think maybe I need to change the order in which things start. Move gpm toward the end, after acpi.
Thoughts?

---

### Post by BrockStrongo on 2010-05-17
What happened to the replys?

---

### Post by BrockStrongo on 2010-05-18
I've been able to use gconf-editor as a workaround.

---

### Post by Ilias83 on 2010-10-28
I had the same problem with gnome-power-manager.
I could not make "on battery" tab appear.
So I installed xfce4-power-manager and now I have this as my default power manager.

---

### Post by graham73may on 2011-01-24
Hi, could you please explain how you used gconf-editor to resolve this? What did you edit? thanks

Thank you for this topic, I did not know that sudo-gnome-power-management worked... this is also the only way I can get it to show up. It is even more annoying now that I know it works (when it wants to).

---

### Post by denova on 2011-09-24
I just solved this problem by running "gnome-power-preferences" (user privileges). Battery tab shows and options work.

---

