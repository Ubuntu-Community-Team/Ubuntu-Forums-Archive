---
title: "Compaq v2000 Help"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by Priapus891 on 2007-05-09
Hey guys

I just switch set up my laptop to dual boot Windows XP Pro and Ubuntu 7.04. And I must say, I am amazed as to how much better this runs compared to Windows XP. 

Heres my problem though, I cant get my wireless card to work. Its a Broadcom BCM4318 AirForce One 54g 802.11g Wireless LAN Controller (rev 02).

I found all kinds of ways that people got it to work on there laptops, but everytime i go to install something or run a ,deb package to install the drivers i get this error:

> 
**FAILED to run gdebi-gtk '--non-interactive' 'home/adam/Desktop/bcm43xx_compwiz18.1-all.deb' as user root. **

The Underlying authorization mechanism (sudo) does not allow you to run this program. Contact your system administrator.


This is what I am currently trying to do btw: [http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5)
And this is one from this site that I tried to do but could not get it to work: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

Another thing is what that quote is. When i set up ubuntu I set my password and that was the password I keep trying to use. Is there anyway I can go and check what the password is or even change it. And before you say to go to system -> administration -> users and groups, that does not work. I don't know why. But I'm trying to solve one problem at a time.

Thnx,

adam

---

### Post by misfitpierce on 2007-05-09
SIMPLE! I have a similar model to the V2000 but in same categorie with same wireless....

Simply do this while connected through ethernet to internet!

Open console....
Type sudo apt-get update
Type sudo apt-get install bcm43xx-fwcutter
It will begin download then install and will ask if you would like to extract firmware....
Click Yes
Allow finish....
COMPLETE!

Within a few seconds wireless light should turn on and you can take out ethernet cord.... Should be fine and working now!

That guide was made for edgy and your using Fesity 7.04... It's just simpler this way :)

---

### Post by Priapus891 on 2007-05-09
Ok, I just did the first part "Type sudo apt-get update" and that worked.

Then I went on to the second comand "Type sudo apt-get install bcm43xx-fwcutter" and I keep getting this:

```

root@localhost:/home/adam# sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcm43xx-fwcutter

```

Is there something I need to change in order for it to do that right?

---

### Post by Priapus891 on 2007-05-09
nice... i got it to work with this: [https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html#install-deb](https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html#install-deb)

just using a .deb file through the root account on the terminal

---

