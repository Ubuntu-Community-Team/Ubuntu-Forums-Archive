---
title: "can't upgrade to new version of ubuntu (from 7.10)"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by T.lancer on 2009-05-31
hi there, I have a server that has been running on 7.10 gusty since it's release.  But now if I try to upgrade to 9.04 (from 7.10 to 8.04 to 8.10 etc.) it tells me that it can't find a valid mirror with the update manager. ("no valid mirror found")

Now I have discovered that the repros for 7.10 are dead, but I have added the old-releases repros.  I can do package updates but no distro updates.  a fresh install is prety much out of the question as the server has been to configuration hell and I don't want to go through that again.

so what steps must I take so that I can upgrade my server?

is there maybe a way I can upgrade with a CD copy of 8.04?

thanks

---

### Post by kruegger on 2009-05-31
My advice is that you update to Hardy 8.04, which is a LTS (Long Term Support version) and stay put until it dies by 2011. You'll have at least two years more of peace.;)

I dunno if u already tried to update via Update Manager...it is very tricky and buggy and I don't think it allows you to keep your server conf.
It had trouble to keep my GRUB configuration ( upgrade froze when it got to GRUB installation after 2 h.) which is quite simpler than a server conf.

I know what you mean when talking about a hell you don't want to go thru again. Well, in Ubuntu, from my experience, you better count on it.:lol:

Be brave, a fresh server installation can be that hard. Apache and Cherokee (some of which I presume you have) have a lot of support on the net.

I'm sorry I can't help you more precisely.

---

### Post by LinuxGuy1234 on 2009-05-31
You could backup /etc and /home and do a clean install. Then restore /etc and /home.

---

### Post by cman26 on 2009-05-31
Although I just downloaded Ubuntu for the first time myself, I agree with the above user. You should ust back everything up and re-install. Afterwards you can recover it and you will have ubuntu 9.04, which I am on right now, it is very good :p.

---

### Post by Sef on 2009-05-31
>  is there maybe a way I can upgrade with a CD copy of 8.04?Yes, there is with the [alternate cd]("https://help.ubuntu.com/community/Installation").

---

### Post by T.lancer on 2009-05-31
Surprisingly I have managed to get rid of that problem, but no I'm suffering the following problem:

After selecting the upgrade in the update manager, it checks all the files and stuff.  Then it gives me this error:

> could not calculate the upgrade
A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

Naturally I guess it's one of those problems, the first 2 seem unlikely, and so it might be the unofficial software.
Where do I need to look in synaptic package manager to find any unofficial packages?

---

### Post by T.lancer on 2009-05-31
once again thanks to a bit of googleing, I found 2 local apps that did not belong to any repository.

but I still get the same error.

could it be because of the fact that the official repositories are now dead, it can't check for dependancies?  and since the upgrade dissables the 3rd party repositories it wouldn't check the old-releases repositories.

if that's the case how can I fool the upgrade in thinking the old-releases repositories are in fact official ones?

---

### Post by T.lancer on 2009-06-02
anyone?

---

