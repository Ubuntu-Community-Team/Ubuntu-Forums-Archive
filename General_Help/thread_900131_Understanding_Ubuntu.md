---
title: "Understanding Ubuntu"
date: 2008-08-25
forum: General Help
---

### Post by elbarto_87 on 2008-08-25
Hi all,

I am a new Ubuntu user and have a few things I would like to discuss on the forum. I am sure my questions have been covered before in some way but with so much information out there, I haven't found anything that clears up my exact queries. 

1) I am use to XP, and hardly ever needed to use the command prompt for anything with the level of computing I do. Something I have found a little intimidating with Ubuntu is the amount of time spent in terminal. It seams everything is run from there, virus scans, samba configuration, etc. My question is, why is so much time spent in terminal and not in GUI's etc. The language used in terminal is quite foreign to me, and I don't think I could memorize 10 % of the commands I have seen posted that perform relatively simple functions. 

2) When I installed Ubuntu, I had to configure it with a password for my user account. I noticed that there are allot of things you need to give permission for to access and adjust settings. Is it necessary to have these passwords in place if I am the only one useing the computer? Do they provide any security for internet purposes etc?

3) When I right click on the 2 monitors in the top right corner, I can't select "Connection information". I found a post which I think suggest that this can only be accessed from the root level or something like that (or by ifconfig in terminal). Am I able to have all the privileges of the root level on my account to access such information without terminal?

Sorry if my question are a little novice, like I said I have only been exposed to windows up to this point. Any links to sites that have useful information for learning the Linux language would be greatly appreciated. 

Finally, it is hard to believe that this software is free, the people who have put time into developing this software have done an excellent job and should be commended.

Regards Elbarto

---

### Post by evildragon2 on 2008-08-25
Hi I also am a pretty new user to Ubuntu.The terminal is used because it is faster and can perform more tasks.Also not all things are run from terminal and I actually find the Ubuntu *GUI more helpful and configurable than windows *GUI.It is true that the terminal has higher learning curve but in the end I used it more because it was faster and easier for me.Its just a matter of preference and you can still use the *GUI.

[snipped]

 You don't need to all know all unix commands just the basic ones and use the *GUI for convenience.Here is a link to basic unix commands [http://sunsite.utk.edu/UNIX-help/quickref.html]("http://sunsite.utk.edu/UNIX-help/quickref.html")

*GUI is the graphic interface*which just mean the menus and icons plus all graphics you see on your computer.

---

### Post by Uchiha_madara on 2008-08-25
[SIZE="2"]> **elbarto_87 said:**
> Hi all,


1) I am use to XP, and hardly ever needed to use the command prompt ,
    It seams everything is run from there, virus scans, samba configuration, etc. My question is, why is so much time spent in terminal and not in GUI's etc.
 The language used in terminal is quite foreign to me,  

2) When I installed Ubuntu, I had to configure it with a password for my user account. I noticed that there are allot of things you need to give permission for to access and adjust settings. Is it necessary to have these passwords in place if I am the only one useing the computer? Do they provide any security for internet purposes etc?

3) When I right click on the 2 monitors in the top right corner, I can't select "Connection information". I found a post which I think suggest that this can only be accessed from the root level or something like that (or by ifconfig in terminal). Am I able to have all the privileges of the root level on my account to access such information without terminal?

Sorry if my question are a little novice, like I said I have only been exposed to windows up to this point. Any links to sites that have useful information for learning the Linux language would be greatly appreciated. 

Finally, it is hard to believe that this software is free, the people who have put time into developing this software have done an excellent job and should be commended.

Regards Elbarto

[/SIZE]
Hi Elbarto
At first Welcome to Ubuntu World don't worry Because Linux is new for you ......Day after day you well be Professional.
and there is small answer about your Questions :

1 - Terminal is Good Language to understand any Operating System
    Although WinXP
    But : Not All the Things you need to access by using terminal
          such as ADD/remove Applications , and so on 
      Some times you need to use the terminal to solve bugs , install some Applications Such as RealPlayer11 , Google Earth and so on, the commands are very much but after the Frequently using you don't have any trouble to remember or save the post which holding the answer or the command.


2 - Configure The Password is Important for Security and The Integrity for the System ,and Permission secure The System
you must to Log in as root from terminal
if you are confused from Login screen while booting you can disable it and Login Automatically as your user and root .

3 - you can use the root orders by using [sudo]

finally if you need any help just Post and you well support you

good luck

madara:lolflag:

---

### Post by sonofusion82 on 2008-08-25
welcome to linux/ubuntu!

1. another reason for many discussion to use terminal is that it allows precise execution of a series of action required. instead of writing a long paragraph trying to guide a user to perform something via GUI, it is easier and more accurate to do it via terminal. if you have tried to help someone less tech savvy to troubleshoot his/her winXP computer by guiding them around a few dialogs and configuration box, u will know what i mean.

2. yes, the need for password is important. vista introduced this as the infamous UAC too :-) and causes the same reaction as yours too. winXP's poor history with viruses and malwares is because most home users run at admin privileges even for daily task. linux and most other OSes has separate account for admin and user making compromised user account less likely to affect the whole system.

---

### Post by sameerds on 2008-08-25
> **elbarto_87 said:**
> I am a new Ubuntu user and have a few things I would like to discuss on the forum. I am sure my questions have been covered before in some way but with so much information out there, I haven't found anything that clears up my exact queries.

First of all, welcome to Ubuntu! I'll try to answer your questions, but here's a list of resources that can be useful for newcomers and for general help:

[LIST=1]
[*][Online Official Documentation for Ubuntu]("https://help.ubuntu.com/")
[*][Community Managed Documentation for Ubuntu]("https://help.ubuntu.com/community/")
[*]On the Gnome panel, click System->"About Ubuntu"
[*]On the Gnome panel, click System->"Help and Support"
[/LIST]

> **elbarto_87 said:**
> 1) I am use to XP, and hardly ever needed to use the command prompt for anything with the level of computing I do. Something I have found a little intimidating with Ubuntu is the amount of time spent in terminal. It seams everything is run from there, virus scans, samba configuration, etc. My question is, why is so much time spent in terminal and not in GUI's etc.


Actually, you are half-way right about the observation that a lot of time is spent on the terminal. Since you are already using Ubuntu, you might have noticed that you don't need the terminal all the time. Most things can be done in the GUI. But commands in the terminal have two advantages: 

[LIST=1]
[*]They have a very rich set of options that allow you to accomplish many tasks that would be cumbersome in the GUI
[*]They are easy to specify on the online forums.
[/LIST]

Whenever someone asks for help on the forum, most replies mention some command that they can run in a terminal. This is because it becomes very cumbersome to provide GUI directions ... click here, then select this, then click that, then type this, and so on. Instead, a terminal command usually allows a precise description of what to do, in a very very short format.

> **elbarto_87 said:**
> The language used in terminal is quite foreign to me, and I don't think I could memorize 10 % of the commands I have seen posted that perform relatively simple functions.

That's true. But you don't need to learn the language ... you'll get used to it over time. Also, when someone posts a command, you could try asking for a graphical way of doing the same. Maybe someone will scratch their head long enough to come up with directions to use the GUI!

> **elbarto_87 said:**
> 2) When I installed Ubuntu, I had to configure it with a password for my user account. I noticed that there are allot of things you need to give permission for to access and adjust settings. Is it necessary to have these passwords in place if I am the only one useing the computer? Do they provide any security for internet purposes etc?

Yes, having passwords is a very important security practice, whether or not you are connected to the internet. If you are the only one using the computer, there are easy ways to configure it so that it directly boots to your desktop without asking for a password. But whenever something needs to be done that changes system settings, it is good to have a password. This way, it is not possible for a malicious program to run in the background without you noticing it.

**[COLOR="DarkRed"]Important Note:[/COLOR]** Do not pay heed to postings that describe how to login as root without a password. Read the [forum policy]("http://ubuntuforums.org/showthread.php?t=765414") about such posts.

> **elbarto_87 said:**
> When I right click on the 2 monitors in the top right corner, I can't select "Connection information". I found a post which I think suggest that this can only be accessed from the root level or something like that (or by ifconfig in terminal). Am I able to have all the privileges of the root level on my account to access such information without terminal?

I just tried that applet on my PC ... when you simply left click it, it provides a dialog with sufficient information, along with a button to configure it. Clicking that button prompts me for a password.

> **elbarto_87 said:**
> Sorry if my question are a little novice, like I said I have only been exposed to windows up to this point.

Not to worry! People on this forum as well as the Linux / Free Software community are usually quite happy to help newcomers.

> **elbarto_87 said:**
> Any links to sites that have useful information for learning the Linux language would be greatly appreciated.

Look at the resources that I posted at the start. You will be able to learn a lot by sticking around on this forum. In addition, there are a gazillion websites out there, that talk about all things Linux.

> **elbarto_87 said:**
> Finally, it is hard to believe that this software is free, the people who have put time into developing this software have done an excellent job and should be commended.

It's important to note that the software is "Free as in Freedom", and not "Free as in Free Beer"! Lots of amazing people have contributed to make this excellent software. You can [start here]("http://www.ubuntu.com/community/ubuntustory/philosophy") to get an idea of the philosophy that drives all these people, and don't forget that Ubuntu is just one example of Free Software. There are many equally good efforts out there.

---

### Post by elbarto_87 on 2008-08-25
Thanks allot for the fast responses and warm welcome. Seeing a community of people willing to help others without any financial incentive is yet another extremely appealing aspect of Ubuntu.


I have family all over the country (Australia) that are currently useing XP, but it seams no matter how much effort you put into keeping anti-virus/spyware/malware/riskware software up to date, you always run into some problem. I would like to get them setup with Ubuntu, which is why I felt the need to ask a little more about the amount of involvement a user has to have with terminal, as the earlier generations of my family are not the most confident of computer users.

I have had a play around with vncviewer, and was able to connect to another pc on my local area network which was pretty cool. Is it as easy to connect to another computer that is not on the local area network, or do I have to have a VPN to do this. I think this would be the easist way to help out friends and family with their queries with Ubuntu once I become familiar with it myself.

One problem I am havein at the moment is my net is dropping in and out. I ran "sudo lshw -C network" and got the following report (when the net was working). 


```
 *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wmaster0
       version: 00
       serial: 00:14:85:cd:b3:b4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.65 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g

```

I am just wondering what your opinion is of using the windows drivers with wrappers on Ubuntu, if it would be anymore stable. At the moment, the net starts up instantly which is ten times better then windows, and so far I have not needed to install any additional drivers to use my system which I found very impressive.

Thanks Again

Elbarto

---

### Post by balaknair on 2008-08-25
*Something I have found a little intimidating with Ubuntu is the amount of time spent in terminal. It seams everything is run from there, virus scans, samba configuration, etc. My question is, why is so much time spent in terminal and not in GUI's etc.* 

You don't *have* to use the terminal, most of these things can be done via the GUI as well, it's just that it's often easier with the command line.
a simple example: *sudo apt-get install amarok* will install the amarok media player for you

You can install it via the GUI- Applications menu> Add/Remove Programs> Sound and Video> Amarok> Install.
One command on the terminal does all that for you. It's also easier to give instructions to someone else(like here on the forums- Terminal> command(s) as opposed to X Menu> Y Submenu> Z Application> Step 1> Step 2, then go to etc...)

As for the Admin password and Root accounts, it's actually designed to provide an optimum between usability and security. Even if you're the only user on your computer, these steps make it more difficult(but not impossible) for malware and virii and other internet based threats to damage/take over your system. I would strongly advise against logging is as Root purely for security reasons.

You will be able to see Connection Information even without Root password if it is not in 'Manual Configuration' mode.


An excellent newbie friendly guide to Ubuntu can be found here:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
It's the one I found most helpful when making the switch to Ubuntu.
It ought to clear most doubts you have expressed in your post, and also has links to more resources. I recommend it highly to all new Ubuntu users(and I add it as a bookmark in Firefox in all Ubuntu Installations I do for friends and family).

Hope this was helpful.

All the best.

---

### Post by mb_webguy on 2008-08-25
> **elbarto_87 said:**
> Hi all,

I am a new Ubuntu user and have a few things I would like to discuss on the forum. I am sure my questions have been covered before in some way but with so much information out there, I haven't found anything that clears up my exact queries. 

1) I am use to XP, and hardly ever needed to use the command prompt for anything with the level of computing I do. Something I have found a little intimidating with Ubuntu is the amount of time spent in terminal. It seams everything is run from there, virus scans, samba configuration, etc. My question is, why is so much time spent in terminal and not in GUI's etc. The language used in terminal is quite foreign to me, and I don't think I could memorize 10 % of the commands I have seen posted that perform relatively simple functions.
Well, that's mostly due to Linux being at its core a command-line operating system.  The desktop managers that provide the windows, icons, menus, and other elements of the desktop environment are actually just programs that run on this text-based operating system.  So while you actually can do a lot of things through the GUI, you're doing it one or two steps removed from the operating system.  By using the command line, you're actually working with the operating system itself.  Some see this as a flaw, but many change their mind once they realize how much Windows cripples users' ability to control the operating system.

However, graphical user interfaces on Linux have come a long, long way in the last few years.  Most of what you do in Ubuntu will be (or at least can be) done using a GUI.  But GUIs, by necessity and often by design, provide only a very simplified view of the systems they control.  While you may be able to do something using a GUI, you can do more and better using the command line, simply because you have the power to access every option and feature of the software.

Also, the "language" used in the command line isn't really a "language".  Commands are simply programs, and the options those programs require to perform their function.  Some are so basic in function and purpose that they are considered part of the operating system, and these will eventually become familiar to you with repeated exposure and experience.  Others, you will always have to look up before you use, just like everyone else does.

My final comment on this point is that Linux isn't Windows.  You mentioned virus scans...  You really don't have to worry about viruses in Linux.  There are some ideas about computing you've developed from using Windows that simply don't apply to Linux, even though they both do the same basic thing.  It's like the difference between driving a car and riding a motorcycle.  Both will get you where you're going, but you shouldn't expect to steer a car by leaning into the curve any more than you should expect a motorcycle to keep you dry when it rains.

> 2) When I installed Ubuntu, I had to configure it with a password for my user account. I noticed that there are allot of things you need to give permission for to access and adjust settings. Is it necessary to have these passwords in place if I am the only one useing the computer? Do they provide any security for internet purposes etc?
The quick answer is that except for the basic idea that some actions -- specifically those that involve more basic modifications to your system -- require escalated privileges (similar to how some actions on Windows require you to be using an Administrator account rather than a Limited account), you don't really need to know anything about Linux file permissions in order to start using the system.  This is a bit of knowledge you will eventually need, but which also will come with time and experience.  There are a lot of things you didn't know about Windows when you first started using Windows, but now take for granted.  The same will be true of Linux.

> 3) When I right click on the 2 monitors in the top right corner, I can't select "Connection information". I found a post which I think suggest that this can only be accessed from the root level or something like that (or by ifconfig in terminal). Am I able to have all the privileges of the root level on my account to access such information without terminal?
If you need root privileges to perform some task on the desktop, you will be asked to enter your login password.  If you aren't prompted for your password, you don't need root privileges.  If you try to use a command in the terminal that requires root privileges, you will be given a message informing you of the fact.

> Sorry if my question are a little novice, like I said I have only been exposed to windows up to this point. Any links to sites that have useful information for learning the Linux language would be greatly appreciated.
Here are a few links you might find useful or interesting.
[LIST]
[*]Linux is NOT Windows -- An very good article discussing some of the common difficulties Windows users have when moving to Linux, and the misconceptions which cause them.
[*][Linux vs Windows (A Comparison)]("http://www.michaelhorowitz.com/Linux.vs.Windows.html") -- A very thorough article about the differences between Linux and Windows to help Windows users understand Linux
[*][Linux Commands: A Practical Reference]("http://www.pixelbeat.org/cmdline.html") -- A quick reference to common commands
[*][A World Without Walls or Fences]("http://wysiwyb.blogspot.com/2007/11/world-without-walls-or-fences-pt1_15.html") -- A series of articles I posted to my blog introducing Linux from a very basic perspective, describing the differences between Linux, desktop managers, and distributions, and including a detailed instruction guide to installing Linux, with a focus on dual-boot systems.
[/LIST]

---

### Post by sameerds on 2008-08-25
> **mb_webguy said:**
> Well, that's mostly due to Linux being at its core a command-line operating system.  The desktop managers that provide the windows, icons, menus, and other elements of the desktop environment are actually just programs that run on this text-based operating system.  So while you actually can do a lot of things through the GUI, you're doing it one or two steps removed from the operating system.  By using the command line, you're actually working with the operating system itself.

Errr, no. That is completely wrong. The GUI is *not* running on top of the command line. What you are saying effectively means that when I drag and drop a file from one folder to another, the GUI is somehow running the "cp" command in bash with suitable arguments. Not so. The GUI is just as close to the system kernel as is the command line. Neither needs the other to run.

---

### Post by agasamapetilon on 2008-08-25
I recommend you to read the book Ubuntu Linux Toolbox, very useful. It will help you in your very first steps into the free software world. 

I have a link to download the book in pdf format, but don't know if its possible to paste it here, can someone tell me please.

Good luck!

---

### Post by mb_webguy on 2008-08-25
I didn't say that the desktop manager was running in a shell.  I said that it was a program on what is otherwise a text-based system, which is a perfectly valid statement.

A minimum install of Linux will have only a shell prompt for user interaction.  The shell itself is a program running on the operating system, but it is the most basic level of user interaction with the operating system -- which means that Linux is essentially a text-based operating system.

A graphical desktop manager such as Gnome, KDE, or Xcfe, is an application, and is not integrated into the operating system like as is the case in modern versions of Windows.  The desktop manager doesn't run in a shell, nor did I ever say otherwise -- only that it is an application that runs on Linux, which is, without it, a text-based operating system.

Using the command line is a very low-level interface, and as close as a user can get to actually manipulating the operating system.  The desktop manager is a high-level interface, and provides a more limited view and degree of access to the functionality of the operating system, both by necessity and design, since the desktop manager is designed specifically to simplify user interaction with the OS.  Since the shell is the most basic level of user interaction with the operating system, my statement that using the command line is working with the operating system itself is true, in that there is no lower-level user interface available.

Nothing about my previous post was inaccurate, except your reading of it.  Please do not put words into a person's mouth and then tell him that he is wrong for the words he never said.

---

### Post by sameerds on 2008-08-25
> **mb_webguy said:**
> I didn't say that the desktop manager was running in a shell.  I said that it was a program on what is otherwise a text-based system, which is a perfectly valid statement.

There is no such thing as a "text-based system". The "system" is actually the kernel along with the libraries that provide the necessary functions that other programs can call in order to do something. The command line, on the other hand, is a "text-based shell" just as the GUI is a "graphical shell" (hence the name Nautilus, btw).

Text is of course important for the system, since everything is identified by text ,.. like configurations, command names and file locations. But that is true with any system, not just Linux.

> **mb_webguy said:**
> Using the command line is a very low-level interface, and as close as a user can get to actually manipulating the operating system. The desktop manager is a high-level interface, and provides a more limited view and degree of access to the functionality of the operating system, both by necessity and design, since the desktop manager is designed specifically to simplify user interaction with the OS.

That is the real distinction. The command line is powerful, while the GUI is not. The GUI can be equally powerful, there is no fundamental limitation. But it would become almost impossible to use. But that simply does not mean that one is "closer" than the other,

> **mb_webguy said:**
> 
the shell is the most basic level of user interaction with the operating system, my statement that using the command line is working with the operating system itself is true, in that there is no lower-level user interface available.

The problem here is that you imply that the GUI is not "working with the operating system itself" in your own words ... that means there is something "in between" the GUI and the operating system. This is what I was replying to. The command line and the GUI are "equally close" to the system itself. The GUI is also "working with the operating system itself", but it does not expose a lot of functions, since they cannot be effectively used in a dialog box.

---

### Post by trwww on 2008-08-25
> **elbarto_87 said:**
> 
1) I am use to XP, and hardly ever needed to use the command prompt for anything with the level of computing I do. Something I have found a little intimidating with Ubuntu is the amount of time spent in terminal. It seams everything is run from there, virus scans, samba configuration, etc. My question is, why is so much time spent in terminal and not in GUI's etc. The language used in terminal is quite foreign to me, and I don't think I could memorize 10 % of the commands I have seen posted that perform relatively simple functions. 


With Distros like Ubuntu, you don't have to spend much time at all at a terminal if you don't want to. The terminal makes it easy to automate stuff (resize all the images in a folder, for example). Also, the reason most of the advice you see is terminal based is because it is easier to provide instructions that way. For example to add a firewall rule someone may have to list out 10 different things that need to be clicked/menus to be opened, when a single command at a terminal will do the job.

> **elbarto_87 said:**
> 
2) When I installed Ubuntu, I had to configure it with a password for my user account. I noticed that there are allot of things you need to give permission for to access and adjust settings. Is it necessary to have these passwords in place if I am the only one useing the computer? Do they provide any security for internet purposes etc?


It provides a lot of extra security. Having to type in a password is one of the reasons why there are so many fewer viruses for linux than there are for windows. The way you are supposed to use windows is set up an account as a regular user and use it to do your work. But then every time you need to install a program or adjust a setting you have to log out and back in to an administrator account, so people just always stay logged in to an administrator account. This is a recipe for disaster (IMHO, at this point things like this are done on purpose so an otherwise unnecessary security industry can be propped up).

---

### Post by gatenby_jp on 2008-08-25
Only use windows drivers in ndiswrapper if the kernel drivers do not work natively. Sometimes you have no option ... I will usually prefer to find a new card rather than use ndiswrapper ... obviously that is not an option if it is a laptop.

The discipline of switching to superuser or root, as most of us call it, (sudo) for installing anything is one of the reasons that Linux is and will remain relatively free of viruses etc ... they have to get your permission to be installed. Microsoft have tried to do something along those lines with Vista but have left too many holes for it to work.

using the terminal is easy when someone gives you commands via a forum like this ... all you do is copy the command then paste it into the terminal ... that way we are sure that you have the exact command we are looking for. You dont need to learn many of the commands most of us get by with very few.

If you are encouraging family to try it out I would suggest they use kubuntu instead of straight ubuntu ... KDE is easier than Gnome for most Windows users to get used to. However Gnome has always been the traditional GUI for Linux, particularly those variants based on the Debian repositories. 

The most important thing about Linux ... is it is built by a vast community of collaborators mainly IT orientated people who like things to work and not crash. No one controls the development it just goes on interminably ... young university students will often contribute improvements.

As an example I run several mail servers which all run QMAIL ... the program was written in 1995 ... it has never had a security breach ... it has never had to be re-written because it fails ... it was written by a 25 old mathematics lecturer. It is extensively used ... by the likes of yahoo etc ... it is truly amazing to become a part of a community that shares with each other.

---

### Post by sandysandy on 2008-08-25
> **agasamapetilon said:**
> I recommend you to read the book Ubuntu Linux Toolbox, very useful. It will help you in your very first steps into the free software world. 

I have a link to download the book in pdf format, but don't know if its possible to paste it here, can someone tell me please.

Good luck!

just copy and paste the link like this

[http://as.wiley.com/WileyCDA/WileyTitle/productCd-0470082933.html](http://as.wiley.com/WileyCDA/WileyTitle/productCd-0470082933.html)

keep in mind copyright issues:)

regards

---

### Post by elbarto_87 on 2008-08-26
Thank you all for your posts and suggestions. I appraciate the time you have taken to help me out. 

gatenby_jp, you recomend trying kubuntu. I might just do that. The last few days have been a bit of a learning experience, which I have enjoyed. 

I hope to become familiar enough  with this operating system to be able to use it as my only OS. At the moment I am still switching between Ubuntu and XP, at least until I can find a way to get MS Office to Install and operate. I have found many tutorials on how to do this (all different in someway to each other), but haven't had much luck yet. 

I will go have a Kubuntu now, as you have me intrigued. 

Kind Regards

Elbarto

---

### Post by sandysandy on 2008-08-26
> **elbarto_87 said:**
> 

I will go have a Kubuntu now, as you have me intrigued. 

Kind Regards

Elbarto

for KDE distros Kubuntu may not be the ideal one. 

i rather find OpenSuse11 or even Mandriva2008 with KDE better.

anyway its a personal choice. hope u like Kubuntu:) 

regards

---

### Post by elbarto_87 on 2008-08-26
Thanks Sandy,

I had a quick look at Kubuntu, at first glance I would have to say I like the plain Ubuntu interface a little bit better at the moment. Maybe thats because I am finally getting to know my way around it a little better tho.

One thing I would like to know is, is there a way you can have a address bar on the interface in Ubuntu that shows  you were you are when you are browsing a hard drive etc. ie "C:\Program Files\Adobe\Acrobat 7.0\Reader"?

Regards Elbarto

---

### Post by Inane_Asylum on 2008-08-26
May be a little late, but...
> Originally Posted by **elbarto_87**  
2) When I installed Ubuntu, I had to configure it with a password for my user account. I noticed that there are allot of things you need to give permission for to access and adjust settings. Is it necessary to have these passwords in place if I am the only one useing the computer? Do they provide any security for internet purposes etc?

One of the innate problems with XP is that the first user created when installing is set as having "root" priveleges.  You can go in, poke around, and change anything without any checks besides the "These files are 'protected' and shouldn't be changed, blah blah blah" messages you get when opening "windows" and "program files" folders.  As a result, any program running under that account has as much access as the user (i.e. root)...it's like leaving an open chimpanzee cage in the NASA control room.  As much as this bothered me when I first switched to Ubuntu, I've come to appreciate the fact that, this time around, the OS is looking out for **me**, and not the other way around.

---

### Post by sameerds on 2008-08-26
> **elbarto_87 said:**
> I had a quick look at Kubuntu, at first glance I would have to say I like the plain Ubuntu interface a little bit better at the moment. Maybe thats because I am finally getting to know my way around it a little better tho.

Oh, quite heartening to know that you would rather wait and get a feel of things before jumping to conclusions about the system! About KDE, a lot of people do seem to have the opinion that it shines better in other distros that have been with KDE for a long time, rather than Kubuntu. I wouldn't know because I never bothered to switch desktops.

One important thing to look out for is that according to current news, the current version of KDE is a big step in terms of redesign. Things might feel broken since there are many rough edges ... but the things being talked about are exciting enough for an entrenched Gnome user like me to take notice! (Gnome is the default Ubuntu "interface", btw ... for now, at least)

> **elbarto_87 said:**
> One thing I would like to know is, is there a way you can have a address bar on the interface in Ubuntu that shows  you were you are when you are browsing a hard drive etc. ie "C:\Program Files\Adobe\Acrobat 7.0\Reader"?

Your question is a little ambiguous ... do you want such a bar in the file browser (called Nautilus)? The default setting is to show a trail of folder names, which you can click on, to move up and down the directory hierarchy. But right next to it is a button with an icon that looks like a pencil on a notepad. Take a look at its tooltip ... it is used to switch to the other view, where the full path is displayed as a single string.

---

### Post by Fri13 on 2008-08-28
> **elbarto_87 said:**
> Hi all,

I am a new Ubuntu user and have a few things I would like to discuss on the forum. I am sure my questions have been covered before in some way but with so much information out there, I haven't found anything that clears up my exact queries. 

1) I am use to XP, and hardly ever needed to use the command prompt for anything with the level of computing I do. Something I have found a little intimidating with Ubuntu is the amount of time spent in terminal. It seams everything is run from there, virus scans, samba configuration, etc. My question is, why is so much time spent in terminal and not in GUI's etc. The language used in terminal is quite foreign to me, and I don't think I could memorize 10 % of the commands I have seen posted that perform relatively simple functions.


Ubuntu lacks own system configuration tools, and offers only a tools to manage system what GNOME desktop environment does include (you can find all those from GNOME menu "System"). There are Linux distributions what has own tools to manage system, like openSUSE or Mandriva (and other distributions what are based to those like PCLinuxOS) what has Yast and Mandriva Control Center. On those distributions, you dont need a CLI (command line interface) to do system wide configurations. That does not mean that CLI can not be used, but usually those choices are better for new users. Sorry for Ubuntu :-(
> 
2) When I installed Ubuntu, I had to configure it with a password for my user account. I noticed that there are allot of things you need to give permission for to access and adjust settings. Is it necessary to have these passwords in place if I am the only one useing the computer? Do they provide any security for internet purposes etc?


Ubuntu is software system what use Linux operating system. And Linux is *nix like operating system. The Unix operating systems were designed for multi-user environments with high security in mind. Linux does have special versions from it like SELinux what has even greater security. But the basis idea is that you dont never be logged in as root (admin) but just a basic user. The Ubuntu toke one as first distributions the sudo technology to their use, what allows one user to be a root. So on your system does not by default have a root account what could be cracked by quessing passwords if you have services open to network, what is not situation by default. The sudo bad side is that you have only one password what is usually used somewhere else too. So social engineering is easier to do and have a root access to your system. I always close the sudo to maximise the security against social engineering, even that I have different passwords (14+ special characters) for every service what I have on internet. The passwords does protect your computer, but it ain't just protect you, it will protect us others too on the internet. Because if your computer gets cracked, it can be used in botnets or other purpose against all other internet users, and I think you would not want that ;-)
 
> 
3) When I right click on the 2 monitors in the top right corner, I can't select "Connection information". I found a post which I think suggest that this can only be accessed from the root level or something like that (or by ifconfig in terminal). Am I able to have all the privileges of the root level on my account to access such information without terminal?


Hmm, actually not on Ubuntu. Because Ubuntu does not include the system wide graphical settings like openSUSE or Mandriva does. But you can start that graphical application from CLI :-)  But that right click on the network applet should allow you to see it. I'm currently running a Ubuntu in LiveCD and I can access to that. I suggest that you try the LiveCD and if it works, then there is something wrong happend to your configurations. You can try too without CD by making a new user and loggin in with it and trying to access it. If it does not access, then the problem is system wide and not on your first account. 

> 
Sorry if my question are a little novice, like I said I have only been exposed to windows up to this point. Any links to sites that have useful information for learning the Linux language would be greatly appreciated. 

Finally, it is hard to believe that this software is free, the people who have put time into developing this software have done an excellent job and should be commended.

Regards Elbarto

There is nothing bad to be a novice, no one of us will born with the knowledge already in our brains ;-). What you mean by the "Linux language"?

It is free but it does not always mean it's free as $$$ but it can be free like bird on sky (free speech). Someone pays always their time to participate the open source projects, so what they give, is their time.
But what they need as return, is your participating to give them ideas, bug reports and other suggestions. Linux world is like democracy, every user has voice what he can use to make whole community better. It's not like "communistic" like Microsoft Windows, where one company says what is coming next and those who has money, can vote and get such ideas, while normal user does not.

So when you use Distribution of Linux operating system like Ubuntu, you are allowed to use it as free, so long as it stays as free as someone gave it to you. This is protected by GPL license what is greatest thing what GNU project has done. It protects Linux operating system and many other application, not just Linux applications but windows too, what are licensed under it. So in short way, help the Linux community because then community is helping you.

---

