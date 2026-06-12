---
title: "Administration Password"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by Jumpy on 2006-01-29
Hi
I am completely new to Ubuntu and have currently almost successfully set it up on my Linux m/c
Everything is running fine except for I cannot get into the Administrator area.
When I was installing I cannot remember being asked for a Admin password.
Is ther a default one to use.
If not, how do I get into that area As I need to set up my modem etc.
Many thanks in advance to those that answer this post.
Trev

---

### Post by aysiu on 2006-01-29
Read the third link of my signature.

---

### Post by Jumpy on 2006-01-30
Thankyou Aysiu for your reply
but maybe the point has been missed here
If I use gksudo as suggested I still need the admin password. But this is what I do not know So how do I get over this
Thankyou
Trev

---

### Post by Sutekh on 2006-01-30
Your administration password should be the password of your user.  You also use it when invoking the 'sudo' command.

Did you do a normal installation or an expert/server?

---

### Post by alamba on 2006-01-30
sudo <any command you would like to run as "administrator" (called root in linux)>

Then just enter your current user's password.
Akshay

---

### Post by cainseriph on 2006-01-30
Hi I'm new to Ubuntu also, and I'm basically having the same problem. I didn't do the expert install, I read on another post that root login is disabled. So I was wondering if any one could tell me how to enable it.Thanks in advanced any and all help is appreciated.

---

### Post by aysiu on 2006-01-30
[QUOTE=cainseriph]So I was wondering if any one could tell me how to enable it.[/QUOTE] You don't need to enable it. If you want to run a command in the terminal with root privileges, you preface the command with the word *sudo*. If you want to run a graphical command, you preface it with the word *gksudo*. Then you use your user password to temporarily gain root privileges.

**There's absolutely no reason you need to activate the root account and log in as root**.

---

### Post by cainseriph on 2006-01-30
I understand its not necessary to but I prefer it. It makes some modifications easier and I just feel more comfortable.Thanks for replying tho.

---

### Post by aysiu on 2006-01-30
[QUOTE=cainseriph]It makes some modifications easier[/quote] I'm trying to convince you of the opposite. It's almost always easier to make modifications using sudo than logging in separately as root. 

> and I just feel more comfortable. Okay. If you insist on what's more comfortable, [here's your answer](https://wiki.ubuntu.com/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d).

---

### Post by Jumpy on 2006-01-30
HI thanks again for the help
I have now got into Admin OK. I was using the wrong password.
Thanks again.  So far it looks a great program that I may stick with. I currently use Mandrake, Mepis and Puppy distro,s 
but this looks good.
Trev

---

### Post by cainseriph on 2006-01-30
Thank you aysiu I can totally see your point in not enabling the root login. But I've sadly been away from Linux for a while now, and forgotten many things. The terminal just isn't as familiar to me bot having superuser will allow me to do my modifications and get me back in touch. The link is awesome because once I'm ready to I'd like to disable it again so double thanks.

---

### Post by Jaudus on 2006-01-30
[QUOTE=aysiu]Read the third link of my signature.[/QUOTE]

And you, Good Sir, has made my day by pointing me in the right direction. Thanks.

---

### Post by kunze_m on 2006-02-01
You can set a new root  with "sudo passwd" and then log in. This worked for me.

Regards,
mikel

---

