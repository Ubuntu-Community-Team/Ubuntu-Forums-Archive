---
title: "how do i add another user for samba"
date: 2008-11-18
forum: General Help
---

### Post by washable mist on 2008-11-18
i am currently using a ubuntu machine on my home network as a file server, i can log on fine but the login for the samba share files is the same as my user details.

so basicly i would like to create another user so that other people on my home network can log on with a different logon. i am new to this and don't know where to start so any step by step help would really be appritiated.

---

### Post by rbc on 2008-11-18
Check this:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

In terminal, on the machine you want users to access, type: sudo smbpasswd -a username. You will be prompted, twice, for the user’s samba password. Also, from synaptic, you can get an application called system-config-samba, so that you can use gui to manage your shares and users. What I am not sure about is this: if you have Jim, John, and Jane as users, I am not sure you can one samba username and password for all three people. In other words, you may have to set each user up as a samba user. Could be wrong.

---

