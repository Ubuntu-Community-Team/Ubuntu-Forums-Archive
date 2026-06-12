---
title: "Keyserver error"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by 311005901 on 2009-09-28
This happens all the time to me. :x 
[IMG]http://img9.imageshack.us/img9/9610/screenshotwn.png[/IMG]
[IMG]http://img340.imageshack.us/img340/7430/term.png[/IMG]

---

### Post by Partyboi2 on 2009-09-28
Sometimes the keyserver sites goes down, I would suggest trying at a later time.

---

### Post by bogdan.veringioiu on 2009-09-28
Hi.
This happens to me usually when I work behind my company firewall.
At home, I am able to run apt-key.
I don't know which ports are used for these operations.
Bogdan

---

### Post by 311005901 on 2009-09-29
Day 2. Down again. :mad:

[IMG]http://img169.imageshack.us/img169/8409/screenshotzo.png[/IMG]

---

### Post by jimwhitend on 2009-09-30
Is anyone else bothered by the consistent failure of keyserver.ubuntu.com? It seems like a big deal, but the apparent lack of uproar indicates to me that there must be a workaround. So what's the workaround? Just asking! Thanks.
-JimW](*,)

---

### Post by 311005901 on 2009-10-05
I agree! I'm wondering if this problem is bothering anybody else...

---

### Post by snapsta on 2009-10-11
Having the same problem. 

I am trying to upgrade to subversion 1.6 in Jaunty and found a solution here [http://dhydrated.wordpress.com/2009/09/23/install-subversion-1-6-in-ubuntu/]("http://dhydrated.wordpress.com/2009/09/23/install-subversion-1-6-in-ubuntu/"), which includes the command

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 413576CB

I then went on to find this archived thread [http://ubuntuforums.org/archive/index.php/t-1243958.html]("http://ubuntuforums.org/archive/index.php/t-1243958.html"), which gives an alternative method by going to [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x71346C8340130828]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x71346C8340130828").  When I tried it a home, the webpage still timed out on me but here at work it returned a public server key (I am in Australia so my working hours may be a better time to try).

So my question is what is the significance of the '413576CB' at the end of the apt-key command?  Is this some random string of hex, or does it have some special significance? If so can I use key returned from the above URL in place of the command above?

Cheers,

Tom

---

### Post by Partyboi2 on 2009-10-11
Each ppa has a different [[COLOR=Blue]gpg key[/COLOR]]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto") so you will need to use the correct key. The one in the link you provided is not the one you need. So go [[COLOR=Blue]here[/COLOR]]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6298AD34413576CB") and copy and post the contents into gedit (Applications>Accessories>Terminal) and save it. Then  open Software Sources and under the 'Authentication' tab choose to import and import the key. Then refresh the package list.

---

### Post by mattgaunt on 2009-10-25
Is there still no fix for this? I'm fairly surprised that I'm still getting this issue after a couple of weeks of getting this error.

I know there is a bug report here - [https://bugs.launchpad.net/ubuntu-website/+bug/435193](https://bugs.launchpad.net/ubuntu-website/+bug/435193) BUT it's filed under 'Ubuntu Website' when it's quite a big Ubuntu problem since this is the proposed method of adding repo's now.

Could it have anything to do with a firewall on my router or on Ubuntu that could be preventing the connection?

Cheers,
Matt

---

