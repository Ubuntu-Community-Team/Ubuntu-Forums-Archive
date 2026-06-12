---
title: "Admin weakness"
date: 2005-11-23
forum: General Help
---

### Post by JimBodkins on 2005-11-23
Hi,


   I'm sure you have heard this before. The absence of a root user weakens what is otherwise a nice OS. I just installed KUbuntu. Once up, I changed the home directory from /home to /usr (which is needed). I also changed the default shell to csh, also needed. 



logged out, and viola - dead system. (DCOP errors) My user cant login, as the utilities didnt create the new home. I cant log in as root - there is no root. I cant boot into recovery mode, to do anything useful would require a root password, which doesnt exist.


Cant login over the net, sshd isnt even installed.


I'm sure there is an 'elegant' reason for not having a root, but I'll be darned if I can imagine what it is.


I am capable of doing most of this manually, but didnt know that was needed. 


I'm sure you have heard all this. I wont mention it again. I suspect that whatever the reason for not having a root will far outweigh adding one. If and when I reinstall, I will add a root.

---

### Post by daller on 2005-11-23
[QUOTE=JimBodkins]Hi,


   I'm sure you have heard this before. The absence of a root user weakens what is otherwise a nice OS. I just installed KUbuntu. Once up, I changed the home directory from /home to /usr (which is needed). I also changed the default shell to csh, also needed. 



logged out, and viola - dead system. (DCOP errors) My user cant login, as the utilities didnt create the new home. I cant log in as root - there is no root. I cant boot into recovery mode, to do anything useful would require a root password, which doesnt exist.


Cant login over the net, sshd isnt even installed.


I'm sure there is an 'elegant' reason for not having a root, but I'll be darned if I can imagine what it is.


I am capable of doing most of this manually, but didnt know that was needed. 


I'm sure you have heard all this. I wont mention it again. I suspect that whatever the reason for not having a root will far outweigh adding one. If and when I reinstall, I will add a root.[/QUOTE]

Have you tried "sudo passwd" ???

---

### Post by az on 2005-11-23
I don't understand what you did to your home directory, but it sounds like you did that wrong.  

"I cant boot into recovery mode,"  Actually, setting a root password will prevent you from getting into recovery mode without a password.  What happens when you try to boot into recovery mode?

I do not understand how having a root account would have prevented your problems?

---

### Post by JimBodkins on 2005-11-23
[QUOTE=azz]I don't understand what you did to your home directory, but it sounds like you did that wrong.  

"I cant boot into recovery mode,"  Actually, setting a root password will prevent you from getting into recovery mode without a password.  What happens when you try to boot into recovery mode?

I do not understand how having a root account would have prevented your problems?[/QUOTE]


Hey, thanks for the replys. I understand what happened, and how to fix it. The problem is, I didnt expect to:


a) not be able to boot into recovery (You cant unless and until you assign a root password - bad idea IMO.

b) have to make the new home directory myself. I can do that, I assumed - bad idea - that kuser (I suspect that is what was running) would take care of that.


sudo passwd root - does work. I hadnt done that, which makes recovery boots impossible. very very bad.


I have a need for /usr/zot instead of /home/zot for other reason. So I just changed home to (in kuser?) /usr/zot. I also manually entered /bin/csh - when in fact csh wasnt even installed. (There is a drop down, that had I looked, would not have had /bin/csh in the list. A minor issue - but csh is always installed, well ... not in this case :) ).


I really really really like ubuntu. But shipping an OS that , for example, has a recovery boot that mandates the use of a password that doesnt exist isnt a good idea. These are pointed comments NOT criticisms. This isnt a flame post. This is good stuff - with a couple of warts. I wouldnt want my sister to have roots password. But I would want to have it incase I needed to recover.


Again, not flames - but I think it is problematic. BTW, I have reinstalled (quick), done the needed reconfiguring, installed apps and am down the road. Its working great.

---

### Post by earobinson on 2005-11-23
you should be able to boot into recovery mode without a root password

---

### Post by JimBodkins on 2005-11-23
[QUOTE=earobinson]you should be able to boot into recovery mode without a root password[/QUOTE]


How? I tried and it asked for a root password to 'admin' the system. It does finally provide a login - which I couldnt do given that my account had no home directory. So - I couldnt login.


Now that I have a root password, I am sure I can use recovery boot.

P.S.
sshd was not installed by default which means that I couldnt attach remote to admin either. Root password and sshd would be great additions to a base install.

---

### Post by 23meg on 2005-11-23
If it asked for a root password that means you've enabled the root password. Maybe you just didn't enable root to login via KDM.

---

### Post by JimBodkins on 2005-11-23
[QUOTE=23meg]If it asked for a root password that means you've enabled the root password. Maybe you just didn't enable root to login via KDM.[/QUOTE]

The root account exists, which is why it asks for the root password. (Ubuntu is just shipped without roots password set and doesnt ask for it during install). The recovery boot - like many unix's before linux, asks for roots password in order to enter admin or maintanance mode. No password, no maintanance. If I could have logged in as a normal user, perhaps I could have used sudo, but I couldnt. My goal with recovery, was to create the required home so I could login. The user account - absent a home directory - was invalid and root had no password. :( It does now :)

These are just comments. Set roots password during install (and I personally would like sshd installed and enabled).

---

### Post by 23meg on 2005-11-23
Ubuntu is very very very unlikely enable root by default in future versions. This has been discussed many times; it just isn't going to happen. On the other hand, the default behavior with the recovery console should be that it won't ask you for a password if you haven't created a root password. 

There's a good chance that you did enable the root account manually, but forgot about it later on. This is one of the reasons why logging in as root isn't enabled as a default; users do forget their root passwords in single-user situations. This is a universal rule.

---

### Post by JimBodkins on 2005-11-23
[QUOTE=23meg]Ubuntu is very very very unlikely enable root by default in future versions. This has been discussed many times; it just isn't going to happen. On the other hand, the default behavior with the recovery console should be that it won't ask you for a password if you haven't created a root password. 

There's a good chance that you did enable the root account manually, but forgot about it later on. This is one of the reasons why logging in as root isn't enabled as a default; users do forget their root passwords in single-user situations. This is a universal rule.[/QUOTE]


This all happened within 5 minutes. I didnt enable it. Honest. :)

---

### Post by 23meg on 2005-11-23
If you can burn down an installation in five minutes you may need tighter measures than the no root policy.. just kidding. Well, there isn't any other explanation of the behavior you describe that I know of.

Having ssh enabled by default is yet another security risk. Ubuntu does not have any listening ports by default. Your requests both undermine the basic security model that Ubuntu has been insisting on from the beginning: no open ports and no root login by default. They're both very very very unlikely to be enabled in future versions. This has been discussed a million times; if you do a few forum and wiki searches you'll get to know the rationale behind it.

---

### Post by Zeddicus on 2005-11-24
[QUOTE=JimBodkins]This all happened within 5 minutes. I didnt enable it. Honest. :)[/QUOTE]

However, it sounds like you used kuser to do some user-administration...

I don't know if the default behavior of kuser will create a root user when you apply the changes you've made, but it's a possibility... and if it's the case, it's a bug and needs to be fixed (I haven't checked, but will when I have a chance).

Single user mode definitely *does* work w/o a password on a default system.  I've had to do it on more than one occasion, and have never enabled the root acct on an Ubuntu system. ;)

My hunch says this very well may be kusers not being entirely ubuntu-friendly.

---

