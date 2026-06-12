---
title: "Sudo - I just don't get it?"
date: 2008-09-17
forum: General Help
---

### Post by skeddon on 2008-09-17
Hi

I was wondering if someone can explain sudo to me in newbie terms?

I understand the idea of elevated privileges but on the other hand I don't see the point. There is only me uses my machine, and if someone else were to use it wouldn't they just type sudo anyway? If you say well there is a way to enable and disable sudo for users... well ok, but users that are sudo enabled, why can they just type in elevated mode?

Is sudo only any use if you get hacked? In which case, can't they just sudo there way under your account anyway?

Sorry, I just dont get it, if want to gedit a conf file, its because I want to edit it, so why make me type sudo in front of everything??

Thanks for explaining, I'm sure I just dont get it... :)

---

### Post by drs305 on 2008-09-17
Here is a good Ubuntu documentation entry on the subject:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by phidia on 2008-09-17
Would someone else also know your password? Sudo protects the operating system and provides security. You can do whatever you want to your personal files but the system files can only be edited/removed by the administrator.

---

### Post by snowpine on 2008-09-17
Hi Skeddon,

The short answer is: Not all Linux distros use sudo. Many of them use a separate root account instead. Choosing to disable root in favor of the sudo system was a conscious decision by the Ubuntu developers to make their distro special (or frustrating, depending on your point of view).

My personal opinion is that sudo helps a user who is transitioning from Windows understand which commands can break their computer and which are (relatively) harmless. That's reason enough for me, though I'm sure there are plenty of other arguments (i.e. security).

---

### Post by EmanresuusernamE on 2008-09-17
If you where always running around as root a command like:
rm -R /
Would kill your entire OS, period.  If you wheren't root when you ran that command, you'd only remove the information that you have access too, such as your home directory.  It can be an inconvenience, but it can also be a blessing.

---

### Post by forger on 2008-09-17
It's a bit similar to the "Cancel" or "Allow" windows vista asks you every now and then when you require administrator priliveges.

You login with your normal username, yet you keep your privileges when you want to use them. Only administrators can use sudo (in System > Administration > Users and Groups > Unlock > select user, click Properties and check out the administrative privileges).

The first user on Ubuntu is by default granted administrative privileges.

If you're a security freak, as soon as you use sudo, you can use **sudo -k** to break the privileges instantly.

---

### Post by skeddon on 2008-09-22
Thanks for all of your replies, I do understand to a point.

How do you say it anyway? Is it like "pseudo" or is it short for something, like "Super User Do" "su doo" or something?

Ok, maybe there is another way around this? I'm trying to do some network auditing. I have previously avoided using Linux which is an obvious choice for such work favouring Windows "ports". 

Basically I want to run my apps but I'd rather have an icon to fire up the tools, currently I have to do it all at command line. Its not such a big deal but installing WireShark, it gives me an Icon in "Applications" but its useless because you have to "sudo wireshark" in order to see the interfaces. Its the same with kismet and other apps.

It certainly looks impressive to colleagues that you can "sudo ifconfig ath0 up" and "sudo kismet" etc but for ease, i'd like to just click on an icon.

Also, while I'm on one, is there anyway to start a script from an icon? e.g. "bash reset_nic.sh"

Please no flaming, I'm just trying to get into Linux.

Thanks :)

---

### Post by RequinB4 on 2008-09-22
A root account, no matter how secure, is always less secure than a permissions system.  I really can't go into ALL the details.

Lets put it this way - you can go to any windows XP machine in existance that you don't own, you can type in 5 "/" and a few characters and wipe the entire hard drive.  And so can any program (coughvirii).  Ubuntu doesn't have this problem.

> **skeddon said:**
> Thanks for all of your replies, I do understand to a point.

How do you say it anyway? Is it like "pseudo" or is it short for something, like "Super User Do" "su doo" or something?

It's technically Super User Do, but everyone i've ever heard talking about it prounounces it "pseudo"

> 
Ok, maybe there is another way around this? I'm trying to do some network auditing. I have previously avoided using Linux which is an obvious choice for such work favouring Windows "ports". 

Basically I want to run my apps but I'd rather have an icon to fire up the tools, currently I have to do it all at command line. Its not such a big deal but installing WireShark, it gives me an Icon in "Applications" but its useless because you have to "sudo wireshark" in order to see the interfaces. Its the same with kismet and other apps.

It certainly looks impressive to colleagues that you can "sudo ifconfig ath0 up" and "sudo kismet" etc but for ease, i'd like to just click on an icon.


Right click on the menu icon and edit menus.  You can create an icon from there with any command.  Including
```

gksudo wireshark

```
or whatever.
(gksudo is used for graphical applications, don't ask me why but its a good reason)

> 
Also, while I'm on one, is there anyway to start a script from an icon? e.g. "bash reset_nic.sh"

Please no flaming, I'm just trying to get into Linux.

Thanks :)

Short answer is yes. 

Long (hitech) version you use whatever interpreter is appropriate for the script syntax.

Pretty much universally you can do
```

./script.sh
./script
./script.yayscript

```
Although the last command isn't exactly regular notation :P

Otherwise, most things you can use ```
sh script.sh
bash script.bash
php script.php
python code.py

```

If there is no extension you can use ./ or sh, they are by far the most common.

---

### Post by EmanresuusernamE on 2008-09-23
> **skeddon said:**
> How do you say it anyway? Is it like "pseudo" or is it short for something, like "Super User Do" "su doo" or something?

[http://www.google.com/search?hl=en&q=define%3Apseudo&btnG=Google+Search&aq=f&oq=]("http://www.google.com/search?hl=en&q=define%3Apseudo&btnG=Google+Search&aq=f&oq=")

Sudo, you're root, you're just not root.

---

### Post by bingoUV on 2008-09-23
> **skeddon said:**
> Thanks for all of your replies, I do understand to a point.

How do you say it anyway? Is it like "pseudo" or is it short for something, like "Super User Do" "su doo" or something?


My theory: "su" stands for switch user. It makes you the other user temporarily i.e. gives you a shell that is authenticated as the other user. sudo on the other hand, is typically just used to run a single command as another user, so su + "do this" = sudo. If you do not specify which user you want to switch to, both su and sudo assume root i.e. the super user. 

> **skeddon said:**
> 
Basically I want to run my apps but I'd rather have an icon to fire up the tools, currently I have to do it all at command line. Its not such a big deal but installing WireShark, it gives me an Icon in "Applications" but its useless because you have to "sudo wireshark" in order to see the interfaces. Its the same with kismet and other apps.


If the application is useless without super user privileges, it is a bug in packaging. Please file bugs on [http://launchpad.net](http://launchpad.net) for such applications that have an entry in the menu that does not assume super user privileges after asking you the password.

But maybe the application has some limited use without super user privileges. In such cases, it is a gray area about what entry to make in the menu, and we do not want to clutter the menus with 2 entries for each application. I guess this is the reason we don't have an menu entry for, say, sudo nautilus.

---

### Post by Bablefish on 2008-09-23
The short answer about giving someone your password is: Only if you trust them, not to screw up your computer. Let me tell you from some one who actually did. Screwing up a Linux OS is quite easy if you don't know what your doing.

---

### Post by FirstByté on 2009-12-16
> **bingoUV said:**
> 
**If the application is useless without super user privileges, it is a bug in packaging.** Please file bugs on [http://launchpad.net](http://launchpad.net) for such applications that have an entry in the menu that does not assume super user privileges after asking you the password.

***But maybe the application has some limited use without super user privileges.*** In such cases, it is a gray area about what entry to make in the menu, and we do not want to clutter the menus with 2 entries for each application. I guess this is the reason we don't have an menu entry for, say, sudo nautilus.

BingoUV,

Would it be appropriate for me to conclude of such with the **Wireshark** 'gksudo' menu, that once read 'Wireshark (Administrator)' or something on my Ubuntu 9.04, and now when I installed it via terminal I don't have the 'Wireshark (Administrator)' menu again.

I hate to be typing 
```
sudo wireshark
```
in the terminal every moment. What more are the use of a wireshark | Zenmap without sudo privileges? 

If there's no point bugging launchpad about it, please what would an appropriate shortcut command be? "gksudo sh <somthing something>"?

---

### Post by FirstByté on 2009-12-16
Sorry for not trying before disturbing the house.

I just Right-clicked on the '**Applications**'. Chose '**Edit Menu**'.

Scrolled down to my '**Internet**' menu, and spotted my **Wireshark**.

Created '**New Item**' and enter the following:

> Name: WireShark (Admin)
Command: gksudo /usr/bin/wireshark


Did the same for **Zenmap** too

Thanks :D

---

### Post by hashahzad on 2009-12-16
Hi all
I am a new user to Ubuntu. running it through USB drive and want to capture packets in wireless network. Sudo wireshark soleved the interface problems but cant see tcp, http,dns traffic in wireshark. 

if any body can help me out please
kind regards

---

### Post by ST3ALTHPSYCH0 on 2009-12-16
You could always place a launcher on the desktop with the run line reading
```

gksudo wireshark

```
then every time you used the launcher it would launch with root privileges.

I have to use launchers to get to my windows shares b/c of my network not playing completely nicely.

---

### Post by hashahzad on 2010-01-02
hi there
I have a problem with wireshark not showing http, tcp data packets. I am trying to do it at home. got wireless router connected to internet and trying to sniff other laptop with mine conneected to same access point. i have tried sudo, gksudo, did put nic in pormisc mode manually under ubuntu. sniffing my own laptop is allright but trying to get capture from second one doesn,t work. I just see NBNS, SSDP and DHCP kind of packets but no http , tcp  data packets are captured. some body help 
PLEASE.....

---

### Post by garryknight on 2010-01-02
> **RequinB4 said:**
> 
It's technically Super User Do
> **bingoUV said:**
> My theory: "su" stands for switch user.


It was originally "substitute user". Do 'info su' in a console for confirmation of this. Or, at least, what *I* call confirmation. :)

> **hashahzad said:**
> Hi all
I am a new user to Ubuntu. running it through USB drive and want to capture packets in wireless network. Sudo wireshark soleved the interface problems but cant see tcp, http,dns traffic in wireshark. 


Although you used sudo, this is a wireshark problem and really should be in a separate thread.

---

