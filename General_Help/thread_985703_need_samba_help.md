---
title: "need samba help"
date: 2008-11-17
forum: General Help
---

### Post by majikhotline on 2008-11-17
Hello unbuntu conutry,
I have been trying to get samba to work with my windoze, and cant seem to get into the files....can anyone help me

---

### Post by cariboo on 2008-11-17
You don't need samba to access windows shares. The only time you need samba is when you are trying to share files from your Ubuntu computer. The one thing that most people seem to have trouble with is the workgroup name. Make sure both computers are in the same workgroup.  It is probably easier for you to change the workgroup name in windows then it is in Ubuntu. If you are using windows XP home, the workgroup name is usually MSHOME, Ubuntu defaults to WORKGROUP. Change the windows workgroup to WORKGROUP and you should be OK.

Jim

---

### Post by majikhotline on 2008-11-18
i configured both computers with the same workgroup, i can see the linux folder in the xp machine but cant access it....any suggestions....also when i restart samba it tells me ¨ unable to resolve host ¨

---

### Post by majikhotline on 2008-11-29
i need help

---

### Post by rbc on 2008-11-29
Post back with your /etc/hosts file. In terminal, type: cat /etc/hosts

---

