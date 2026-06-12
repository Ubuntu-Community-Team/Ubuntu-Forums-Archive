---
title: "Mounting Remote Shares"
date: 2005-11-14
forum: General Help
---

### Post by bschneider on 2005-11-14
Hi All,
I am new to ubuntu, but so far I love it.  Anyway, I work for a school district and we have it authenticating to a windows AD for the students to log in.  Now all that is necessary is a way for their home drives on the windows server to be automatically mounted on the local machine at logon.  Does anyone know how to make this happen?  I have tried in the past with other distributions to use pam_mount with out success.  Is it the thing to use or should something like smb4k work better.

Thanks for the help
Brian Schneider
Oak Hill High School
Oak Hill, OH

Problem solved.  After finding out how to install pam_mount it was a piece of cake.  Just needed to change the config file and it all works great.
From what I have looked at and experienced, Ubuntu has to be the easiest system to work with when it comes to the windows compatabilty.  This is the first time I have managed to get the authentication and mounting to work consistantly and I have tried over the last 8 months various other distributions including, Suse, FC4, Mandrake and none of them would ever work as well or as easy.

Keep up the great work.
Brian Schneider

---

