---
title: "[SOLVED] how to download file off of ssh server"
date: 2008-09-19
forum: General Help
---

### Post by RuB3N on 2008-09-19
I have to access a file on a ssh server. And I forgot the whole command to download it to my desktop. When I connect to the ssh sever I put in my password and then im connected. Then I 'ls' to list the directory's contents. And it shows everything that is on the server. To upload/ download those files to my computer I must connect and like download it. (this is hard for me to explain so please if anyone know what im talking about:/)   how do i download it to my computer?


Thank you for your time and sorry if it is hard to understand.

---

### Post by -Zeus- on 2008-09-19
> **RuB3N said:**
> I have to access a file on a ssh server. And I forgot the whole command to download it to my desktop. When I connect to the ssh sever I put in my password and then im connected. Then I 'ls' to list the directory's contents. And it shows everything that is on the server. To upload/ download those files to my computer I must connect and like download it. (this is hard for me to explain so please if anyone know what im talking about:/)   how do i download it to my computer?


Thank you for your time and sorry if it is hard to understand.

the command you want to use is scp; read the man page for explanation.

---

### Post by TheLions on 2008-09-19
the moust easyest way install konqueror and type ```
fish://your_username@location_of_server_eg_ubuntu.com
```

---

### Post by russlar on 2008-09-19
rsync?

---

### Post by The Cog on 2008-09-19
I think sftp supports the **cd** and **get** comments as well as **ls**. But you might find it easier if you are using Ubuntu to use nautilus and enter an address like this into the location bar:
**ssh://username@1.2.3.4/** then navigate to the right folder and just drag the file to your desktop or another nautilus window.

---

### Post by RuB3N on 2008-09-19
I connect by 

ssh [email]username@xxxx.xxxxxxx.xx[/email]
 then i put the password in so on

when im connected i 'ls'

and it lists the files.  specifically 'photo-0049.jpg'

there is a command. that when you open up your terminal you type it in where you connect and say what file you want to download to your desktop.....

---

### Post by mbeach on 2008-09-19
as Zeus pointed out the command you are looking for is scp.

from
[http://www.hypexr.org/linux_scp_help.php](http://www.hypexr.org/linux_scp_help.php)
you'd use the following at your local console:
```

scp your_username@remotehost.edu:foobar.txt /some/local/directory 
```

---

### Post by RuB3N on 2008-09-19
thank you very much

---

