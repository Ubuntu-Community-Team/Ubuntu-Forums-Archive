---
title: "Post-installation issue with KPPP on Intrepid AMD64"
date: 2008-11-09
forum: General Help
---

### Post by schlauf on 2008-11-09
Hi everybody,
as the thread title suggests, I've been running Intrepid for some days now on an x86_64 arch. Since Kubuntu 8.10 AMD64 is not equipped with KPPP any more (and since I need to run this program), I downloaded the appropriate package from packages.ubuntu.com and installed it via dpkg --install, since I was unable to get any internet access beforehand.
After installation, KPPP would complain about a missing /etc/resolv.conf which it was expecting to exist, even an empty file would do fine. Fine, I "touched" it in the designated folder, however, when running KPPP for the next time it would show up a kdesudo windows first, asking for my password again.
Since I never needed to enter my password in former Kubuntu versions, I'm curious how to turn it off again. KPPP works like a charm after entering my password, but I'm a lazy guy and don't wanna do this several times a day without a good reason.
So is there any advice how to proceed? Any help will be greatly appreciated!
schlauf

---

### Post by editrix on 2008-11-10
Just guessing, but do you have a kppp folder in /home/your_user_name/.kde/share/apps/ ?

If not, maybe just create one? You might have to copy the Rules directory from /usr/share/apps/kppp and change the permissions on it.

---

### Post by schlauf on 2008-11-10
Thanks for your reply.

The folder /home/{user}/.kde/share/apps/kppp exists. There is an (empty) folder Rules inside, which is owned by {user} {user_group}.

Unfortunately, there is no folder like /usr/share/apps/kppp ... so there's nothing to copy from either :(

---

### Post by editrix on 2008-11-10
> **schlauf said:**
> Unfortunately, there is no folder like /usr/share/apps/kppp ... so there's nothing to copy from either :(

Well, that's most peculiar, because there should be one. Unless they've made some drastic changes in Intrepid (I'm on Hardy).

I suspect the lack of this folder is at the root (sorry for the pun) of your problem.

The only thing I can suggest is, now that you have some kind of dialup access, to reinstall kppp from the repositories--force it if you have to.

And thanks for the heads up about it not being included in Intrepid. Yet another reason for me not to switch.

---

### Post by schlauf on 2008-11-12
I took the latest version available from the repository ... so I don't get it what a reinstall should resolve ...

Well, basically KPPP wouldn't be necessary any more since KNetworkmanager deals with the majority of PPP-issues since 0.7 ... however, specific use cases such as mine still exist and depend on a KPPP installation :(

---

