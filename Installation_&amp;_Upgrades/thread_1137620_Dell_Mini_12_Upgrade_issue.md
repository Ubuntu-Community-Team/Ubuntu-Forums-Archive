---
title: "Dell Mini 12 Upgrade issue"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Leviathan433 on 2009-04-25
Has anyone had any issues trying to upgrade Ubuntu on a dell mini 12? I can't seem to select my repositories in software sources when I try to upgrade, even from the console.

---

### Post by brianchidester on 2009-04-27
Is this Mini 12 running the customized dell version, or stock ubuntu? and what do you mean you cannot enable your software sources?

---

### Post by brianchidester on 2009-04-27
Sorry I misread that but the question remains, what do you mean you cannot enable your repositories?

---

### Post by Leviathan433 on 2009-04-27
> **brianchidester said:**
> Is this Mini 12 running the customized dell version, or stock ubuntu? and what do you mean you cannot enable your software sources?

I am running the version that came with my dell. 

What I mean to say with not being able to select my repositories is that on the [Ubuntu]("https://help.ubuntu.com/community/IntrepidUpgrades") upgrade page, they show a way to select the upgrades you want to receive. My software sources window looks nothing like this. I have only three tabs and no way to select distribution upgrades. I also have no way enabling what kinds of updates I want to receive.

I can send a screen shot of what I see if that would be more helpful.

---

### Post by indngolfer on 2009-04-27
Hi, 

I'm having an upgrade issue as well on my new Dell mini. I went to check for new upgrades, but the popup window just stays open and the little wheel just keeps spinning, but never finishes:(

Does anyone know how to resolve this issue?

Thanks, indngolfer

---

### Post by greggh on 2009-04-27
I just got a refurbished Mini 12 from Dell's Outlet site a few days ago. Paid only $266 total after tax and coupon.

Anyway, about doing an upgrade. I had problems too. I tried using upgrade Manager and it crashed half way through the upgrade process.

After rebooting I did the upgrade again using Upgrade Manager. This time it completed with about 37 MB of new packages. But after the upgrade Firefox and some other programs would not open. I would click on the Web Browser Tab and it would try to open it for about 10 secs and then nothing would happen. Something got screwed up.

So then I opened up a terminal window. I typed sudo apt-get update. Entered my password. Then typed sudo apt-get upgrade. It downloaded and installed the new packages again. After this the system was fine and everything worked. I noticed that Firefox was upgraded from version 3.04 to 3.08. So it definitely took this way.

---

