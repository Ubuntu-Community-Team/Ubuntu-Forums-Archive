---
title: "Not able to log back as a user/ help with Usermod"
date: 2008-10-08
forum: General Help
---

### Post by Pranav Shanker on 2008-10-08
Hi,

I need some help with account setup with ubuntu(7.0.4). I had basically goofed up due to my lack of knowledge of ubuntu and it surely is unforgiving. The details of the problem is as follows :-

I got this PC with ubuntu loaded on it. It had a user account for xyz by the name xyz. I had changed the account name to abc. Now i am not able to log onto gnome and it gives the following error

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $home directory must be owned by user and not writable by other users. 

And then it would give me another error that my session only lasted 10 seconds. I had then logged onto failsafe Terminal and checked under $home directory that there is only one dir by the name of abc and was empty and so made a new dir by the name of xyz. On making that directory it had 2 dir (Desktop & Pictures) and one file Examples. 

I did tried changing the name of the directory abc to xyz, xyz to abc, copy files from xyz to abc but none worked. After researching online found about usermod but couldnt get the syntax wrong and right now struck. 

Could anyone please help me either to log back as xyz or abc

Cheers

Pranav

---

### Post by justleen on 2008-10-08
You can safely remove that file that bothering you (it only stores what Xsession is default)
make sure /home/zyx is actually owned by the user (check with the "id" command that the id is the same as the owner shown with ls -la /home )

---

### Post by Pranav Shanker on 2008-10-09
Thanks mate. 

Well it seems different UIDs were to be blamed to be blamed. I have made both of them as same UIDs but now facing another problem. 

The moment i try to log in as user 'abc' it gives me the following error

[I]" The files that contain your preference settings are currently in use.

You might be logged in to a session from another computer, and the other login session is using your preference settings files.

You can continue to use the current session, but this might cause temporary problems with the preference settings in the other session.

Do you want to continue? "[/I]

Well no other session is running and i have already removed the ethernet cable just in case. When i click on continue it gives me another error message :-

[I]" Please contact your system administrator to resolve the following problem:
Could not resolve the address "xml:readwrite:/home//.gconf" inthe configuration file "/etc/gconf/2/path":failed: Could not make directory '/home//.gconf' "[/I]

Thinking it might be related to some permission to write to directory .gconf i had changed the permissions to 777 but still no luck. 

Can you please guide me as to what needs to be done 

Thanks Much appreciated

Pranav

---

