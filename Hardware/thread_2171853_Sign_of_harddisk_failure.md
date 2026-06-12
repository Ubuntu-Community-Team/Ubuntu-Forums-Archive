---
title: "Sign of harddisk failure  ?"
date: 2013-09-01
forum: Hardware
---

### Post by prismctg on 2013-09-01
[ATTACH=CONFIG]245918[/ATTACH]

Disk utility  showing this error ( 4 attributes are failing) for some days , is my disk is dying ?

---

### Post by scbingham on 2013-09-02
That's a bit vague.
 
I did a quick search, try: [COLOR=#000000][FONT=Ubuntu Mono]sudo smartctl -a /dev/sdb See what that shows up.

Edit: You might need to install smartctl first: [/FONT][/COLOR]sudo apt-get install smartmontools

---

### Post by mörgæs on 2013-09-02
Please click the cog wheel in the top right corner and post the results.

---

