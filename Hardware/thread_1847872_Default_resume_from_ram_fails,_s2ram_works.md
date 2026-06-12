---
title: "Default resume from ram fails, s2ram works"
date: 2011-09-21
forum: Hardware
---

### Post by xLukas on 2011-09-21
Hi,

I'm having issue with DELL Latidtude with ATI video card.

The laptop fails to resume from ram, if suspended by closing the lid. It ends up with display being to turned on (black, no back light).

On the other hand it resumes perfectly if s2ram --force was executed as root.

Any ideas how to solve it or patch?

I had the same issue with opensuse and previous kubuntu install too, so its less likely to be setup issue.

---

### Post by Toz on 2011-09-21
Hello and welcome to the forums.

I have the same problem with an older Toshiba that I have lying around. I ended up just using s2ram because it works. The issue I ran into was trying to make it the default for when running suspend commands.

According to the documentation that I found, you should be able to edit (or create if it doesn't exist) the file **/etc/pm/config.d/module** and add the following content:
```
SLEEP_MODULE=uswsusp
```
as well as the file **/etc/pm/config.d/defaults** with the following content:
```
S2RAM_OPTS="-f"
```

All suspend functions should now work using s2ram. 

Unfortunately, this wasn't the case for me - it still continued to use pm-utils - but this may be because I run Debian sid on that laptop.

You could try the above to see if it works. If not, I can provide a workaround that, although not perfect, will work.

EDIT: Or we can troubleshoot pm-utils in a little more depth.

---

### Post by xLukas on 2011-09-22
Thanks Toz, I hope this would work. 

I'll try your way next time that laptop gets on my hands :)

---

