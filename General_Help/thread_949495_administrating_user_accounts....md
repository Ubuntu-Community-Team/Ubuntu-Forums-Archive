---
title: "administrating user accounts..."
date: 2008-10-16
forum: General Help
---

### Post by gdp77 on 2008-10-16
In the class I teach there is a pc where I have installed xubuntu. I have created 2 accounts: **teacher** and **student**.  **Teacher** belongs in the root group and **student** belongs in the user group with no administrative privileges. All my pupils have access in the **student** account.

 I have put a file in the /home/student/Desktop. All my pupils have access to this file, but** I need to make it a read only file and not allow them to be able to delete it or rewrite it. **Now comes the trick question (just for me maybe since I have no administration experience): How can I from my account (teacher) change the attributes of a file that exists in another user's home directory?

1) I have tried entering from gui and access is denied for me (in the /home/studend/Desktop folder). (why access is denied, since I am a member of the root group is beyond me).

2) I have tried from terminal using sudo. No luck. I go to /home/student, but when I try ```
sudo cd Desktop
``` , I get ```
sudo: cd: command not found
```.

Your help would be appreciated. Thank you.

---

### Post by eentonig on 2008-10-16
Go to the users Desktop.
[PHP]cd /home/student/Desktop[/PHP]

Take ownership for the file (otherwise they can just change the right themselves afterwards.)
[PHP]sudo chown root:root <filename>[/PHP]

Give them read access to the root owned file.
[PHP]sudo chmod 754 <filename>[/PHP]

---

### Post by gdp77 on 2008-10-16
> cd /home/student/Desktop  

But (from teacher account) I can go up to the /home/student . Once I try to "cd Desktop", I get a "access is denied" response.

---

### Post by Rhubarb on 2008-10-16
In that case run:
```
sudo su
```
Then enter in your password.
This gives you root until you enter in:
```
exit
```

Please be careful after you run *sudo su*, as any command you type in after will have super user (root) privileges, there is no need to prepend *sudo* to any commands after you've typed in *sudo su*.
You'll notice your prompt will change from a *$* to a *#*, while you see a *#* you're root.

So, try:
```
sudo su
cd /home/student/Desktop
chown root:root <filename>
chmod 754 <filename>
exit
```

---

### Post by gdp77 on 2008-10-16
Thank you very much, I will try it tomorrow when I go to school again.

If I wanted to do this from gui, how could I enter /home/student/Desktop from **teacher** account?

---

### Post by jerome1232 on 2008-10-16
(although I never do it this way)
You can run Nautilus as root

```
gksu nautilus
```

just as an fyi in case you ever need to. You can use sudo to run as any user you want to with the -u flag.
```
sudo -u student [command to run]
```

---

### Post by gdp77 on 2008-10-16
> 
So, try:
```
sudo su
cd /home/student/Desktop
chown root:root <filename>
chmod 754 <filename>
exit
```


I experimented a bit at my own desktop. The problem is that even though I change the owner and attribbutes of the file (let's say test.ods), the directory owner or group can delete the file.

I finally dug a lot and found the solution with [sticky bits](http://en.wikipedia.org/wiki/Sticky_bit)

The solution, finally was :

```
chown root:root /home/student/Desktop/test.ods
chown root:student /home/student/Desktop
chmod +t /home/student/Desktop
```

The last command is the one that permits only to the owner of an item or the directory to be able to delete an item. Without it, my students were able to delete a file in their home Desktop folder, even if I was the owner and had restricted their write access to the file...

---

