---
title: "No volume control gstreamer plugins and/or devices found"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by iBuck on 2007-10-25
It was incredibly weird... My sound was working for me at about 4PM today, right before I left for work. Then I came home about 4 hours later and all of a sudden, my sound is gone. This is one of the errors I get:
> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

I ran lspci -v | grep Audio and it outputs:
```
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)

```

so ubuntu is recognizing my sound card, but must not be loading any drivers. I just don't understand how the sound just stopped working. No one else uses this computer except for me, so it layed dormant for 4 hours and magically stopped producing sound.

I've looked around at other threads and can't find a solution. I tried reinstalling ALSA too by running:
```
sudo aptitude purge linux-sound-base alsa-base alsa-utils
sudo aptitude install linux-sound-base alsa-base alsa-utils gdm ubuntu-deskop
```

but that was no help at all. I've rebooted and still have nothing. This is my second day running 7.10 after my 3rd switch from windows Vista. I don't want to go back to Vista, so i'm really hoping I can fix all my linux problems before I get too frustrated again.

---

### Post by scrooge_74 on 2007-10-25
from a terminal

sudo sh /etc/init.d/alsa reload (or is unload and then do a load)
sudo sh /etc/init.d/alsa-util stop and then start

---

### Post by dysonsphere23 on 2007-10-26
Wierd for me too.

Everything was working fine then I shut down my laptop after work restarted at home and now volume control won't work, still after start again this morning.  The sound card is functional, I am getting sound, but when I try to open the volume control from the pannel I get that same message:

"No volume control GStreamer plugins and/or devices found."

and

"The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I tried reinstalling all the gstreamer stuff from Symantec and nothing.

When I type " sudo sh /etc/init.d/alsa reload" in terminal I get:

"sh: Can't open /etc/init.d/alsa"

I find it odd that this hust happend between a shut down and restart, what gives?

Oh yah, also my Exaile player won't start since this problem.  Whn I try opening in terminal it gives some output about not finding playbin.  Tried uninstall and reinstall, no help.

Thanks in advance for any advice/insight.

---

### Post by iBuck on 2007-10-26
> **scrooge_74 said:**
> from a terminal

sudo sh /etc/init.d/alsa reload (or is unload and then do a load)
sudo sh /etc/init.d/alsa-util stop and then start

I'm getting:
> sh: Can't open /etc/init.d/alsa

When I try to do those commands, so no luck there.

To the above guy: Something could have happened to you during startup possibly, my situation seems ridiculous, I left my computer for 4 hours, came back and the sound was gone. Ridiculous I tell you.

---

### Post by scrooge_74 on 2007-10-26
check what you have in /etc/init.d maybe is not alsa, but something different.  I am using Debian Etch so things are slightly different

---

### Post by iBuck on 2007-10-26
> **scrooge_74 said:**
> check what you have in /etc/init.d maybe is not alsa, but something different.  I am using Debian Etch so things are slightly different

mine was called alsa-utils, so I just needed to add the s at the end. 

I can start and stop alsa but using
>  sudo sh /etc/init.d/alsa-utils start
 sudo sh /etc/init.d/alsa-utils stop


but I still get " sudo sh /etc/init.d/alsa-utils start" when trying to run
>  sudo sh /etc/init.d/alsa-utils start

I looked in my /etc/init.d folder and found alsa-utils, but nothing just named alsa. I don't know what that means... maybe i'm missing it?

---

### Post by scrooge_74 on 2007-10-26
Yes alsa-utils would be in your case the correct statement, you first give the command stop and then the command start.

sudo sh /etc/init.d/alsa-utils stop
sudo sh /etc/init.d/alsa-utils start

In Etch I have both alsa and alsa-utils

---

### Post by teqagogo on 2007-10-26
Hi I got similar problem after upgrading to 7.10.

I found this and was able to fixed it as follow:

1/ update the default kernel options into /boot/grub/menu.lst
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0baea18f-2277-494d-8c62-95c4fcbdef86 ro quiet splash pci=assign-busses acpi=off noapic nolapic irqpoll=noacpi

2/ reconfigure the alsa module even if you already reinstalled it
cd /usr/src
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa
sudo shutdown -r now

---

### Post by professor fate on 2007-10-27
> **teqagogo said:**
> Hi I got similar problem after upgrading to 7.10.

I found this and was able to fixed it as follow:

1/ update the default kernel options into /boot/grub/menu.lst
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0baea18f-2277-494d-8c62-95c4fcbdef86 ro quiet splash pci=assign-busses acpi=off noapic nolapic irqpoll=noacpi

2/ reconfigure the alsa module even if you already reinstalled it
cd /usr/src
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa
sudo shutdown -r now

I'm using a Vostro 1400 and am having the same problem  What's your sound card?

---

### Post by eamann on 2007-12-04
Hello!

I too have the same problem. Apparently it is due to "permissions". Further information on [http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)

However, when I tried the solution proposed by Kamil
 chmod -R a+rwx /dev/snd
my terminal replied: su: invalid option -- R

How do I get round that?

---

### Post by scrooge_74 on 2007-12-04
type sudo in front of the command

---

### Post by eamann on 2007-12-06
Hello!

Try the very simple solution proposed by LinuxTechie at

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

It worked for me.

Best of luck!

---

### Post by dsplabs on 2007-12-10
> **eamann said:**
> Hello!

I too have the same problem. Apparently it is due to "permissions". Further information on [http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)

However, when I tried the solution proposed by Kamil
 chmod -R a+rwx /dev/snd
my terminal replied: su: invalid option -- R

How do I get round that?

Hi eamann,

In order to give read and write permissions to all users you need to have root permissions, otherwise the following error will occur:

    **chmod -R a+rwx /dev/snd**
    chmod: changing permissions of `/dev/snd': Operation not permitted

To get root user permissions under Linux (Ubuntu specific approach is given later on) you could:
 
*a)* login as root from the terminal, i.e. press Alt+Ctrl+F1, enter root as username and then the root password, then you would run 

    **chmod -R a+rwx /dev/snd**

and then after logging out you can get back to the X window system by pressing Alt+Ctrl+F7;

*b)* you could use the **su** command, however _not_ like this:

    **su chmod -R a+rwx /dev/snd**
    su: invalid option -- R
    Try `su --help' for more information.

but like this:

    **su**
    Password: ******

enter the root password at the '*Password: *' prompt above, then change permissions:

    **chmod -R a+rwx /dev/snd**

then exit;

*c)* or simply use the **sudo** command as follows:

    **sudo chmod -R a+rwx /dev/snd**
    root's password: ******

Enter the root password, this time at the '*root's password: *' prompt.

Under Ubuntu you are probably best to use option (c) which for user 'kamil' looks something like this:

    **sudo chmod -R a+rwx /dev/snd**
    [sudo] password for kamil: *******

Note that the prompt above is changed: under Ubuntu you will be asked for the password of the current user (and not the root user). If you want to read up more on this, then look-up sudoers in the man pages:

    **man sudoers**


Hope this helps,

Kamil

---

### Post by biddy on 2008-02-04
Hi I have the same problem with my sound, no sound for music, video or internet, this happened sunday afternoon UTC but when i bootup machine you can hear the ubuntu music it gives you when you logon.

I have a red square with a white cross in it next to my speaker icon on the top panel, when I click on it I get the error in the title.

I have tried to run commands given in previous posts but nothing happens after I enter my password.


warren@warren-desktop:~$ sudo aptitude purge linux-sound-base alsa-base alsa-utils
[sudo] password for warren:
warren@warren-desktop:~$ 

I think it might have something to do with the fact that I can no longer open synaptic, i get the following error for that:

Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

starting to send me crazy all this weird stuff happening, it seems i'm in a fair bit of bother if I cant even run synaptic.


someone please help

big thanks
biddy

---

### Post by ludiq on 2008-02-06
I've tried all proposals from this thread and couldn't solve this problem.
Reinstall ubuntu from scratch should help...

BTW Totem and some applications plaing sound but skype even cannot star

---

### Post by SmartIcon on 2008-04-05
I am having Dell Inspiron 1520 Laptop. I am having the same problem. Please help me.

---

