---
title: "Samba Share"
date: 2008-10-23
forum: General Help
---

### Post by Aysah on 2008-10-23
I'm having a problem figuring this out in my head so I'll try to explain this as best I can.

We set up an SFTP server with jailed users in their own specific /home directory such as EastWest.  Based on the instructions I followed everything is working fine as long as root owns "/home/ezLink.System/IN.DataFiles" and EastWest owns "/home/ezLink.System/IN.DataFiles/EastWest".

So all was well until we needed to make a SambaShare for our ezlinksystem user to be able to access any of these directories.  We cant seem to write any files to the directory from windows.

Can someone please direct me on how to make root, ezlinksystem, and EastWest all own the same directory. EastWest should only be able to write in the EastWest folder but ezlinksystem and root needs to be able to have full access of the ezLink.System directory.

---

### Post by spiderbatdad on 2008-10-23
It sounds, to me, like you want to create a "group" possibly called ezlink and make that user and the windows account user members of that group.

[http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)
[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

---

### Post by Aysah on 2008-10-23
> **spiderbatdad said:**
> It sounds, to me, like you want to create a "group" possibly called ezlink and make that user and the windows account user members of that group.

[http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)
[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

well the share worked when I made all the users part of the same group called ezlinksystem but something weird does happen and I'm not sure if its a bug.  To make the SFTP server I followed the rules of this article:

[http://ubuntuforums.org/showthread.php?t=858475]("http://ubuntuforums.org/showthread.php?t=858475")

The only thing slightly different is that I dont have the group ID identical to the username but rather the group ezlinksystem as the owner of all my SFTP directories.  It does work and actually jails the user but I cant write in my Samba Share.

I've searched high and low and it seems if i change the permissions to anything but CHMOD 755 it doesnt work but then when I put it back it works. I even did the dreadful 777 and it doesnt work.  I'm so confused... I really need this by the end of next week for my boss..  :confused:

---

### Post by Aysah on 2008-10-24
bump..

anyone have any knowledge of using sftp and then making that jailed home directory a samba share so that windows users can touch it??

---

### Post by Aysah on 2008-10-24
bump..

anyone have any knowledge of using sftp and then making that jailed home directory a samba share so that windows users can touch it??

---

