---
title: "Linux help"
date: 2008-09-22
forum: General Help
---

### Post by Tryfan on 2008-09-22
Hi there, this may seem like a silly question! but at the moment I am a Windows Xp user .. thinking of coming over to Linux!

The thing is.. I keep seeing things like the use of command codes! Is this something that needs to be used in everyday useage? I don't want to load up Linux ubuntu and find I have to type in a load of codes to do anything.. :confused::confused::confused:

Also I have a ubuntu disc which I have tried to install but it won't uninstall the Windows Xp.. any help would be greatfully accepted.. :):confused::confused::confused:

---

### Post by Sycron on 2008-09-22
You can use Ubuntu fine without a terminal. Welcome to ubuntuforums.org and fell free to ask EVERYTHING, no matter how it sounds. We are doing our best to satisfy the Ubuntu users.

---

### Post by snowpine on 2008-09-22
> **Tryfan said:**
> 
The thing is.. I keep seeing things like the use of command codes! Is this something that needs to be used in everyday useage? I don't want to load up Linux ubuntu and find I have to type in a load of codes to do anything.. :confused::confused::confused:


Hi Tryfan, most of the time, Ubuntu gives you several options for performing a particular task. Most tasks can be performed using point-and-click. However, there's a very good reason why most of the tutorials on these forums use the Command Line Interface (aka the Terminal): if I give you a command like "sudo apt-get install firefox", you can copy and paste it into your terminal. It is much quicker and simpler than trying to tell you "go to menu X and select Y, then click the green button halfway down the screen, and make sure the box is checked next to blah blah blah," plus there is less chance you will misinterpret the instructions. 

The other benefit is that Ubuntu has variations such as Kubuntu, Xubuntu, Edubuntu, etc. Command-line instructions are the same in all of these, whereas point-and-click instructions don't necessarily translate.

Personally, I like using the terminal, and I don't find it intimidating. That being said, I understand you prefer point-and-click, and the answer is yes, you can do almost all of your everyday tasks without ever opening the terminal.

ps Ubuntu has a "live CD" that you can use without making any changes to your system. Very useful if you want to try it out and decide if you like it or not. We would love to have you as part of the community, but only if Ubuntu meets your needs and makes you happy. :)

---

### Post by Elfy on 2008-09-22
Often it is quicker to use a command to accomplish a task, also it is easier to give someone a command to run something as it is generally universal between variants.

For example - run this command sudo apt-get install package is a lot easier than open synaptic or add/remove from a menu and then search for it there, right click and use install, but if you're not using ubuntu you have to use adept instead of synaptic.

That said you won't necesssarily find yourself using it a lot once youre setup.

The ubuntu disc will only uninstall xp if you tell it to use the whole of your hard disk drives. If that is what you want to do then choose the use whole disc option - it will do so, if you have more than one parrtition on the drive you will lose all of them.

If you had C:\ and D:\ you would for instance lose them both (unless they were sepereate hdd's)

---

### Post by Sycron on 2008-09-22
I'm a happy Ubuntu user, and after acomodating with it I use a lot of terminal commands. It really speed up some tasks and I love that.

As a first time user, I didn't used too much terminal, but HELPED me a lot configuring my computer as I saw in forums, docs, tutorials.

---

### Post by Tryfan on 2008-09-22
OK thank you for all your help.. 

one more question.. how do I bring up the terminal?.. :(:confused:

---

### Post by snowpine on 2008-09-22
> **Tryfan said:**
> OK thank you for all your help.. 

one more question.. how do I bring up the terminal?.. :(:confused:

Applications menu, in the Accessories category. (That's the point and click way.)

---

### Post by Tryfan on 2008-09-22
> **snowpine said:**
> Applications menu, in the Accessories category. (That's the point and click way.)

Cheers Snowpipe  ;):guitar:

---

### Post by snowpine on 2008-09-22
The first terminal command you should learn about is 'sudo' (Super User DO)

Basically, if a command does NOT require sudo, it can't break your system. The worst that can happen is that you will lose all of your personal documents and files (which you should back up regularly anyway).

If a command DOES require sudo, it's a warning that the command could potentially break your system so Ubuntu doesn't work any more (for you as well as any other users on your computer). That's why you need to enter your password again; it's warning you that you're about to execute a system administrator level command. Don't be scared, but be careful! When using anything with 'sudo' make sure that you understand what the command does, that you trust the person telling you to do it, and that you don't make any typos.

Sudo is nice for Ubuntu newbies because it reminds you to think before you type. You'll need it to, for example, install new software, change system settings, add new users, modify your network settings, etc.

If a point and click graphical application asks for your password (for example, Add/Remove Programs), that means it's using sudo behind the scenes (more accurately, 'gksu' which is short for 'graphical sudo') and the same warnings apply. :)

---

