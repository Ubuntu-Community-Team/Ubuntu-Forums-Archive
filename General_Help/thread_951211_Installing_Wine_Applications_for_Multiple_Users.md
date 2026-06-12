---
title: "Installing Wine Applications for Multiple Users"
date: 2008-10-17
forum: General Help
---

### Post by leehach on 2008-10-17
I just installed my first Wine app.  I was a little surprised when I switched to another user account and didn't see the app available under Applications>Wine>Programs.  Do I have to install the application again for each user?  Or is there a way for multiple users to share one install?

Thanks for you help,
--Lee

---

### Post by MaxIBoy on 2008-10-17
The best way I can think of is to move your .wine directory into /home (not /home/username) and adjust the permissions so that everyone has read/write access. Then, create symbolic links named .wine in every user's home folder, and have them all redirect to the main .wine folder. 


You really shouldn't need to do that manually, but there you go.

---

### Post by leehach on 2008-10-18
Thanks for your response.  Follow-up question:  Is this approach worth it to do, or would you recommend just installing the Windows app multiple times?  What has your experience (or the experience of anyone else listening in) been with the different approaches?

Thanks,
--Lee

---

### Post by jerome1232 on 2008-10-18
I would recomend Maxiboy's approach just because it'll save you on disk space. The only problem is I don't think menu's will be automatically created for each user (Applications->Wine->appname)

I think you'll have to manually change permissions everytime a new program is installed on that program (it'll be owned by whoever installed it.)

It's done that way so that every user can have their own custom wine configurations and etc...

---

### Post by leehach on 2008-10-21
Final question for anyone who has done this.  If you install MSOffice or another Windows app for Wine so that multiple users share a single installation, is the app able to keep user settings (options, toolbar customization, recently-used-files list) separate?  Or does it all get mashed into a single user?

If user settings get mashed together, it might be worth it to sacrifice the disk space required for multiple installs, since I don't expect to be installing very many apps on Wine.

Thanks,
--Lee

---

