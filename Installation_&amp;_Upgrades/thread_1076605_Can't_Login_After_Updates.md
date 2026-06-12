---
title: "Can't Login After Updates"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by robertv on 2009-02-21
Carried out some updates today, and there was an error. The two suggested methods to fix it (running dpkg --configure -a and apt-get -f install) didn't do anything productive. After around an hour, I suddenly got a small popup from X (not styled as KDE) complaining it couldn't find something (I didn't get time to see what) before being forcibly logged out. Now all that happens is I get the login screen, and when I attempt to login I just get a black screen, then the login screen again.

Adept itself provided little useful information during the upgrade, although afterwards I spotted a number of packages marked as broken.

I'm typing this from a Live CD, and any help is greatly appreciated. If anyone has any way to get some helpful information, or ways to fix this, then let me know. Otherwise I'll just have to reinstall I guess.

---

### Post by robertv on 2009-02-22
I have also tried logging in using the "Failsafe" option on the login screen. This is not as failsafe as it claims - it does exactly the same as the normal option. Flash of a black screen, then straight back to the login screen.

---

### Post by Pete051 on 2009-02-22
Same problem here no kde and no network connection and only windowmaker running looks like we have major bug here

---

### Post by Pete051 on 2009-02-22
Ok problem solved by connecting by ethernet and running apt-get update and apt-get install kde, it seems to have been a bug with adept.
Pete

---

### Post by robertv on 2009-02-22
Hasn't fixed it for me. I've reinstalled Kubuntu and I now get a quick error from X flash up during the black screen, before being thrown back to the login screen. I have kept the same home directory, so I assume there was some combination between files in my home directory and the rest of the system.

Again, any help would be nice.

---

### Post by tommcd on 2009-02-22
> **robertv said:**
>  I've reinstalled Kubuntu and I now get a quick error from X flash up during the black screen, before being thrown back to the login screen. I have kept the same home directory, so I assume there was some combination between files in my home directory and the rest of the system.


If you have reinstalled Kubuntu from scratch, and you still can't login, then there may be a problem with the .kde directory in your home directory. Try booting to recovery mode and renaming the .kde directory in your home directory to .kde.bak. Also rename any directory in you home directory that has .kde* in it (there may be more than one, I'm not sure, as I don't run KDE). Then reboot and try to login. KDE will create a new, pristine .kde directory when you login.

---

### Post by Icefalls on 2009-02-22
Hey,

I seem to have the same problem. Made upgrades yesterday and had some trouble to complete them using adept. I had to use apt-get in the terminal to complete the update.

When I turned on the computer this morning, the xserver would not start.Kubuntu desktop manager does not start after logging in .  I found the following entry online about a similar problem after the update.

[http://www.linux-archive.org/kubuntu-user/249047-latest-kubuntu-update.html](http://www.linux-archive.org/kubuntu-user/249047-latest-kubuntu-update.html)

After checking with aptitude it seems there are some packages missing relating to Kubuntu desktop but i am unable to install them. apt-get update returns failed connections to the repositories online. 

I have checked the connection from the computer using the terminal and it seems there is no connection. I know the actual connection works because im using it with a laptop at the moment.

It seems to be a double edged problem. I need the internet to sort out the xserver problem, but there is no conncetion for me to use aptitude...

Does anyone have a suggestion, im not an experienced linux user and im pulling my hair out

---

### Post by bikerelc on 2009-02-22
I have the same basic problem.  I tried to login using the failsafe and got an error message about not having an xserver emulator installed.  When trying to boot using the default I go straight to a black screen with my cursor.  Also it should be noted that I only have internet access via a wireless connection.  Another important thing that I noticed was when the updates were occurring I noticed an update for the Fglrx driver which had caused me problems in the past, mostly the inability to use the FGLRX drivers.

---

### Post by Icefalls on 2009-02-23
Hello again,

Im still grapling with this problem. Found another link to a similar problem caused by a language pack.

[http://www.linuxquestions.org/questions/ubuntu-63/kde-wont-load-after-apt-get-update-kubuntu-x8664-620882/](http://www.linuxquestions.org/questions/ubuntu-63/kde-wont-load-after-apt-get-update-kubuntu-x8664-620882/)

The problem is i am unable to run any of the commands using the terminal. I think this is because the computer cannot/will not access the internet to check the sources.

Has anyone else had any luck?

---

### Post by Pete051 on 2009-02-23
I think the only solution to the connection problem is to connect with an ethernet cable, not wireless once you have updated with apt-get everything should be hunky dory :)

---

### Post by tommcd on 2009-02-24
> **Icefalls said:**
> 
When I turned on the computer this morning, the xserver would not start.Kubuntu desktop manager does not start after logging in .  I found the following entry online about a similar problem after the update.

[http://www.linux-archive.org/kubuntu-user/249047-latest-kubuntu-update.html](http://www.linux-archive.org/kubuntu-user/249047-latest-kubuntu-update.html)

After checking with aptitude it seems there are some packages missing relating to Kubuntu desktop but i am unable to install them. apt-get update returns failed connections to the repositories online. 

I have checked the connection from the computer using the terminal and it seems there is no connection. I know the actual connection works because im using it with a laptop at the moment.


1. It seems unlikely that you would have internet access from Firefox and not from the terminal. To verify that you have internet access from terminal do this:
```
ping www.google.com
```
You should get something like this:
```
bash-3.1$ ping www.google.com
PING www.l.google.com (64.233.169.99) 56(84) bytes of data.
64 bytes from yo-in-f99.google.com (64.233.169.99): icmp_seq=1 ttl=241 time=20.3 ms
64 bytes from yo-in-f99.google.com (64.233.169.99): icmp_seq=2 ttl=241 time=16.6 ms ......

```
To stop it hit: **ctrl c** 

To fix your KDE problem, first backup your .kde directory in your home directory:
```
mv ~/.kde ~/.kde.bak
```
Then run:
```
sudo dpkg -configure -a
sudo apt-get install -f
```
Then reboot. If that does not fix it, then backup your .kde directory again and run:
```
sudo apt-get install --reinstall kubuntu-desktop
```
If you have problems with any of this, post the output of these commands.

---

### Post by Mujaheiden on 2009-03-18
I have the same issue, but then on ubuntu, 8.10. none of your solutions worked for me so im starting a new [thread]("http://ubuntuforums.org/showthread.php?p=6916073").

---

