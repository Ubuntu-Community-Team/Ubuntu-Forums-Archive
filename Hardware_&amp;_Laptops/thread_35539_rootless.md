---
title: "rootless"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by ubuntuneube on 2005-05-19
Peace, All.   This is a second install of ubuntu 4.  The first was also without root bearings.  The log (during start-up) mentions something relevant to root-less, being temporary.  I can't quite make out what it's saying.  I cannot change anything, because I wasn't permitted to sign in as root, only as 'user.'  When I try to use a terminal, I'm asked for a root p/w which of course I don't have.  I can't get on line via ubuntu, and would like to change some settings, but cannot.  What would be a good  remedy for this problem?

---

### Post by Zelut on 2005-05-19
Well ubuntu doesn't really use a 'root' account for changing settings.  I think this is due to the fact that too many people run as root which is NEVER a good idea.

If you want su (super user) powers you can use 'sudo <command>' which will then ask you for your password & allow you to run root enabled commands.  Also, if you'll need su access for a while you can use the 'sudo -s' followed by your password.

I hope this helped.

---

### Post by BackslashN on 2005-05-19
The root user isn't active at default settings.

you should try 'sudo'.

e.g.

sudo the_command_you_write

if you still want the root user just define a root password with:

sudo passwd root

---

### Post by codejunkie on 2005-05-19
you can also enable the root user by typing sudo passwd root enter your password then enter the new root password.

---

### Post by XDevHald on 2005-05-19
If you're trying to login as root via on the login screen when you first boot up, [u][i]you can't

[/i][/u]To change/make the password to root follow the steps provided below.

Step 1: **System** > **Administration** > [b]Users and Groups

[/b]Step 2: Click on **root **and select **Preferences **or **Edit **whichever one is available to you.

Step 3: You'll notice when it brings up the dialog box for you to change the info on root, you can change the password to root provided below on that dialog box and uncheck the box that shows that root has a password, in this case it's scrambled.

Last Step: Click the box above to check it so you can set a password for yourself in which root will be given a password for you to access back end folders/files and etc. Click Ok, then Ok again on the next screen, and you're all set :)

---

### Post by ubuntuneube on 2005-05-19
Peace, All.   Thanks, kuyaedz, BackslashN, codejunkie, and BB, for the input, and quick replies.   I'll give it a try.

---

### Post by BackslashN on 2005-05-19
have fun :)

---

### Post by ubuntuneube on 2005-05-20
Peace, All.  Well, I finally got into root.  Your help is appreciated.  But you know, it seems I haven't the right info to get ubuntu, on line.  Is there a guide that explains what is needed to satisfy online requirements?  I entered all (I think) of the info from my ISP, but shouldn't I install the ISP's software?  I see no mention of this in the documentation. Is the server, installed with ubuntu all that is needed?  That appears a little strange to me. Another problem is that the ISP's disk will not boot in ubuntu.  Again, your help will be appreciated.

---

### Post by Zelut on 2005-05-20
Its been my experience that ISP software is never needed.  If you're using a high-speed connection you shouldn't ever need it as you're always connected.  If you're using some type of dial up ISP that needs software (ie; juno, etc) then you may have a different problem.

As far as setting up the network mine has always worked right out of the box.  I use a cable modem with DHCP and ubuntu has always just detected that.  If you can give me your settings I may be able to help you more.  Are you using DHCP or Static?

---

