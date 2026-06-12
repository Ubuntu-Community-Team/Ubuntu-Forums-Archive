---
title: "[SOLVED] Hibernate on t41 broken by Hardy"
date: 2008-09-19
forum: Hardware
---

### Post by afilonov on 2008-09-19
I have Ubuntu on this laptop since 2005. Started with 5.04, then upgraded to 5.10 and then 6.06 (Dapper). All the time both suspend and hibernate worked. Had some problem with hibernate on Breezy, sometimes it took up to 20 min. Had no problems whatsoever on Dapper.

After direct upgrade from Dapper to Hardy, hibernate stopped working. Computer hibernates OK, I mean it shut down fast. The problem is, when I turn it on, it just boots up instead of resuming. I couldn't find any info on my problem here, that's why I'm posting a new thread. Suspend/resume works flawlessly. I have huge swap (3G). Looking in the log files, I see no sign of attempt to resume after initial boot.

---

### Post by dhoulder on 2008-10-05
I had the same problem. See my fix here:

[http://ubuntuforums.org/showpost.php?p=5909790&postcount=10]("http://ubuntuforums.org/showpost.php?p=5909790&postcount=10")

---

### Post by afilonov on 2008-10-20
> **dhoulder said:**
> I had the same problem. See my fix here:

[http://ubuntuforums.org/showpost.php?p=5909790&postcount=10]("http://ubuntuforums.org/showpost.php?p=5909790&postcount=10")

Thanks a lot! Adding resume=/dev/sda2 completely fixed the problem. Strangely enough, my System76 laptop, upgraded from Gutsy, hibernates and resumes just fine without this parameter.

---

