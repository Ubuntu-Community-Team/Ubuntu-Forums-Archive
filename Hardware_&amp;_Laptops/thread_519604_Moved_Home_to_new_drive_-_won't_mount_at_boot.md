---
title: "Moved Home to new drive - won't mount at boot"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by SoggyCornflake on 2007-08-07
I was running out of room on my hard drive, so I added a second one and moved my /home directory to the new drive.

The new drive works, I am using it now.

However, every time the pc is rebooted, or cold booted, the home drive is not mounted.    I can [ctrl][alt][f1] ,  mount it manually, and we're off and running again. but  if my wife or kid were to turn on the computer, they probably are stuck until I can fix it.

Here is the relevant portion of my /etc/fstab file:
```
/dev/sdb1 /home etx3 defaults,errors=remount-ro 0 1
```Any ideas where to go from here?

---

### Post by jnorthr on 2007-08-07
just seems funny to me as your command shows 
/dev/sdb1 /home [COLOR="Red"]etx3[/COLOR] defaults,errors=remount-ro 0 1
and all the time i thought the ubuntu disks were formatted as [COLOR="red"]ext3[/COLOR] - well guess i learn something everyday. :KS

---

### Post by pbcartwright on 2007-08-07
my home in /etc/fstab looks like this:
/dev/sda7            /home                ext3       defaults              1 2

---

### Post by jnorthr on 2007-08-07
not sure about the 'defaults' choice, we need to find out if the 'default' setting provides automount or no automount. Let's google this.

---

### Post by SoggyCornflake on 2007-08-07
> **jnorthr said:**
> just seems funny to me as your command shows 
/dev/sdb1 /home [COLOR="Red"]etx3[/COLOR] defaults,errors=remount-ro 0 1
and all the time i thought the ubuntu disks were formatted as [COLOR="red"]ext3[/COLOR] - well guess i learn something everyday. :KS

Seems you caught me in a dyslexic moment.  When I get home I'll fix that.   Thanks.  Nothing like having somebody look over your shoulder to find something wrong.

---

### Post by SoggyCornflake on 2007-08-08
> **jnorthr said:**
> not sure about the 'defaults' choice, we need to find out if the 'default' setting provides automount or no automount. Let's google this.

According to this [page]("http://www.tuxfiles.org/linuxhelp/fstab.html"), it appears that defaults means auto mount which is what I found to be the case after fixed the above noted typo.

---

