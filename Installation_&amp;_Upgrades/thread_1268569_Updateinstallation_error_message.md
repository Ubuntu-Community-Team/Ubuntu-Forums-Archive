---
title: "Update/installation error message"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by Root 5 on 2009-09-17
[LEFT]Hi,

I'm fairly new to Ubuntu and am currently running Ubuntu Studio and I've had no problems with it up until this week. When trying to install a new program or just trying to install updates I've been getting the following error message when I hit the install button:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Does anyone out there know what this is all about? I'd be really, really grateful if somebody could explain to me how I can resolve this issue.

Cheers,

Root 5
[/LEFT]

---

### Post by Cheezespread on 2009-09-17
Welcome to the forums.

Could you please give details about the program you are trying to install ?.

The error message speaks for itself. Lets break it down.
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

The installation files are usually in the form of packages and dpkg is related to that. The installtion was interrupted in some way and you are asked to enter the below code into terminal.

```
sudo dpkg --configure -a
```

This will require you to enter the password , but you won't be able to see it . Just type the password and press "Enter".

Let us know if you have hit some errors again.

---

### Post by Root 5 on 2009-09-17
Thanks for your response. I'm currently trying to install some Firefox updates, I hit the install updates button and then after I've entered my password this error message appears. I understand that I have to 
enter ' sudo dpkg  - - configure -a ' into the system somewhere but I don't know where. You mention typing it into the terminal. How do I do this? Sorry for my ignorance!

---

### Post by Cheezespread on 2009-09-17
Sorry . My mistake. I assumed you were installing it from the terminal.

Teminal can be accessed from Applications -> Accessories -> Terminal.

Check this [link]("http://www.psychocats.net/ubuntu/terminal")if you are still unsure.

When you have opened the terminal , it should look something like this :

<username>@<Desktop name>:~$ without the <> . 
username - your Ubuntu login id
Desktop name - The system name

Type in the command into the terminal . You will prompted to enter a password. But you can't see it. Just type it and press enter.
[Passwordinterminal]("http://www.psychocats.net/ubuntu/passwordinterminal")

---

### Post by Root 5 on 2009-09-17
Thank you. I have just gone through the process you've just advised me of and the command it's asking me to run appears to be linked to open office, which I had trouble installing last week. After I typed in the command and entered my pass word another message in terminal came up saying:
[I]
error processing openoffice-emailmerge (--configure): subprocess post-installation script killed by signal (interrupt)[/I]

Then my computer crashed. Open office did install onto my system last week, but it must have been corrupted in some way. I will remove the program from my system and see how things go from there.

Thanks for all your help. I'll let you know how I get on.

Have a great day.

---

