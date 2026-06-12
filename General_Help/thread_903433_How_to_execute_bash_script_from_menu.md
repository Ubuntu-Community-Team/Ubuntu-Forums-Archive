---
title: "How to execute bash script from menu?"
date: 2008-08-28
forum: General Help
---

### Post by abcuser on 2008-08-28
Hi,
in Ubuntu 8.04 I would like to create menu shortcut to execute bash script file. Let just very simplify example. I have created file.sh where there is only one command:
echo "This is echo"

I have given privileges: chmod 777 file.sh

And put the command into menu: System | Preferences | Main menu.

I typed in Command field: /home/myuser/file.sh > /home/myuser/file.log

I tried Application and also "Application in Terminal". But there was no message in file.log file. I have also tried:
/home/myuser/file.sh 2> /home/myuser/file.log  (note 2> to put only error messages into log file). And there is no message in file.log.

I don't understand how "menu" works. Is there any tutorial I could read more about how to set settings in "Main menu"?

Is there any simple way of entering bash script to menu?
Thanks,
Abcuser

---

### Post by DGortze380 on 2008-08-28
> **abcuser said:**
> Hi,
in Ubuntu 8.04 I would like to create menu shortcut to execute bash script file. Let just very simplify example. I have created file.sh where there is only one command:
echo "This is echo"

I have given privileges: chmod 777 file.sh

And put the command into menu: System | Preferences | Main menu.

I typed in Command field: /home/myuser/file.sh > /home/myuser/file.log

I tried Application and also "Application in Terminal". But there was no message in file.log file. I have also tried:
/home/myuser/file.sh 2> /home/myuser/file.log  (note 2> to put only error messages into log file). And there is no message in file.log.

I don't understand how "menu" works. Is there any tutorial I could read more about how to set settings in "Main menu"?

Is there any simple way of entering bash script to menu?
Thanks,
Abcuser

Make your script. Include any redirections to logs in the script. Put it anywhere you'd like. Create a launcher for the script. Add the launcher to the menu.

---

### Post by abcuser on 2008-08-29
Hi,
thank you very much. In bash file has to be the following command: /home/myuser/file.sh

And inside file.sh:
echo "This is echo" > /home/myuser/file.txt

Thanks a lot,
Abcuser

---

