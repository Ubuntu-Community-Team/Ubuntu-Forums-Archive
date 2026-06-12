---
title: "Couple of gripes immediately after installing 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Niva on 2009-11-01
I cannot seem to enable root password.  I'm not talking about graphically logging in as root, I'm talking about using su in the command prompt.  

Grub 2: looks great, it's definitely a step up.  How the f do I configure it?  Part of my problem is that I cannot sudo gedit /etc/default/grub Never mind that I can't locate exactly where the boot menu is anyways so that I know where my windows partition is so that I can make that my default boot.  I dual boot all my machines and please don't ask my wife to understand what grub is or to use linux.  What I'm trying to say here is that there should definitely be a GUI to configure Grub 2 and I DON'T see it in my System>Admin menu.  

One of my machines is old, athlon xp 2500+, but it came to a crawl with 9.10  ...
I honestly thought 8.04 was slow on this machine but this new version confirms to me that newer linux distros are definitely becoming more resource hungry and I'm not exactly sure where that is.  But out of the box 9.10 takes up more ram and is less responsive on this hardware than windows XP.  Seriously.

I'm probably going to go back to 8.04 on this machine and I'm not sure I'll upgrade my other machines to 9.10 even though I've always upgraded my newer machines.  Jaunty has been great for those machines and until I'm sure I can resolve the grub and SU issues no friggin way.  Maybe I'll try the lxde fedora or the new suse on this machine but I really like to stick with Ubuntu at this stage.

---

### Post by sliketymo on 2009-11-01
A good place to start.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by legalguy on 2009-11-01
I was able to enable root password, the procedure is almost the same (System>Users), they changed the unlock button.  But I enabled it.

Graphical root login has been disabled.  I had LXDE installed, that will let you login as root.  (Click other, type in root, and a bunch of options will appear on the lower panel bar.  Select LXDE, and it will let you log in, instead of getting an authentication failure.  Mods will probably ban me for telling you this, root login seems to be something of a holy shrine at Canonical.

---

### Post by Niva on 2009-11-01
> **sliketymo said:**
> A good place to start.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I visited that site, if you'd read my post you'd realize that I couldn't edit /etc/default/grub 

Not only that but such a major conifguration change should've come with a GUI and a simpler way to configure.  I'm finding myself chasing config files all over the system with no clear indication of where to go besides searching online.

---

### Post by Niva on 2009-11-01
> **legalguy said:**
> I was able to enable root password, the procedure is almost the same (System>Users), they changed the unlock button.  But I enabled it.

Graphical root login has been disabled.  I had LXDE installed, that will let you login as root.  (Click other, type in root, and a bunch of options will appear on the lower panel bar.  Select LXDE, and it will let you log in, instead of getting an authentication failure.  Mods will probably ban me for telling you this, root login seems to be something of a holy shrine at Canonical.

I don't care about using root as a login. 

What I want is to be able to use super-user, or to type in su at the command prompt and avoid having to type sudo for every one of your supersuser commands.

I enabled the root password, it generated no errors.  But I can't use it in any way.  When I type "su" and enter my password I get a error message stating "su: Authentication failure"  It appears they've somehow managed to completely disable the root account except through the regular ways ubuntu uses it by "sudo" and their own tools.

---

### Post by autocrosser on 2009-11-01
Greetings--

Take a look thru the (closed) Karmic-Development forum: [http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)  Most of your questions can be answered with a search there..

---

### Post by lswb on 2009-11-01
> **Niva said:**
> I don't care about using root as a login. 

What I want is to be able to use super-user, or to type in su at the command prompt and avoid having to type sudo for every one of your supersuser commands.

"sudo -i" will open a root shell.

---

### Post by Niva on 2009-11-02
OK guys thanks for these responses, I'm taking a look at the closed forum and indeed it seems to answer the questions I have for Grub 2.

I'm really ranting here but such a major update to what I consider one of the main aspects of the linux OS and the ability to dual boot should've been more polished.  Lets hope it is for Lucid Lynx.

lswb I'll check the workings of sudo -i when I get home tonight.  Hopefully it resolves some of the issues I'm having right now.

---

### Post by Niva on 2009-11-03
lswb the sudo -i command certainly worked and resolved most the issues I was having thusfar in terms of being unable to access the root account.

It would still be helpful if ubuntu threw an error when people attempt to log into user through "su" command if that's how it's going to be from now on.

Thanks for the help of resolving that one.

---

