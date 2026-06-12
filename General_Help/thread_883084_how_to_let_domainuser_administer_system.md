---
title: "how to let domain\user administer system"
date: 2008-08-07
forum: General Help
---

### Post by joec22 on 2008-08-07
I have successfully joined my Ubuntu system to our Active Directory domain using likewise open.  I've successfully added my domain\user to the sudo group and admin group.  I can log into Ubuntu with this domain\user.  But I'm having trouble getting this login to be allowed to edit the menus.  I know where to enable "administer system" for local users(System-Administration-Users and Groups).  But this tool does not show my domain\user account, only the locals.  

If I try to edit the menus, when I select something that requires elevated privilege, it promptly deselects it for me.  So I'm unable to add/remove for example or use the synaptic package manager.

Does anyone have any suggestions?
Thanks

---

### Post by damoxc on 2008-08-07
You'll need to edit the sudoers file. You can do this by dropping down to the commandline and running: ```
sudo visudo
``` (when logged in as someone with sudo privileges).

You can then add:
```
%Administrators    ALL=(ALL) ALL
```
to it which will grant everyone in the Administrators group of the domain sudo rights. I personally added a "UnixAdmins" group to our AD and gave that sudo rights on the machine.

---

### Post by joec22 on 2008-08-08
Yes, I've done that successfully, as I mentioned in the original post.  But that does not let me add the menu items in gnome so I can add programs or run the package manager.

And by the way, sudo visudo did not work on my system, I had to su first in order to run visudo as root.  The man pages also make this point.

---

### Post by damoxc on 2008-08-08
Sorry, it was 3 in the morning.

You could try ```
adduser user@domain admin
``` (Which is the System Admin group locally).

---

### Post by joec22 on 2008-08-08
Thanks for your response, but sorry, that did not work either.  However I believe from some other posts, I've come up with a work-around.  By mapping domain usernames to local usernames I believe I now have everything I need when logging in as domain\user.  This was done through the lwopen:name_map function inside lwiauth.conf.

---

