---
title: "log on"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by ejbirdwell on 2009-04-04
I installed Ubuntu from the downloaded disc and chose to install with windows. After auto installation, I got the sign on window and could not sign on. Tried all possible combos of user name and password. Any suggestions on how to determine my logon and password or reset it to the one I'm using here? Thanks
I'm new at forum communication so bear with me!

---

### Post by coffeecat on 2009-04-04
Welcome to the forum. :)

Some questions:

When you say you installed with Windows, do you mean you used the Wubi installer, or that you set up a dual-boot Windows and Ubuntu, such that when you boot up you get a menu with the choice of Ubuntu or Windows?

Did you use the 'Desktop' CD to install which lets you run a live environment from the CD before you install, or did you use the alternate CD? You'll know the latter. It gives you an old-fashioned looking text installer.

When you installed, do you remember a screen that looked like this:

[IMG]http://news.softpedia.com/images/extra/LINUX/large/ubuntu804installationguide-large_008.png[/IMG]

That's where you put your username and password in and that's what you are being prompted for now.

Last thing. As far as I am aware the only way you can install without selecting a username and password is to do an OEM install. And I believe you can only do this from the alternate CD. Does that sound familiar?

---

### Post by ejbirdwell on 2009-04-04
> **ejbirdwell said:**
> I installed Ubuntu from the downloaded disc and chose to install with windows. After auto installation, I got the sign on window and could not sign on. Tried all possible combos of user name and password. Any suggestions on how to determine my logon and password or reset it to the one I'm using here? Thanks
I'm new at forum communication so bear with me!

Hope this reply reches you. I installed using the menu on the cd that said "install inside windows. It did an auto intall with that used an internet connection I believe. If I can't resolve this problem can I uninstall the product, re download and go through the install again?( Will the install work over the installed copy instead of uninstalling?)Any help is appreciated.(is this the proper way to reply on the forum?

---

### Post by cariboo on 2009-04-04
You don't need to reinstall, that is the Windows way of doing things. Start in recovery mode, you may have to press escape to see the grub menu, then select recovery mode. Once at the menu  select drop to root prompt. At the prompt type:

```
passwd <username>
```

where <username> is your username. The above command will allow you to create a new password for your user.

Jim

---

### Post by coffeecat on 2009-04-04
> **cariboo907 said:**
> You don't need to reinstall, that is the Windows way of doing things. Start in recovery mode, you may have to press escape to see the grub menu, then select recovery mode. Once at the menu  select drop to root prompt. At the prompt type:

```
passwd <username>
```where <username> is your username. The above command will allow you to create a new password for your user.

Jim

See the OP's first post. They don't know their username, so that won't work. Besides, it sounds like a Wubi install, so uninstalling from within Windows seems quite a reasonable thing to do.

> **ejbirdwell said:**
> Hope this reply reches you. I installed using the menu on the cd that said "install inside windows.

That does sound like a Wubi install. If so, have a look at [this Wubi howto]("http://www.brighthub.com/computing/linux/articles/7982.aspx"). Look at the first screenshot. Sorry, but there's absolutely no way you could have proceeded without choosing a username and password.

However, that very well may be academic now. I don't have any experience of Wubi, but I believe it is possible to uninstall it from the Windows Add/Remove utility. If I'm wrong I'm sure someone will chip in. Then you could reinstall the Wubi way, but this time please keep a note of the username and password you choose. As you've found out the hard way, without them you're at a disadvantage. In this respect, Linux is much more strict than Windows, but that is a good thing. It's the price you pay for far superior security.

Do persevere. It's worth it in the long run.

Good luck!

---

