---
title: "gnome power manager not installed correctly"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by cooltarlee on 2009-04-05
error occured suddenly at startup 

--------------------------------------------------------------------------------

an error occured suddenly at start up . the error is " an error occured while loading or saving configuration information for update-notifier. some of your configuration settings may not work properly".

DETAILS FOR ERROR:-
failed to construct configuration server .some possible causes are that you need to evolve tcp/ip networking for orbit or you have stale nfs locks due to a system crash. details1- could not send message to gconf deamon. message did not recieve a reply.
(timeout by message bus).

it is also showing installation error which is-"configuration defaults for gnome power manager has not been installed correctly.

what should i do now to solve this problem. now i can see just a black screen. please tell me an appropriate solution

---

### Post by zigga15 on 2009-04-05
> **cooltarlee said:**
> error occured suddenly at startup 

--------------------------------------------------------------------------------

an error occured suddenly at start up . the error is " an error occured while loading or saving configuration information for update-notifier. some of your configuration settings may not work properly".

DETAILS FOR ERROR:-
failed to construct configuration server .some possible causes are that you need to evolve tcp/ip networking for orbit or you have stale nfs locks due to a system crash. details1- could not send message to gconf deamon. message did not recieve a reply.
(timeout by message bus).

it is also showing installation error which is-"configuration defaults for gnome power manager has not been installed correctly.

what should i do now to solve this problem. now i can see just a black screen. please tell me an appropriate solution

boot up in terminal (press ctrl+alt+f3 at the blank screen) or press escape when grub loads up so you can boot in safe mode, or boot in terminal.

If you can manage to get a terminal use:

sudo apt-get remove powermgmt-base
sudo apt-get install powermgmt-base

Make sure that you actually have an internet connection here. so you can get the package again. do this with iwconfig or ping [http://www.google.com](http://www.google.com)

---

### Post by cooltarlee on 2009-04-05
> **zigga15 said:**
> boot up in terminal (press ctrl+alt+f3 at the blank screen) or press escape when grub loads up so you can boot in safe mode, or boot in terminal.

If you can manage to get a terminal use:

sudo apt-get remove powermgmt-base
sudo apt-get install powermgmt-base

Make sure that you actually have an internet connection here. so you can get the package again. do this with iwconfig or ping [http://www.google.com](http://www.google.com)

ihave done all the procedure but now its showing-"err http:/us.archieve.ubuntu.com/ubuntu/pool/main/p/powermgmt-baseowermgmt_base_1.30 could not resolve us.archieve.ubuntu.com.

failed to fetch http:/us.archieve.ubuntu.com/ubuntu/pool/main/p/powermgmt-baseowermgmt_base_1.30_,i386.deb.could not resolve'us.archieve.ubuntu .com"

i think my internet connection is not working what should i do now . before the occurence of this error my internet conne ction was working .

wot shud i do now .PLEASE HELP ME.

---

### Post by infallible on 2009-04-07
I came across your thread while searching for the solution to a similar problem, and thought I would share what I've learned (or at least my theory.) 

The system crashed, and gconf didn't close out properly. It has a function that locks critical files, etc for the use of the individual user. The crash caused them to remain locked, and therefore inaccessible.  ctrl-alt-1 brings up a terminal, ctrl-alt-7 brings up  a gnome (windowed) session. To remedy this, try typing ```
 mv ~/.gconfd/saved_state saved_state.old

``` into your terminal and reboot, or perhaps its only necessary to ctrl-alt-backspace and log in again.   It was either this that fixed it, or "dpkg-reconfigure gconf<tab><tab>" and reconfiguring everything that started with gconf. either way, these steps allowed me to log in again.

best of luck,
Pete

---

### Post by cigtoxdoc on 2010-09-04
During a recent update on 10.04, there was an unknown problem and the system did a hard drive check before rebooting correctly.  My login (Administrator) worked correctly, but my Son's login came up with the Gnome power manager not installed correctly error leaving just the background and nothing working.  Here is the fix.

Type CTRL-ALT-F1 to get to a prompt.
login with the user's name and password of the affected account
Type the following phrase

mv .gconfd/saved_state saved_state.old

REBOOT and login to the affected account.  Problem should be fixed.

John

---

### Post by msboston01 on 2010-09-21
I have the same error and I confirm cigtoxdoc's assessment. I tried the mv solution below, unfortunately I get ```
mv: cannot stat `.gconfd/saved_state': No such file or directory
```

Any suggestions?

---

### Post by msboston01 on 2010-09-21
Well I tried a few thing and it turns out that my HDD is totally full which is super duper weird as I was running on 5 GB out of 13 GB... 

I did the update from 9.1 to 10.04 a month ago or so.. could this have anything to do with this?

---

### Post by PeterChrisF on 2010-12-02
> **msboston01 said:**
> Well I tried a few thing and it turns out that my HDD is totally full which is super duper weird as I was running on 5 GB out of 13 GB... 

I did the update from 9.1 to 10.04 a month ago or so.. could this have anything to do with this?

Same problem here.  Except that I know I had 55 GB free, and for some reason the disk was full.  This produced the gnome power manager login error.

To check your disk, login to the terminal and type ```
df
```

I deleted some stuff so I can log in normally now.  But I still have no idea what suddenly took all the disk space or how to find it.

---

### Post by WA4MOE on 2010-12-13
I did the update from 9.1 to 10.04 a month ago or so.. could this have anything to do with this?[/QUOTE]

Well, I also did an upgrade to 10.04 and have the Gnomer Power Manager not configured problem. I have tried to boot to CD ROM but it will not recognize it. I tried to use the ESC to get to a recovery and then use the prompt but then the keyboard input only is successful on about 2/3 of the letter inputs.

It is totally frustrating. I am about to try to go back to a windows environment but that didn't seem be working with the inability to boot from CD. It's been over a month and all I have tried is futile.

HELP!

---

### Post by DevinAdkins on 2010-12-29
ok so i happened to install a usual update from ubuntu one day and it was fine until i rebooted it ... now when i load my computer the login screen liiks weird and in the top right it says "The Configuration defaults for GNOME power manger have not been installed correctly." im new to ubuntu and i have version 10. i need a way to fix this so i can login and use the desk top because all i care about is saving my music. Pleas it would be nice if i could get some help that works.. i have tied some things but it just wont work.

---

### Post by llspence on 2011-01-02
I can confirm that "mv .gconfd/saved_state saved_state.old" worked for me after going through the other solutions suggested here: [http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/)

In short, this error usually seems to be caused by root running out of space, in which case one of the following fixes should work (just press Ctrl+Alt+F1 to get the terminal from your login screen):


[LIST]
[*]clear out some disk space using "sudo apt-get clean" or move some files onto another drive or partition
[*]chmod /tmp to 0777 using "chmod 0777 /tmp"
[*]reconfigure your packages using "sudo dpkg --configure -a"
[*]manually create the default gconf folder using "mkdir /var/lib/gconf/default"
[*]reinstall Ubuntu desktop with "sudo apt-get --reinstall install ubuntu-desktop" (which may change or remove some of your settings)
[/LIST]

If neither of the above works (as in my case), the problem is likely to have been caused by gconf locking critical files after a crash as suggested by infallible, in which case "mv .gconfd/saved_state saved_state.old" should fix it.

---

### Post by FreeMan0110 on 2011-03-10
> **infallible said:**
> ```
 mv ~/.gconfd/saved_state saved_state.old

``` into your terminal and reboot 

  
This command helped me. I had same problem in office laptop.
Even " ~ " is also necessary. When this is missed, the following error comes up. 
```
mv: cannot stat `.gconfd/saved_state': No such file or directory
```
.

---

