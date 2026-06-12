---
title: "Local Update Server"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by afhkhan on 2009-10-27
Hi!

Is there a similar way of updating the Ubuntu desktops like we do with Windows Server Update Services (WSUS)? I have 40 machines that I need to install Ubuntu with and each machines downloads around 220 MB from the internet as part of updates and this throttles the bandwidth. Pls help.

afhkhan

---

### Post by elliotbeken on 2009-10-27
yes i believe there is a way you can set up a cache server. i cant remember what is was called or how you do it but some one must know to.

sorry i cant help ..

---

### Post by zvacet on 2009-10-27
[Here]("https://help.ubuntu.com/community/Apt-Cacher-Server")

---

### Post by shaggy999 on 2009-10-28
There are many ways to do this. You could run a completely full-fledged mirror using either apt-mirror or debmirror. This will sync a major subset of the repository (you pick release version, architecture type, and section such as "main", "restricted", "universe", and "multiverse").

I mirror all 4 sections of i386 and amd64 going back 4 releases and it takes up ~40G per release, so 160G total. I do this for a LUG group and drag the repos on a USB drive to installfests. Main reasons are everybody is different and want different software (ubuntu vs kubuntu vs ubuntu vs ubuntu server) as well as different extra software on top and some people want the LTS release while others want the bleeding edge while others want almost the bleeding edge... uh, it's easier to just bring the whole repos. :)

If you're using a lab then they're all pretty similarly configured so you're better off using a caching proxy that all the lab computers connect to. They request a package and if the proxy has a local copy it provides it. If not, it fetches it from the proper repo, hands it off and keeps the copy. I have not used this method, so I can't help you there.

---

