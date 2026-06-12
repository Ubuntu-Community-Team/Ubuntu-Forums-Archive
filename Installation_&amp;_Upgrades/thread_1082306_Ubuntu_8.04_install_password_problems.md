---
title: "Ubuntu 8.04 install password problems"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by cdanderson04 on 2009-02-27
Hello!

I am new to Ubuntu and Installed it on my Windows Vista HDD as a 10 gig partition.  Anyways, I set up the isntallation correctly and followed all the instructions, but when I try to change anything that needs administration privileges my password is not accepted, yet it was accepted to log into Ubuntu for the first time.  I had a friend that knows about linux look at it and he assured me that I was the root.  Also, it was a fresh install.  So I really have no idea what is going on.  Either way.  Thanks in advance.

-Colin

---

### Post by taurus on 2009-02-27
One thing to keep in mind.  When you type in your password from a terminal, you won't see any display on the screen, not even *****, so make sure you enter the right one and hit Return.

---

### Post by cdanderson04 on 2009-02-27
Yeah.  I figured that.  I also tried caps lock when typing my password just in case i typed it in wrong.  But what bothers me is that I am able to log into in Ubuntu itself but I can't use any of the features that require authentication.  Even though I set up only one user.

Thanks for the reply though!

---

### Post by taurus on 2009-02-27
Is there an error message like you have entered a wrong password or you are not allowed to run that command because of root privilege?

What's the output of this command from a terminal?

```
id
```

---

### Post by joesdad on 2009-02-27
Sorry to jump on the bandwagon, but I've installed Ubantu 8.1 this evening and have the same difficulty.

When I type in the password (or anything else) in terminal it now just ignores me and gives another :~$ prompt

(BTW I'm trying to sort out the driver for my wireless broadband, that's why I'm "trying" to put my password in)

---

### Post by cdanderson04 on 2009-03-04
hey.  sorry about the delay

this is the result of typing ```
id
```

uid=1000(anderson) gid=1000(anderson) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(anderson)
anderson@anderson-laptop:~$

---

### Post by Carlos Sevcik on 2009-03-04
Collin, Are you using the sudo command?

---

### Post by cdanderson04 on 2009-03-04
no.  i am not using the sudo command.

when i use su it asks for my password and when i enter in the one i used to log onto ubuntu it does not accept it.  i basically can't do anything that requires me to authenticate.

---

### Post by Carlos Sevcik on 2009-03-04
That may be the problem, Ubuntu has no su officially. If you want to use su you first have to do

sudo passwd root

it will then ask for your passwd and let you create a root passwd after that you will be able to use su.

Usually you don't need su, you may use 

sudo -s

it will ask your passwd and after that you will have a root session.

Otherwise if you need to execute a command xxxxx as root you type it in a command window as:

sudo xxxxx

it will ask your passwd and that is it

---

### Post by Carlos Sevcik on 2009-03-04
One point more to use su you have to use the root passwd (NOT your own passwd) that you created as I said previously.

---

### Post by cdanderson04 on 2009-03-04
I tried that and here is the result:

```
anderson@anderson-laptop:~$ sudo passwd root
[sudo] password for anderson: 
Sorry, try again.
[sudo] password for anderson: 
Sorry, try again.
[sudo] password for anderson: 
Sorry, try again.
sudo: 3 incorrect password attempts
anderson@anderson-laptop:~$
```

---

### Post by csevcik on 2009-03-04
Was yours the first account created in your machine?

---

### Post by cdanderson04 on 2009-03-04
yes.  all i did was do a fresh install of ubuntu on a 10 gig partition so i could get more used to it.  when i went in to edit some of the setting it asked me for my password and i entered in the password that i set up my account with when i installed and it did not work.

---

### Post by cdanderson04 on 2009-03-04
so has anyone ever heard of this problem before? i would really like to get this working

---

### Post by avtolle on 2009-03-04
I'm going to suggest you consider resetting your password. See [http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword) for a good how-to.

One other thought: did you do a Wubi install, by any chance (although I don't think this makes any difference)?

---

### Post by cdanderson04 on 2009-03-04
What is a Wubi install?

---

### Post by cdanderson04 on 2009-03-04
woo!  i got it working after resetting my password.  thank you everyone for all the help!

---

### Post by avtolle on 2009-03-04
A Wubi install is installing Ubuntu "within Windows"; if you don't know what it is, a very large probability exists that you didn't install Ubuntu in this way. The reason for my question was your comment that you had allocated a 10gb partition for Ubuntu, which, while perhaps adequate, is a bit smaller than most do when installing Ubuntu directly to its own partition on a HDD, but seems to be a common size of installation selected by those using Wubi to install Ubuntu "within Windows". 

As I noted above, this is likely not relevant to your situation, as I am sure that the process outlined within the link to reset the password will work regardless of installation method.

---

