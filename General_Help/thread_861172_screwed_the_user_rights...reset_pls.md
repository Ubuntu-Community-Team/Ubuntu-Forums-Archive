---
title: "screwed the user rights...reset pls"
date: 2008-07-16
forum: General Help
---

### Post by Azrael90 on 2008-07-16
Hi 
I did change the user basic directory /home/username  to / and now I cannot login anymore because ubuntu crashes.

Is there a way to reset the user rights by using the ubuntu disk or sth ?

---

### Post by sisco311 on 2008-07-16
Reboot in recovery mode
and from the root shell
change the home directory back:

```
usermod -d /home/username username
exit
```

---

### Post by jag32266 on 2008-09-07
Hi,
Getting the old windoze frustration factor going and it's all my fault. 
I recently installed on my Win XP sys Ubuntu from the Live CD I downloaded 08/25/2008. Then I promptly went on vacation only to come back and find I've forgotten both my user name and password. I have installed the system and am not booting from the disk any more- wanted to press myself to learn this system once and for all.

I've searched various threads and forums but most seem to address a corrupt MBR or sudo and direct me to open a window. Sorry, can't even get pass the logon to open a window.
And I've tried to boot again from the disk. Catch 22 there since all it seems to do it take me back to sq 1. Can't log in to open a window/command prompt.
Tried to press the escape key after the Grub started and do a repair in recovery mode but no luck either.

Am I at the point where I need to re-install Ubuntu? And if so, how to do that?

Embarrassed to say I've been pc'ing for a decade- read geek. Apparently I'm not so I'd appreciate any assistance in the matter.
Please help me start my trip away from MS and bill gates 

Point of all this- I did try the above code provided in recovery mode and error msg stated there was no "username" dir. I typed in "usermod -d /home/username username" and got the error msg. So I tried "usermod -d /home/username" only to get the same msg.

Further help is requested, please.

---

### Post by sisco311 on 2008-09-07
> **jag32266 said:**
> Hi,
Getting the old windoze frustration factor going and it's all my fault. 
I recently installed on my Win XP sys Ubuntu from the Live CD I downloaded 08/25/2008. Then I promptly went on vacation only to come back and find I've forgotten both my user name and password. I have installed the system and am not booting from the disk any more- wanted to press myself to learn this system once and for all.

I've searched various threads and forums but most seem to address a corrupt MBR or sudo and direct me to open a window. Sorry, can't even get pass the logon to open a window.
And I've tried to boot again from the disk. Catch 22 there since all it seems to do it take me back to sq 1. Can't log in to open a window/command prompt.
Tried to press the escape key after the Grub started and do a repair in recovery mode but no luck either.

Am I at the point where I need to re-install Ubuntu? And if so, how to do that?

Embarrassed to say I've been pc'ing for a decade- read geek. Apparently I'm not so I'd appreciate any assistance in the matter.
Please help me start my trip away from MS and bill gates 

Point of all this- I did try the above code provided in recovery mode and error msg stated there was no "username" dir. I typed in "usermod -d /home/username username" and got the error msg. So I tried "usermod -d /home/username" only to get the same msg.

Further help is requested, please.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by ubername on 2008-09-07
> **jag32266 said:**
> Hi,
Getting the old windoze frustration factor going and it's all my fault. 
I recently installed on my Win XP sys Ubuntu from the Live CD I downloaded 08/25/2008. Then I promptly went on vacation only to come back and find I've forgotten both my user name and password. I have installed the system and am not booting from the disk any more- wanted to press myself to learn this system once and for all.

I've searched various threads and forums but most seem to address a corrupt MBR or sudo and direct me to open a window. Sorry, can't even get pass the logon to open a window.
And I've tried to boot again from the disk. Catch 22 there since all it seems to do it take me back to sq 1. Can't log in to open a window/command prompt.
Tried to press the escape key after the Grub started and do a repair in recovery mode but no luck either.

Am I at the point where I need to re-install Ubuntu? And if so, how to do that?

Embarrassed to say I've been pc'ing for a decade- read geek. Apparently I'm not so I'd appreciate any assistance in the matter.
Please help me start my trip away from MS and bill gates 

Point of all this- I did try the above code provided in recovery mode and error msg stated there was no "username" dir. I typed in "usermod -d /home/username username" and got the error msg. So I tried "usermod -d /home/username" only to get the same msg.

Further help is requested, please.

Might be a simple question, but did you use 'username' or the username  (e.g.jag) you set yourself up with? I note you say you have forgotten the username. Maybe try a few guesses? It can do no harm.

---

### Post by sanemanmad on 2008-09-07
> Point of all this- I did try the above code provided in recovery mode and error msg stated there was no "username" dir. I typed in "usermod -d /home/username username" and got the error msg. So I tried "usermod -d /home/username" only to get the same msg.

Hi jag32266~ 

1. Did you forget your username altogether?
2. You shouldn't be typing 'username' that is an example. Instead, **sisco311** meant you should replace 'username' with your username.

---

### Post by pebo on 2008-09-07
If you can't remember your $username you can find it again. First go into the grub menu at boot and edit the kernel line by adding ```
init=/bin/bash
```at the end. then hit b to boot which will take you to a root shell. Then run ```
less /etc/passwd
```where you will find a list of users. Your username will most likely have an id of 1000 so look for a line with something like 'xxx:x:1000....' where xxx will be your username. Armed with that you can do ```
passwd xxx
```where xxx is your newly found username to create a new password. Then hit ctrl-alt-del and reboot. You should then be able to log in in the usual way.
hth

edit: that smiley is supposed to be 'colon x'

---

### Post by jag32266 on 2008-09-07
hi all,

Great suggestions and even more mistakes on my part. Yes, I did use username since I forgot mine I thought it might reset the file.
I'll try and use all the advice mentioned above- thank you soooo much!!

I'll let you know how it goes, too.

---

### Post by jag32266 on 2008-09-07
sisco311- that was great help and it DID the trick for me, so thank you very much.

I am perplexed as to why google didn't pull that page up when I did a search  for resetting passwd, tho. I did look in other places than just these forums, oh well.

Bookmarked those pages too!

Anyway- I'm now a happy camper and fully appreciate all your help folks. Thank you so much. Hope this can help out others,..

---

