---
title: "update-manager dapper to hardy alternate cd"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by fingau on 2008-12-05
Hello all.

I wish to upgrade from "dapper" 6.06.2 LTS to "hardy" 8.04.1 LTS. The recommended method is a network upgrade using "update-manager". I have dial-up internet access only with 6-hour sessions. Over the last month I have downloaded and burned the alternate cd. My question is can "update-manager" recognize the alternate cd as a package source. That way I hope most of the packages will be retrieved from the cd and not from a network source.

Has anybody done an upgrade this way.  Is it possible?

fingau.

---

### Post by Partyboi2 on 2008-12-05
You should be able to stick the alternate cd in the cdrom and a box should pop up asking if you want to upgrade. If no box appears then press Alt+F2 and enter
```
gksu "sh /cdrom/cdromupgrade"
```

---

### Post by fingau on 2008-12-09
Partyboi2,

yes, I tried that first, but after running for 30 mins or so and getting into the second stage, it stopped without any warning or error. Their was no indication in the log files either.  The documentation on help.ubuntu.com says the alternate cd can be used for 7.10 to 8.04, but does not mention 6.06 to 8.04. Other community documentation says 6.06 to 8.04 is ok but i guess that's wrong.

Anyway, I'm now upgraded to 8.04.1!

What I did was copy all the debS from the alternate cd into /var/cache/apt/archives/ and start gksu update-manager.  Even with all the extra debS already "downloaded" the download stage ran for about 20 hours! That's dialup speed for you!

Thanks for your message.
Regards,
fingau.

---

### Post by grognut on 2008-12-30
Hi,

I've been trying to upgrade dapper to hardy over broadband with no luck. The first two attempts failed and I'm about to try a third.

The update-manager only allows and update to 8.04.1 so in theory it should work but it doesn't. I end up with no fonts.

I'm trying to get mono working on a homeserver dapper 6.06.1 so I'm using a parallel system for testing. I can get it working but I get error with examples from tutorials so I assume the standard install is an older version hence the upgrade.

If my latest attempt fails I may try the alternate CD as well

Good luck

grognut

---

