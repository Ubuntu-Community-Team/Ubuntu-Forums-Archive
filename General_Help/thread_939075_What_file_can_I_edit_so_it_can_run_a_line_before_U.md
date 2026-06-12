---
title: "What file can I edit so it can run a line before Ubuntu starts up?"
date: 2008-10-05
forum: General Help
---

### Post by riahc3 on 2008-10-05
What file can I edit that can run a line when I first hit enter on my boot menu for Ubuntu (I mean I hit Ubuntu and it instantly runs that line).?

---

### Post by bodhi.zazen on 2008-10-05
what are you wanting to de exactly ?

Sounds like you are wanting to edit /boot/grub/menu.lst

---

### Post by riahc3 on 2008-10-05
I want to run (for example)

echo "Hello"

before Ubuntu even starts doing anything. Where would I put that?

---

### Post by Neo_The_User on 2008-10-06
I can't really understand what you're talking about.

If you're looking for start up errors during the boot, type this command into the terminal:

sudo gedit /boot/grub/menu.lst

scroll down near the very bottom of the file. Take out the part that says "quiet splash"

A few lines below where it says ## ## End Default Options ##. You can't miss it. It's right next to the kernel thing.

---

### Post by Yellow Pasque on 2008-10-06
The OP is asking where to execute a startup command before X loads (I think). The answer is "it depends". If it's something you want to perform for all users, you'll probably want to put it in /etc/rc.local.
So:
```
sudo chmod 755 /etc/rc.local
gksudo gedit /etc/rc.local
```
Add your command, save, and exit.

---

### Post by davidryder on 2008-10-06
And if you want to execute commands for your profile only:

```
gedit ~/.profile
```

If you are going to execute a program, put a & at the end of the command - otherwise it will hang on boot.

---

### Post by riahc3 on 2008-10-06
> **Temüjin said:**
> The OP is asking where to execute a startup command before X loads (I think). The answer is "it depends". If it's something you want to perform for all users, you'll probably want to put it in /etc/rc.local.
So:
```
sudo chmod 755 /etc/rc.local
gksudo gedit /etc/rc.local
```
Add your command, save, and exit.

I want to execute this command once (I would write this command before the Ubunutu loads in whatever file then afterwards simply remove it and be done)

> **davidryder said:**
> And if you want to execute commands for your profile only:

```
gedit ~/.profile
```

If you are going to execute a program, put a & at the end of the command - otherwise it will hang on boot.
But doing it for my profile, will execute it after the boot/login screen right? Im not intrested in that.

---

### Post by Yellow Pasque on 2008-10-06
Ok, then I have absolutely no idea what you are trying to do. Please tell us.

> before the Ubuntu loads
Be more specific. When you start your system, the BIOS loads the GRUB bootloader, then GRUB loads the kernel, the kernel loads the desktop manager, and then you login to the desktop environment. Where in the process do you want the command to run?

---

### Post by mixmaster on 2008-10-06
Nothing can run before Ubuntu starts up because there is no operating
system to run anything.

I assume you want a sort of "runonce" processor which will run before any end user gets control of the system.  You can achieve this by executing and then deleting a script from somewhere within the boot process, preferrably near the end so that you have the OS services you might require.  There may be tools to help achieve this but tbh I've never had the need to do this (except when writing installers) so I can't point you at anything specific.  If you give a bit more detail as to what you are trying to achieve and why then someone might be able to offer more specific advice.

---

### Post by davidryder on 2008-10-06
> **riahc3 said:**
> Im not intrested in that.

Then tell us what you are interested in :D

---

### Post by Yellow Pasque on 2008-10-06
> I hit Ubuntu
> before the Ubunutu loads in whatever file

Can you clarify these expressions? Are you running wubi (Ubuntu in Windows)?

---

### Post by riahc3 on 2008-10-06
> **Temüjin said:**
> 
Be more specific. When you start your system, the BIOS loads the GRUB bootloader, then GRUB loads the kernel, the kernel loads the desktop manager, and then you login to the desktop environment. Where in the process do you want the command to run?
I installed Ubuntu using Wubi. Installing via Wubi method, creates a boot menu. When I hit enter while selecting "Ubuntu" right after I hit enter, I want it to run (for example)

echo "example command"

> **mixmaster said:**
> 
I assume you want a sort of "runonce" processor which will run before any end user gets control of the system.  You can achieve this by executing and then deleting a script from somewhere within the boot process, preferrably near the end so that you have the OS services you might require.

Basically yes. 

> **davidryder said:**
> Then tell us what you are interested in :D

Running a command right before Ubuntu boots up and does all its loading.

> **Temüjin said:**
> Can you clarify these expressions? Are you running wubi (Ubuntu in Windows)?

You can't run Wubi; Wubi is simply a installation method.



I think this will help out: I want to do what in Windows is autoexec.bat

---

### Post by Yellow Pasque on 2008-10-06
You may have more luck having a mod move this thread to the wubi forum (or searching there).

---

### Post by bodhi.zazen on 2008-10-06
riahc3: If you would be so kind as to describe what you are wanting to do exactly we can help you.

I think we understand you are wanting to run a command before you load the ubuntu kernel, but this is difficult.

Basically in Linux you write a bash script. This is a file , the first line is #!/bin/bash, and then like a .bat file you list commands you wish to run.

Like this :

> #!/bin/bash
command 1
command 2

The "problem" is that before you load the kernel there is not much in the way of an operating system, you have the BIOS and then Grub.

Most likely you can do what you wish by adding your command(s) to /etc/rc.local, or if not we will need to add the script earlier in the boot process.

This thread may help explain the boot process :

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Otherwise without a more specific question it is hard to give a more specific answer.

---

### Post by riahc3 on 2008-10-10
I want to run

modprobe -r pcspkr

Which removes my pc speaker (or similar command)

---

### Post by Yellow Pasque on 2008-10-10
Try blacklisting the module so it does not load.
```
cd /etc/modprobe.d/
sudo chmod 776 blacklist
gksudo gedit blacklist
```
Add "blacklist pcspkr" to the file, save, quit, and:
```
sudo chmod 544 blacklist
```

---

### Post by riahc3 on 2008-10-10
> **Temüjin said:**
> Try blacklisting the module so it does not load.
```
cd /etc/modprobe.d/
sudo chmod 776 blacklist
gksudo gedit blacklist
```
Add "blacklist pcspkr" to the file, save, quit, and:
```
sudo chmod 544 blacklist
```

Reexplain please.

---

### Post by -Zeus- on 2008-10-10
what do you want reexplained???  do what he said

---

### Post by bodhi.zazen on 2008-10-10
> **riahc3 said:**
> Reexplain please.

LOL

Now that you have explained what you are wanting to do , Temüjin posted the solution.

Linux has a wide range of hardware drivers , called modules. blacklisting the pcspkr module keeps it from loading when you boot your box.

Temüjin was kind enough to give you explicit step-by-step instructions.

See also : [http://linux.die.net/man/8/modprobe](http://linux.die.net/man/8/modprobe)

---

### Post by riahc3 on 2008-10-12
> **-Zeus- said:**
> what do you want reexplained???  do what he said

What the hell am I doing exactly? Blacklisting? WTF is that?

I add 
blacklist pcspkr
to what file?

It makes no sense...

> **bodhi.zazen said:**
> LOL

Now that you have explained what you are wanting to do , Temüjin posted the solution.

Linux has a wide range of hardware drivers , called modules. blacklisting the pcspkr module keeps it from loading when you boot your box.

Temüjin was kind enough to give you explicit step-by-step instructions.

See also : [http://linux.die.net/man/8/modprobe](http://linux.die.net/man/8/modprobe)

Thanks for the better explaination but again...What/when/where do i run this (besides terminal)?

---

### Post by bodhi.zazen on 2008-10-12
You run those commands in a terminal and it is a one time configuration.

---

