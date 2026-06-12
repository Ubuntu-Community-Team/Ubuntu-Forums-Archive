---
title: "AD user profile issue"
date: 2008-12-02
forum: General Help
---

### Post by sbarnesi on 2008-12-02
I am using Likewise Open to authenticate to Active Directory, which works great. I have two local users created on my machine for various needs, but the primary users will be AD users. I'd like to be able to place launchers on their (the AD users) desktops. I have placed a test launcher in /etc/skel/Desktop, but it doesn't seem to copy properly.

Is there anything special I need to do to the launcher in order for it to copy properly? 

My initial thought was that Likewise wasn't copying from /etc/skel, but from somewhere else. Nothing on Likewise's site mentioned that. To test that, I created another local user, and he received the launcher on his desktop. The AD users don't seem to get everything from /etc/skel. I suppose I could go the long way and created a little script that will check to see if the launcher exists or not and copy it to their desktop at logon, but I'd rather not have to do that.

Thanks!

---

