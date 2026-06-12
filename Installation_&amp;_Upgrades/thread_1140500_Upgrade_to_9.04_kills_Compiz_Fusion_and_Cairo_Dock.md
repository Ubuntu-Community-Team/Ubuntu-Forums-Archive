---
title: "Upgrade to 9.04 kills Compiz Fusion and Cairo Dock and the indexing is corrupt"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by seoras on 2009-04-27
Decided to upgrade my home PC from 8.04 to 8.10 then to 9.04 All went apparently smoothly until the final reboot, then I noticed the following problems:-

[LIST]
[*]Cairo Dock started behaving weirdly, no background transparency for example
[/LIST]
[LIST]
[*]My Compiz Fusion desktop effects have completely disappeared and cannot be re-enabled
[/LIST]
[LIST]
[*]Tracker keeps reporting that the index is corrupt and the only option is to re-index the whole system?
[/LIST]
[LIST]
[*]Cannot enable any visual effects at all. They worked fine with 8.04 
description: VGA compatible controller, product: 82865G Integrated, Graphics Controller, vendor: Intel Corporation
[/LIST]
I've searched through the forums and many have reported similar problems but I have yet to find a solution. I have not experienced these sort of problems with upgrades since 7.10 and had thought them a thing of the past, looks like I was wrong. I think I might revert back to 8.04 as there are clearly bugs in 9.04 and it clearly does not work well on my Dell Dimension 3000.

---

### Post by cariboo on 2009-04-27
To repair the tracker problem you simply have to delete Tracker's current DB and reindex everything. So delete " ~/.cache/tracker/* " and reindex everything and the problem is gone.

Your video problem is a little harder to fix. If you had checked the [Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/904") you would have seen there was a problem with the Intel graphics drivers. To repair the problem have a look [thread=1130582]here[/thread]

---

### Post by seoras on 2009-04-28
Thanks, I appreciate I probably should have read the release notes but having now read them I don't think this would have put me off an upgrade. I had already tried the first workaround with no success and the second is experimental so no thanks. Think I'll still go back to 8.04 whatever advantages there may be with 9.04 are outweighed by the bugs and other issues.

---

### Post by DavidTangye on 2009-05-01
There are many posts here all repeating your issue. For a solution see the launchpad bug reports, in this case [this one is good]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912") and there are many duplicate reports there too.
I can recommend you search launchpad before posting issues, especially [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu), as your answers are often already there, and it saves these forums being filled with 10,000 'me too' issues.

---

