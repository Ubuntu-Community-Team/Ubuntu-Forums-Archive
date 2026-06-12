---
title: "Burning Programs can't go more than 6 Folders Deep? This isn't happening in Windows"
date: 2008-08-27
forum: General Help
---

### Post by OzzyFrank on 2008-08-27
I wasn't sure whether I should put this under Multimedia or General because this error seems to have something to do with UTF-8. Now, while I'm still scratching my head over not being able to burn single files over 4Gb ([http://ubuntuforums.org/showthread.php?t=867456](http://ubuntuforums.org/showthread.php?t=867456)), I've come across something else I can't burn: folders that go "too deep", which is something I don't have to worry about in Windows with any of the programs. As far as I know, I didn't have to worry about this in Ubuntu either until around the same time I noticed I could no longer burn files larger than 4Gb.

Anyway, in apps like Graveman the burning just fails before it even starts, but with GnomeBaker it gives me an error message after failing immediately:

[B][COLOR="DarkRed"]I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Directories too deep for 'Roxio Easy Media Creator Suite 10/EMC_CONTENT10/Common/Roxio Shared/10.0/DLLShared/1033/Themes' (7) max is 6.[/COLOR][/B]

I gather this is going to happen with any app that uses the **genisoimage** backend, and have yet to find one in Ubuntu that can handle this or similar folders. I'm sure I've never had this problem before, so how can I fix this? If there are apps out there that won't succumb to this, please let me know, but I wouldn't mind getting GnomeBaker and Brasero etc working properly again, since I am used to them. Cheers

---

### Post by iaculallad on 2008-08-27
It could be a limitation of the ISO filesystem. Try using Brasero or k3b instead.

---

