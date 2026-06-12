---
title: "suspend / log off issues"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by NooneReally on 2007-10-31
A weird issue has popped up for me in the last week. Half of the time when i suspend now, when i resume I am logged out! This makes suspend almost useless as I obviously can't trust anything I'm running to stick around. I haven't installed anything new lately I don't think...but security & important updates are installed weekly. Has anyone else encountered this? Any ideas on where to look, logfile to check for clues? dmesg doesn't say anything out of the ordinary and I can't find anything else mentioning an error possibly causing this. Its not a gracefull logout either as firefox & another app report their crashing upon next execution.

my laptop is a dell e1410/640m.

---

### Post by cadamr on 2007-10-31
Are you using compiz/compiz-fusion/beryl? If so, try switching to metacity ("metacity --replace") before suspending. Compiz fusion was giving me problems with suspending.

---

