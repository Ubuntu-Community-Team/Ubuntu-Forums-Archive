---
title: "Help needed: X won't start"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by neocortex on 2006-11-24
Hello,
Yesterday, after I did update of my Dapper, I did something stupid: changed source.list of my repositories, from 'dapper' to 'edgy', and tried to upgrade vim, some of its addins, like vim-latexsuite, and cream. I did that following some comments/advices on the cream-list at sourceforge.net, because my cream didn't started vim-latexsuite automatically. Being the fact that Dapper's vim, vim-gnome, cream and vim-latexsuite are not the latest versions, I saw that Edgy's are, and tried to upgrade from its repositories. I didn't carefully checked all the dependencies (and only vim asked them), and just let everything be done. Now, my Dapper cannot start X. I tried reinstalling fglrx-driver (I have ATI on my HP nx8220 laptop), but without success.
Please, help me! How to fix the problem?

Sincerely,
Petar

---

### Post by amp_man on 2006-11-24
hmm...what happens if you edit xorg.conf and use the "ati" or "radeon" driver instead? also, did you get the updated kernel as well, and an updated restricted modules? and did you do a dist-upgrade or just upgrade?

---

### Post by neocortex on 2006-11-24
what happens if you edit xorg.conf and use the "ati" or "radeon" driver instead?
> I didn't try to edit xorg.conf.

also, did you get the updated kernel as well, and an updated restricted modules?
> I think, yes.

and did you do a dist-upgrade or just upgrade?
> No, just upgrade, and only for vim, cream, and addons I changed repositories from Dapper's to Edgy's.

Thanks for helping me! I am really desperate: lots of work that must wait ... :( 
Petar

---

### Post by Sandriman on 2006-11-24
Ok, first of all, try:

```
sudo apt-get dist-upgrade
```

Then run:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And after that, modify your */etc/X11/xorg.conf* and find 

```

Section "Device"

and from there,

Driver "something"

and change it to either

Driver "fglrx"

or

Driver "ati"


```

---

### Post by neocortex on 2006-11-24
Thanks Sandriman!
But, if I do:
```
sudo apt-get dist-upgrade
```
I shall go from Dapper to Edgy. Am I right?
Then, since I use dial-up, can I do upgrade from Edgy's CD?
Also, can I downgrade? How?
My Dapper is very nicely fixed. I am hesitating to upgrade to Edgy, because I am a bit afraid that I shall (a) lose something and/or (b) finish with lot of garbage.

Sincerely,
Petar

---

### Post by Sandriman on 2006-11-25
Hey,

got your mail too. Don't worry. *dist-upgrade* doesn't upgrade to Edgy unless you switch all *'dapper'* words in **/etc/apt/sources.list** to *'edgy'*.
*dist-upgrade* just upgrades your current distribution's packages to latest Dapper packages.

You could try the **dpkg-reconfigure**-approach too without *dist-upgrade*.

Give it a go, if at all possible and then let's get back to it. :)

---

