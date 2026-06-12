---
title: "i was told about an issue with ubuntu..."
date: 2008-09-18
forum: General Help
---

### Post by miked860 on 2008-09-18
about it destroying harddrives because it parks the head a lot? is this something i really need to worry about and if so how can I fix it?

---

### Post by cb951303 on 2008-09-18
it's not true.

---

### Post by Sef on 2008-09-18
>  		it's not true. 	

That is correct.  For more information, read [Ubuntu Demon's Blog]("http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/").

---

### Post by mb_webguy on 2008-09-18
Actually, it's somewhat true, assuming [this]("http://hardware.slashdot.org/article.pl?sid=07/10/30/1742258") is what you're talking about.  Yes, there is a problem with some laptops running Ubuntu that causes hard drives to wear out faster than normal.  However, it's not limited to Ubuntu, and occurs on Windows systems as well.  It's also limited to certain specific drives.  The problem apparently lies with hardware vendors who have too aggressive default power management settings for their drives.  Since Ubuntu's policy seems to be to not adjust the default power management settings of a drive (on the assumption that the hardware vendors know best the capabilities of the hard drives they manufacture), it is the drives themselves and not Ubuntu that is at fault.  

Here is [Ubuntu's official wiki entry]("https://wiki.ubuntu.com/DanielHahler/Bug59695") on the subject, complete with a list of affected drives, and some possible workarounds.  And [here]("http://www.advogato.org/person/mjg59/diary/82.html")'s what one the the Ubuntu developers has to say on the subject.

---

