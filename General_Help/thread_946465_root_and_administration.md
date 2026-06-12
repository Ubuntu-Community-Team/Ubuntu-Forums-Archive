---
title: "root and administration"
date: 2008-10-13
forum: General Help
---

### Post by senescal on 2008-10-13
im new to ubuntu and struggling to understand how to access the networking configuration.I,ve installed 7.04 ok but get a message saying "The configuration could not be loaded you are not allowed to access this system" i,ve read the community documents and the instruction for user name and password etc and about root but still do,nt understand.I would welcome any help to get started with linix.

---

### Post by snowpine on 2008-10-13
Hi Senescal, the only user name and password you need in Ubuntu are the user name and password you entered during the installation process. You do not ever need to use the username 'root' or a root password. Instead, you should use 'sudo' for example to install Flash 'sudo apt-get install flashplugin-nonfree'. When prompted for a password, enter your user password, not the (non-existent) root password.

Your problem may be because you've added one or more new user accounts; is this the case? If so, you should login as the original user, go to System->Administration->Users and Groups, then add your new user to the 'sudoers' group. This will give that user administrative powers to use sudo.

I'd also encourage you to install Ubuntu 8.04 Hardy Heron Long-Term-Support, as support for 7.04 is being phased out this month, and you won't be able to get updates/upgrades any more. :(

However, it sounds like your question is *really* about networking, so perhaps you could be more specific about what you're trying to accomplish, and I'll do my best to help. :)

---

### Post by Sam on 2008-10-13
To complete snowpine's post, I add the following link which explain all the details about root and sudo.

[uhelp]community/RootSudo[/uhelp]

---

