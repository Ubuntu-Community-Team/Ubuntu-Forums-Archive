---
title: "Shouldn't dist-upgrade change/update my sources.list?"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by Elchbulle on 2009-06-23
Hello all, I recently did a:

```
apt-get update
```

followed by a 

```
apt-get upgrade
```

then a 

```
apt-get dist-upgrade
```

I was previously on 8.10 and was thinking I was going to 9.04 (jaunty?)

The ugprades seemed to go fine, no noticeable errors, rebooted, and my /etc/apt/sources.list is still the same with everything pointing to intrepid...

How can I verify that I did in fact do a distribution upgrade and am now at 9.04?  When I re-run the commands they come back with 0 packages to update....

Thanks much!

---

### Post by decoherence on 2009-06-23
> **Elchbulle said:**
> Hello all, I recently did a:

```
apt-get update
```

followed by a 

```
apt-get upgrade
```

then a 

```
apt-get dist-upgrade
```

I was previously on 8.10 and was thinking I was going to 9.04 (jaunty?)

The ugprades seemed to go fine, no noticeable errors, rebooted, and my /etc/apt/sources.list is still the same with everything pointing to intrepid...

How can I verify that I did in fact do a distribution upgrade and am now at 9.04?  When I re-run the commands they come back with 0 packages to update....

Thanks much!

You change your /etc/apt/sources to point to Jaunty first, THEN you do the apt-get commands.

BUT you shouldn't use apt-get dist-upgrade. You should use Update Manager under System > Administration. I understand it does some extra things that dist-upgrade doesn't. Anyway, tell it to update and it should give you the option to upgrade to Jaunty.

ADD: oops, didn't realize this was a kubuntu thread. My instructions to use Update Manager may need to be modified, but I'm not a kubuntu user so I don't know how. In any case, use whatever graphical updater Ubuntu supplies rather than dist-upgrade.

---

### Post by Elchbulle on 2009-06-23
> **decoherence said:**
> You change your /etc/apt/sources to point to Jaunty first, THEN you do the apt-get commands.

BUT you shouldn't use apt-get dist-upgrade. You should use Update Manager under System > Administration. I understand it does some extra things that dist-upgrade doesn't. Anyway, tell it to update and it should give you the option to upgrade to Jaunty.

ADD: oops, didn't realize this was a kubuntu thread. My instructions to use Update Manager may need to be modified, but I'm not a kubuntu user so I don't know how. In any case, use whatever graphical updater Ubuntu supplies rather than dist-upgrade.


Ah, gotcha, thank you so much.  I will do it the graphical way =).

Thanks sir!

Tim

---

