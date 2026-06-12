---
title: "Mini installation needs some patch work."
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by WolfRage on 2009-09-24
[FONT=Arial]I have a ASUS Eee PC 900A which came with a tiny 4GB SSD. The version of Linux that the system came with sucked and there was no room for any thing else. So I took several days to try out multiple distros of Linux to find something small but still in my comfort zone. But I learned I like the comfort of Ubuntu and none of there distros are small enough for me to pack in my applications. [/FONT]
[FONT=Arial]However by doing this I learned a ton about Linux in general. So with this knowledge I got brave and got a hold of the mini.iso and went about building my own tiny install. Now two days since I began this endeavor things are going well and I have just about everything I want and I am comfortable with the feel of the system. Currently everything installed is just under 2.5GBs, details below. But I have some lose ends that I need help patching up, before I will be satisfied. My wife says it will never end, but I told her if I get these things patched then at least it will slow down. Anyways my issues are listed below and thanks in advance![/FONT]
 
[FONT=Arial]1: Sound, I can not get the sound to work on this thing. To my own credit only 1 out of 8 distros had the sound working out of the box. I have read many forum posts and tried a lot of things, but standard tactics do not seem to work with this model of the Eee. As stated previously this was a problem I was trying to fix on the previous distros but I could only get it working on 3 of the 8 distros. But I have not had the same success on my mini installation. So I decided to start all over from the beginning and removed ALSA and Pulse Audio. Now I am hoping some one experienced with this model of the Eee can give me directions for which packages I need to install and in what order and what kind of configuration edits I need to make.[/FONT]
 
[FONT=Arial]2: Power Management, I have not installed any extra packages for power management as I am working issue number one. But I am pretty sure I need to install ACPI and APM plus each daemon. But I also read about PM being a good package to replace both, but it sounded like it was not ready yet. Also I would like to have some sort of a interface even if it looks like aptitude and htop. But I need it to be light weight, if an interface is not possible then I can deal. So what packages are recommended and what kinds of things do I need to know to setup proper power management on the Eee.[/FONT]
 
[FONT=Arial]3: Wifi, I have my wifi working and I am even using nm-applet to have a graphical interface. But I am thinking I should change to Wicd as i hear it is lighter and better. I also have a problem with the wifi card that is quirky. If I login fast and startx quickly then the wifi will ask for access to the keying and will connect to my network ok. But if I am slow or have a problem then the wifi will continuously try to connect and fail even if I provide my password for the key ring. Once this starts it will not even connect to an unsecured network. The only fix I currently have is to reboot. I would like to be able to restart the wifi card from terminal, but I was not able to find any such command.[/FONT]
 
[FONT=Arial]4: Auto mounting, is a minor problem, because I know how to mount a drive. I even had tried to setup an auto mount, but when the system boots it states that it failed when mounting the device because "Unable to mount special device /dev/sdb1 device does not exists. But when I mount it via the terminal I use "sudo mount /dev/sdb1 /media/MMC_SD_Slot". Can some one explain how I can properly setup auto mounting for my system?[/FONT]
 
[FONT=Arial]My current setup is Ubuntu mini 9.04 with: fluxbox, GNOME-Commander, ETerm, IDesk, NM-Applet, SAMBA, Firefox+Flash+Java, Netbeans+Java+PHP+Python+HTML+Javascript, Thunderbird+Lightening, Open-Office.org, Leafpad, htop, Pidgin, Skype, Xchat, & a LAMP Server^.[/FONT]
[FONT=Arial]I plan to include Movie Player, AUmix, and Blender. Which as a complete system with the above issues fixed should be just under 3GBs.[/FONT]
 
[FONT=Arial]Thanks to all who help out with any of my four issues! I will be checking back latter today and through out the week.[/FONT]

---

### Post by DFlame on 2009-09-24
I have to admire anyone willing to give a "ground up" install a go. I did the same with a very, very old Compaq "sub-notebook". I can't help with maany of your problems however.

For your networking questions, I slaughtered NM and went with wicd. As you are using 9.04, wicd should already be in the repos. You can install it and remove NM at the same time with:

```
sudo apt-get install wicd
```

Network interfaces can be refreshed/restarted with:

```
sudo /etc/init.d/networking restart
```

[s]I shall continue this post later, as my dinner will burn shortly![/s]

As for your mounting issues, mount the drive manually as you do, then post the contents of /etc/fstab and the output of "sudo mount"

---

### Post by WolfRage on 2009-09-24
Hey you are awesome! When I took a look at /etc/fstab I had a duh moment and noticed that I had made a typo! Auto mounting issue resolved! Also just installed Wicd and about to give it a go for awhile. Thanks for your help.
    I hope others will help me with the last 2 problems.

So Wicd is definitely a much better network manager and it is much less resource intensive! I am going to be sticking with Wicd for sure and it seemed to have fixed the wifi issues.

---

### Post by WolfRage on 2009-09-25
Still trying to get some help with the Sound for a ASUS Eee PC 900A. I have solved my wifi issues with Wicd and I have also solved my auto mounting thanks to the help of "DFlame". Powermanagement has been resloved by installing pm-utils, the system now does everything the way i would like in regards to power. But sound is still a major issue. Any help will be appreciated, thanks!

---

### Post by DFlame on 2009-09-26
This thread might offer some insight, but it is slightly aged:

[http://ubuntuforums.org/showthread.php?t=849646](http://ubuntuforums.org/showthread.php?t=849646) << Fixed by installing ALSA packages

---

### Post by kerry_s on 2009-09-26
4gb & your almost at 3gb ?

:lolflag: i'm using a debian gnome-core build up & i haven't even reached 2gb.
i'm on a 10 year old vaio laptop 450mhz 256mb ram.

---

### Post by WolfRage on 2009-09-28
Alright so installing ALSA and then running "alsamixer" still results in this message. 
"alsamixer: function snd_ctl_open failed for default: No such device"
I have tried several configurations but nothing seems to work.

kerry_s: I have to respect the size of your Debian installation. But I was fearful of going outside of the Ubuntu support network. However if I do not make more progress and the fact that my desktop has arrived I may work towards that route.

---

### Post by WolfRage on 2009-10-22
I have solved the problems, although I kind of cheated. I decided to do a full ubuntu install and then remove unneccesary aspects. I had to be careful though because at one point I accidently broke my sound. But Ubuntu allowed me to fix it agian.

---

