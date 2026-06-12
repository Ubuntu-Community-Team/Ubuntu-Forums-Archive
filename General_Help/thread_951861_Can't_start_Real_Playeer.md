---
title: "Can't start Real Playeer"
date: 2008-10-18
forum: General Help
---

### Post by rozeni on 2008-10-18
Hi, 

I've installed Real Player 11 in the default directory as described elsewhere.  However, I didn't get the entry in the Application Menu.  Moreover, when I type 'realplay' in the terminal I get "Permission Denied".  When I type "sudo realplay" I am asked for password and after I enter it Real Player starts.  For this reason adding it to the menu manually doesn't work.

Why does all of this happen?  I've enabled Automatic Login, may this be the cause of the problem?

Thanks for any help

---

### Post by oldos2er on 2008-10-18
> **rozeni said:**
> Hi, 

I've installed Real Player 11 in the default directory as described elsewhere.  However, I didn't get the entry in the Application Menu.  Moreover, when I type 'realplay' in the terminal I get "Permission Denied".  When I type "sudo realplay" I am asked for password and after I enter it Real Player starts.  For this reason adding it to the menu manually doesn't work.


 I believe this error is caused by running the program when the installer prompts you to, immediately after installation. By "default directory" do you mean /opt ?

---

### Post by rozeni on 2008-10-18
Yes, I've installed in the opt directory.  So, how so I fix this mess?:(

---

### Post by oldos2er on 2008-10-18
I'm not sure. You could try deleting /opt (assuming there's nothing there but Realplayer), then reinstall.

---

