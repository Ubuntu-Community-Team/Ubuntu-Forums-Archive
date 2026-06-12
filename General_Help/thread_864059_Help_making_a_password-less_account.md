---
title: "Help making a password-less account"
date: 2008-07-19
forum: General Help
---

### Post by feistybill on 2008-07-19
I wanted to remove the password from my main account (it's a development pc located in my house, no security concerns) but I don't know how to make Ubuntu accept a blank password.

My /etc/pam.d/common-password says:
password   requisite   pam_unix.so nullok obscure md5

and yet, in System / Users and Groups if I choose "set password by hand", click the password boxes and leave them empty it says "Password is too short - User passwords must be longer than 6 characters etc."

Why? There is no min/max limit in that pam.d config file...

And again, if I use sudo passwd MYUSER -d to delete the password, when I have to click the Unlock button for root access it still asks for a password (empty not accepted, former password not accepted).

If I use "sudo passwd MYUSER" and press enter when asked for a new password, it says "no password supplied". I guess this is normal but as I said before, the -d doesn't work either.

I've run out of ideas... any suggestions?

---

### Post by Claus7 on 2008-07-19
Hello,

first things first I do not know how to help you. Yet, I want to inform you that the reason a password exists it's not only because of security reasons, so as to avoid other users tampering with your pc, but also to avoid harming your system accidentaly. For example typing a command wrongly and damaging a component of your system. That way you have less risk.

From what I know up to now, this is the general idea behind a password and this is a general philosophy behind ubuntu as well. I do not think that it can be easily done. I would advise you not to bother with such a thing.

Regards!

---

### Post by lightstream on 2008-07-19
> **Claus7 said:**
> .. avoid harming your system accidentaly. For example typing a command wrongly and damaging a component of your system.

This would only apply if you were to remove the root password. There's no reason not to have a user account without a password and to somehow set that account to automatically login on boot, as you would still need to enter the root password before doing any sensitive commands.

Unfortunately I don't know if you can create an 'autologin' account like this, but would be interested to find out!

---

### Post by feistybill on 2008-07-19
Well thanks, but why is it every time someone posts a question like mine, everyone starts commenting about the dangers and the perils of doing this and doing that?

The reason I'm using Linux is because I want to be able to customize it and make it do what *I* want.

I own several PCs and I installed Linux on all of them. This specific PC, however, is for development (experimenting) only. No DSL, no LAN, no multiuser, nothing. It can burn and crash, I don't care, there are backups just in case.

Perhaps now I'll even enable the root account and root access on Gnome, and put a nice launcher on my desktop with a nice "sudo rm -rf /" in it.

Now, is there someone who can PLEASE answer my question?

Thanks...

---

### Post by Claus7 on 2008-07-19
Hello,

> **lightstream said:**
> This would only apply if you were to remove the root password...

correct me if I'm wrong, yet the other day I created a new user account to an ubuntu pc. There, I lost an hour or so to find out that I had to connect as the pc administration user (from my friends accound) and take root priviledges because when I had created my user account I didn't click to the option that would enable me to have root rights.

Yet, now, if I connect and I want to have those priviledges, I have to use my own password and not the administration user password. Am I missing something here?

> **feistybill said:**
> 
Now, is there someone who can PLEASE answer my question?

If you do not care to burn your pc, that's ok with me. May be this is close to what you are looking for :
[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_068.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_068.html)

Yet I do not think from that :
[http://brainstorm.ubuntu.com/idea/4096/](http://brainstorm.ubuntu.com/idea/4096/)
that you can create such an account.

Regards!

---

### Post by feistybill on 2008-07-19
> **lightstream said:**
> Unfortunately I don't know if you can create an 'autologin' account like this, but would be interested to find out!

I enabled autologin in the Preferences menu, it works fine. However I still want to use a blank password for my main user (things like the "Unlock" button still require my password.)

---

### Post by sisco311 on 2008-07-19
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by feistybill on 2008-07-19
> **sisco311 said:**
> [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

I already enabled NOPASSWD in sudoers for when I have to use sudo. I just want to use a blank password for my regular user. Nothing more, nothing less.

*sigh*

(either I'm asking in the wrong forum or my english is uncomprehensible)

---

### Post by feistybill on 2008-07-19
> **Claus7 said:**
> Yet I do not think from that :
[http://brainstorm.ubuntu.com/idea/4096/](http://brainstorm.ubuntu.com/idea/4096/)
that you can create such an account.

Ah, so it is not possible. Thanks for your reply.

Now I can safely trash that useless /etc/pam.d/common-password :mad:

---

### Post by syntag on 2008-07-19
Actually, you can remove your password using the -d switch, but you have to authorize the use of blank passwords in gdm and pam:

> sudo passwd -d YOUR_USER_HERE

sudo sed -i 's/#PasswordRequired=false/PasswordRequired=false/' /etc/gdm/gdm.conf

sudo sed -i 's/nullok_secure/nullok/' /etc/pam.d/common-auth

HTH.

---

### Post by aysiu on 2008-07-19
Try [this](http://ubuntuforums.org/showthread.php?t=513820).

---

