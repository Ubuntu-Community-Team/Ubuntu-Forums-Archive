---
title: "Help please, for absolute ubuntu beginner"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by TrevG on 2009-07-17
Hi,
This is no doubt a stupid question with an obvious answer but rather than mess round I thought I'd ask.
I have downloaded and installed ubuntu on a friend's recommendation. On the first start after installation it is asking me for a user name and password.
There was definitely nowhere in the installation process where I was asked to set up a user name and password.
So of course I can't get into the program.
I would appreciate any advice. And yes, I'll accept any ribbing if I've done something stupid.
FYI. I'm reasonably computer literate, have been installing my own operating systems and various software for years, so I am at a loss to explain this.

---

### Post by nikhilbhardwaj on 2009-07-17
when you install
it asks for a username and password
its not possible for you to miss or skip that 

it is possible to reset your password with a live cd

---

### Post by TrevG on 2009-07-17
I'll try that thanks.
You are just going to have to accept I did not get asked for a user name and password.

---

### Post by AndyCee on 2009-07-17
> **TrevG said:**
> I'll try that thanks.
You are just going to have to accept...

Lol, it's all good. Not supposed to happen, but there you go.

What I did when given no password or username on a pre-install, was to go to the GRUB boot menu (escape if it doesn't show up) and enter "recovery mode", which is essentially a root account.

From there you can add a user account. If it's command-line only (I can't remember at this point) the command is:

```
useradd *<your username>*
```

and you will be prompted for a password. Reboot the machine or type "sudo reboot".

---

### Post by TrevG on 2009-07-17
I'll try that thanks.
You are just going to have to accept I did not get asked for a user name and password.

I've now seen the screen you're referring to. Definitely did not come up first time through. However, there were some errors in downloading. Had to burn a second disk to get it to work and still get some odd error messages in setting up, but works.
And I've now set a user name and password.
The same as I use for any other programs - but they didn't work on ubuntu when it asked me for them, which would seem to back up what I said earlier.
We'll see what happens this time.
Thanks again.

---

