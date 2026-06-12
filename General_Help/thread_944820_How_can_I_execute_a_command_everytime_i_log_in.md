---
title: "How can I execute a command everytime i log in"
date: 2008-10-11
forum: General Help
---

### Post by yinglcs2 on 2008-10-11
Hi,

How can I execute a command every time i log in? 
I need to start this command using the environment I setup in .bashrc.

Thank you.

---

### Post by fragos on 2008-10-11
The .bashrc in your user /home/user folder is run whenever you open a terminal session. Anthing you want to run after a login can be initiated in System-> Preference-> Sessions-> Startup programs tab-> Add button. Assuming the you wish to run a shell script, I'd store it in /usr/local/bin and make sure it has execute permission.

---

