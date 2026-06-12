---
title: "upgrades unavailable"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by tituspurdin on 2009-05-25
I have been using Ubuntu successfully on several machines for some time.
On this laptop, it tells me (quite regularly) that there are upgrades
available.  However, when I try to install them, it tells me that they are
unavailable ("W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/udev/libvolume-id0_113-0ubuntu17.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/udev/libvolume-id0_113-0ubuntu17.2_i386.deb)
  404 Not Found")

I have reset the repositories, reloaded, done everything I can thnk of.  I
would appreciate some insight.  THanks.


Titus sends

---

### Post by MarcusCarabas on 2009-05-27
I'm having the same problem... I tried to install some packages using "Add/Remove Applications" and ended up with "Failed to Fetch" messages of the following type:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/r/ruby-gnome2/<NAME OF FILE> ruby1.8_0.16.0-3ubuntu1_i386.deb
  404 Not Found [IP: 91.189.88.140 80]

I tried using Synaptic and ended up the same problem

So does anyone know what's going on? I've never had this problem before ... 

Any help would be appreciated

thank you,
Marcus Carabas

---

### Post by _Purple_ on 2009-05-27
Go to System > Administration > Software Sources and try to change to a different server and see if it works.

---

### Post by tituspurdin on 2009-05-27
I have tried several different servers: mains server, several USA servers;
but nothing changed the outcome.

Titus sends

---

### Post by _Purple_ on 2009-05-27
> **tituspurdin said:**
> I have tried several different servers: mains server, several USA servers;
but nothing changed the outcome.

Titus sends

Can you please type the following command in terminal and post the contents
```
gedit /etc/apt/sources.list
```

---

### Post by kruegger on 2009-05-27
Yes, I suspect Gutsy has run out of support. No repo's available from any server mirror.

I have tried to install several packages for a week (without luck) and things haven't changed so far.

It's just as well I made a Gutsy backup. Too many bad experiences.:biggrin:

What d'you reckon guys?. .Am I wrong?. I need reassurance, please. I'm the insecure type.;)

---

### Post by _Purple_ on 2009-05-27
> **kruegger said:**
> Yes, I suspect it is an Ubuntu Project major failure. No repo's available from any server mirror.

I have tried to install several packages for a week (without luck) and things haven't changed so far.

It's just as well I made a Gutsy backup. Too many bad experiences.:biggrin:

What d'you reckon guys?. .Am I wrong?. I need reassurance, please. I'm the insecure type.;)

If you are still using Gutsy, by now the repositories must have closed or will close soon as it has reached end of life. I suggest you to upgrade to the LTS (8.04) or 9.04.

---

### Post by kruegger on 2009-05-27
Thanks_PURPLE_. I needed it.:D

That was the problem for tituspurdin and marcarafe, as well. 

So, let's upgrade.
 
See you.

---

### Post by _Purple_ on 2009-05-27
> **kruegger said:**
> Thanks_PURPLE_. I needed it.:D

That was the problem for tituspurdin and marcarafe, as well. 

So, let's upgrade.
 
See you.

You are welcome. :)
The profile info says MarcusCarabas is using Gutsy but there is nothing in the OP's profile info.

---

### Post by tituspurdin on 2009-05-28
I will try (and post the results of) 'gedit /etc/apt/sources.list'
command later today.  This problem is on a laptop which, as folks
have observed, is running Gutsy.  I don't have the laptop with me
today.  But I will be reunited with it later.  The laptop was
purchased from Dell with Ubuntu installed.  It runs like a champ
and I am reluctant to upgrade.  Of course I must eventually; but
upgrading desktop machines at home to Hardy did cause me some
grief.

Titus sends

---

### Post by _Purple_ on 2009-05-28
> **tituspurdin said:**
> I will try (and post the results of) 'gedit /etc/apt/sources.list'
command later today.  This problem is on a laptop which, as folks
have observed, is running Gutsy.  I don't have the laptop with me
today.  But I will be reunited with it later.  The laptop was
purchased from Dell with Ubuntu installed.  It runs like a champ
and I am reluctant to upgrade.  Of course I must eventually; but
upgrading desktop machines at home to Hardy did cause me some
grief.

Titus sends

That explains it. The sources.list is not required if you have Gutsy installed in that machine. Just wanted to make sure. Your only option is to upgrade. The repositories are not available for Gutsy anymore. If you had problems with Hardy, may be you can try a live CD of Jaunty and see if it works for you and then upgrade to it. You can try Hardy too because the issues you had with your desktop might be related to the hardware. The advantage of using Hardy is it will be supported for a longer time.

---

### Post by tituspurdin on 2009-05-29
Here is the output of the 'gedit /etc/apt/sources.list' command:

------------------------------cut here--------------------------------


# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties

---

### Post by _Purple_ on 2009-05-29
You do not have the security and updates in the sources list but that does not make any difference as the repositories of Gutsy must be closed by now. Please upgrade to the LTS (8.04) or the latest version which is 9.04.

---

### Post by tituspurdin on 2009-06-02
Okay, I upgraded the laptop.  It solved the problem---though the upgrade
was not without its own problems.  And in the end, upgrading because
the Ubuntu folk 'want' me to seems like a rather MicroSoftian solution.


Titus sends

---

### Post by TheNosh on 2009-06-02
> **tituspurdin said:**
>  And in the end, upgrading because
the Ubuntu folk 'want' me to seems like a rather MicroSoftian solution.

canonical is only going to host so many repositories, you can run whatever verion you want and the fact that they won't be officialy supported forever seems pretty fair to me

---

### Post by _Purple_ on 2009-06-02
If you install the LTS, it is usually supported for 3 years.

---

