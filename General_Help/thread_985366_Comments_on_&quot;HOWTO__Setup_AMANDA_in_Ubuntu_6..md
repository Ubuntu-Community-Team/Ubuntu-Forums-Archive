---
title: "Comments on &quot;HOWTO : Setup AMANDA in Ubuntu 6.06 / 6.10 with Virtual Tapes&quot;"
date: 2008-11-17
forum: General Help
---

### Post by cbciv on 2008-11-17
The following are comments on the HOWTO article <http://ubuntuforums.org/showthread.php?p=2470030> by cjsmith.  I would have posted my comments in that thread, but it has apparently been archived and is no longer available for additional replies.

First, thanks to cjsmith the the effort he took to put this together.

I'm running 8.04, Hardy Heron, while the HOWTO was written for 6.06, so that may account for some of the differences.  I didn't spot an Amanda version listed in the HOWTO, but I'm using 2.5.2p1-1.

1. Rather than have a single /etc/xinetd.d/amanda with entries for all three services as suggested by the article, the amanda package that I installed from the repositories created a separate file for each service: /etc/xinetd.d/amanda, /etc/xinetd.d/amandaidx and /etc/xinetd.d/amidxtape.

2. In the section on amanda.conf, the article recommends adding a number of lines to the file, including these:

```

diskdir "/tmp"
disksize 5000 MB

```

In my case, doing so caused Amanda to complain:
```

"/etc/amanda/DailySet1/amanda.conf", line 124: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 124: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 126: configuration keyword expected
"/etc/amanda/DailySet1/amanda.conf", line 126: end of line is expected
"/etc/amanda/DailySet1/amanda.conf", line 127: configuration keyword expected

```

I haven't determined if commenting them out causes any problems, but amcheck is happy.

---

