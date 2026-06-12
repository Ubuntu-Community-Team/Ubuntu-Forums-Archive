---
title: "Install hangs, never finishes"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by averagejoe77 on 2009-03-14
Ok, I am COMPLETELY new to Kubuntu. I have NEVER used it before. I know absolutely NOTHING about the CLI.

With that Out of the way, let me explain my problem. I have an HP Elite Media Center PC (m9340f). It has an Intel Core2 Quad CPU running at 2.66GHz, 750GB HDD with two partitions: 1) Windows Vista (64 bit edition)(600+GB) and 2)the factory image of Windows Vista(11.35GB), both with an NTFS format. 

I downloaded the Kubuntu 64-bit PC (AMD64)Desktop CD from this site ( [http://releases.ubuntu.com/kubuntu/8.10/]("http://releases.ubuntu.com/kubuntu/8.10/")). I then burned the .iso file onto a cd. Then I placed the cd in my disc drive and rebooted. When asked what drive I wanted to boot from I choose Kubuntu. I then was taken to a splash screen with the blue Kubuntu logo and the blue "progress" bar. Once the bar stopped bouncing back and forth, and filled completely from the left to the right, I was presented with the boot options. I chose to "try Kubuntu without making any changes to my computer" and I was taken to a command line interface with the promt "ubuntu@ubuntu:~$" (without the quotes of course) where I was stuck (not knowing the CLI for Linux, or any other OS for that matter).

I rebooted using ctrl+alt+delete (because I didn't know what else to do), and began the arduous search of the internet for more information as to how to set up a dual boot with Windows Vista(x64) and Linux. The best information that I came across was this site ([http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")). I followed these instructions to a "T", but I couldn't actually get past the first step, as I never got to the installer. I tried to reboot from the Live CD and select "Install", but I am eventually presented with the same CLI promt.

So, my question is, simply, HOW do I install Kubuntu on my Vista machine without having to reinstall Vista or set up a seperate partition? 
I would like to remove the Factory Image, without deleting the partion that has been created for it, and install Kubuntu in it's place. However I see that Kubuntu uses the "ext3" file system (never heard of that before), and the current file system on the partition is NTFS. I assumed that I would be able to reformat it using the Kubuntu CD, but I can't get anywhere with it.

I can be reached on both Windows Live Messenger (joe4jchrist@hotmail.com) and yahoo messenger (leviathan1977@yahoo.com) or through my gmail addy at [email]joe.mesot@gmail.com[/email].

Thank you,
Sincerly frustrated,
Joe.

---

### Post by martrn on 2009-03-14
Can you switch off anything in your computer's BIOS to make sure it doesn't recognize any wireless input devices and make sure you have pluged in a keyboard ps2 and ps mouse. 

Buy or borrow a cheap wired keyboard and mouse to install Kubuntu and then installing wireless device drivers after if you have any wired keyboards/mice.

Plugging in a USB mouse or USB keyboard might work - plugging in wireless / input devices possibly won't.

Are you sure your keyboard is attached ?

---

### Post by averagejoe77 on 2009-03-14
Martn,

I don't use any wireless devices. The only thing I use as wireless is my network connection, which at that point in the install is not even a factor, at least i wouldn't think it would be. And yes, everything is connected, ps2 mouse and keyboard.

Thanks for the advice,
Joe.

---

### Post by SuperSonic4 on 2009-03-14
Did you get the right CD image? What happens if you check the disc for errors?

---

### Post by averagejoe77 on 2009-03-14
Ok, Update.

I found this site ([http://www.brighthub.com/computing/linux/articles/14039.aspx]("http://www.brighthub.com/computing/linux/articles/14039.aspx")), and it talks about using the auto installer. I also tried to use this method (before I found the site), but it still resutled in the same CLI prompt. I am going to try to walk through this site's walk through to see if they do anything different from what I have done.

I didn't try to check the disc for errors, but I will. I was also thinking that naybe I had gotten the wrong installer. Would checking the disc for errors alert me to this, or am I just left to assume it is the wrong one?

Tahnks,
Joe.

---

### Post by martrn on 2009-03-14
> **averagejoe77 said:**
> I didn't try to check the disc for errors, but I will. I was also thinking that naybe I had gotten the wrong installer. Would checking the disc for errors alert me to this, or am I just left to assume it is the wrong one? Tahnks, Joe.

[URL="http://releases.ubuntu.com/kubuntu/8.10/"]
http://releases.ubuntu.com/kubuntu/8.10/[/URL]

Neither is the wrong installer for ubuntu from that page.  If you use the destktop CD installer you should have the ability to boot into a live Kubuntu environment if you boot using that CD, if you have the 'alternative CD' it should give you the option to install kubuntu using a menu driven like enviorment, where you can install ubuntu but not run kubuntu live from the CD.  This (the alternative CD) is a better CD to 'Install' Kubuntu as it allows you to install ubuntu with problematic hardware, but would not be a good CD to get if you wanted to boot into a live CD enviroment.

I would say do not install webi, as the file system is just one large file on another operating system, and could result in data loss to the file.

If you are booting the live CD (desktop CD) and presented with a CLI after booting it would suggest you can not boot into X because of some problem with it detecting your hardware or simular.  An alternative CD will let you install kubuntu to your computer and should work or give you an error as to why it did not.

If you you use GParted to partition your disk,  ([http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")) if you need to move/resize or change your partitions, and use the 'alternative CD' then you can install kubuntu using the alternative CD.

I do not know from what you say weather you have the alternative CD or the Desktop CD version of ubuntu ?

---

### Post by averagejoe77 on 2009-03-15
> **martrn said:**
> [URL="http://releases.ubuntu.com/kubuntu/8.10/"]
http://releases.ubuntu.com/kubuntu/8.10/[/URL]


If you are booting the live CD (desktop CD) and presented with a CLI after booting it would suggest you can not boot into X because of some problem with it detecting your hardware or simular.  An alternative CD will let you install kubuntu to your computer and should work or give you an error as to why it did not.

First off, I am using the Desktop CD. Secondly you hit it on the head. I tried to install again, this time doing the verbose otion, and I noticed right at the end that is said "Xserver'something-or-other' failed to start after 60 seconds.". So, I will redownload the ALternate CD and try that.


> 
If you you use GParted to partition your disk,  ([http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")) if you need to move/resize or change your partitions, and use the 'alternative CD' then you can install kubuntu using the alternative CD.

I will do this as well, and report back here shortly, hopefully from a Linux browser. :)

Thank you,
Joe

---

### Post by Jphenow on 2009-03-15
I am having a VERY similar problem. In fact it sounds exactly the same so far. I hope you find a solution because I have not had really anything working so far...

---

### Post by averagejoe77 on 2009-03-15
Update,

Well, I downloaded the GParted.iso, burned that to a disc. Then I downloaded the "Alternate CD" and burned that to a disc. 

I rebooted from the GParted CD, reformated the 11.35GB partition (which was 12.2GB) to the ext3 FS. Then I rebooted from the "Alternate CD", again reformatted the 12.2GB partition (Just to be sure) but did not create a "swap file" partition because I was unsure how to do it exactlly, and the warning mentioned the reason for creating one was because of low system RAM, of which I have 6GB, so I figured there was no need. Then I installed Kubuntu. Everything went fine. 

I was asked if I wanted to add GRUB to the Windows Bootloader so that I coudl be given the option to boot from either OS, so I did that. Then I was asked to reboot into Kubuntu.

Upon reboot I was presented with a "Login: " prompt, where I entered the login name that I created during installation, then the "Password: " prompt, where I entered the passsword I created during during installation. An then... drumroll please... I was AGAIN taken to a CLI, this time it was "*username*@Kubuntu:~$" (*username* is the name I logged in as). 

Is there a command that that I need to execute at the CLI in order to get Kubuntu to load the desktop? I am completely lost when it comes to CLI commands. I do not know anything about Bash other then the few exmamles that I have read in the internet in the past few days.

So, still no luck.
Joe.

---

### Post by Jphenow on 2009-03-15
The fact that you're dropped to to bash right off the bat usually means starting up the Desktop manager after that won't much be happening. =/ I'm sorry I believe I have the exact same problem as you and I cannot figure out why, this seems to not be too prevelent though because there's almost no information on this problem.

If you do want to try starting up manually just to be sure do this..
```
sudo /etc/init.d/kdm start
```
it's possible it will claim that it's already running in that case replace "start" with "restart."

Good luck, I've spent as much time over the last 3 days on this as I can afford and I'm starting to get pretty unhappy.

---

### Post by martrn on 2009-03-15
Back up and check your existing xorg.conf file

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf
```
// <ctrl> + X to quit (check resolution settings)

Install and run EnvyNG

```
sudo apt-get update
sudo apt-get upgrade
```

Check you can ping a server and install drivers

```
ping google.com
sudo apt-get install envyng-qt
sudo envyng -t

```

Choose Install Nvidia/ATI driver, and follow guidance to choose a driver. When you are returned to the CLI prompt, run the Nvudia/Ati xorg configuration utility:

```
sudo nvidia-xconfig   
sudo aticonfig
```

When it is done writing a new xorg.conf file, restart the X server with

```
startx
```

---

### Post by martrn on 2009-03-15
> **Jphenow said:**
> The fact that you're dropped to to bash right off the bat usually means starting up the Desktop manager after that won't much be happening. =/ I'm sorry I believe I have the exact same problem as you and I cannot figure out why, this seems to not be too prevalent though because there's almost no information on this problem. [..] Good luck, I've spent as much time over the last 3 days on this as I can afford and I'm starting to get pretty unhappy.

```
sudo ls /var/log/ -alt
```
will have the answers you need, like an error message or simular...

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/62539]("https://answers.launchpad.net/ubuntu/+source/xorg/+question/62539")
[http://forum.kde.org/dual-monitors-in-kde4-t-25765.html]("http://forum.kde.org/dual-monitors-in-kde4-t-25765.html")
[http://www.x.org/wiki/FAQ]("http://www.x.org/wiki/FAQ")

You have not /var/log/   ~~some error message or other  so you wouldn't be looking for anything in particular as to what it is.

---

### Post by averagejoe77 on 2009-03-15
Martn,

Well, what can I say, you got it.

I actually Googled the error "X server failed to start after 60 seconds" to see who else had this same issue, and sure enough it was a monitor issue.

This site fixed it [https://answers.launchpad.net/ubuntu/+question/8351]("https://answers.launchpad.net/ubuntu/+question/8351"), bout i had some issues with it at first. And surprise, I am writing this from Konqueror!!!!!

Thanks for all the help

---

