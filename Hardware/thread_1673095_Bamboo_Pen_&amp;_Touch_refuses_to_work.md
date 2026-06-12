---
title: "Bamboo Pen &amp; Touch refuses to work"
date: 2011-01-21
forum: Hardware
---

### Post by ticktoast on 2011-01-21
I'm going to start out letting you guys know that I'm new to Ubuntu (actually.. I'm new to Linux in general). I'm a little slow on these types of things, but I'm getting better.

Anyway. My actual post...
I have spent nearly 6 hours trying to set up my new Bamboo tablet. I have literally tried every tutorial I could find and thoroughly read over any thread that was even remotely related to the issue.

However, after installing every driver mentioned and following every step on multiple guides, the tablet refuses to even register the pen's touch. 

I'm a very shy person, which is the reason why I waited 6 hours before coming here. I've never had the guts to use these forums before (despite reading threads constantly) and I'm still pretty iffy with the whole system. So, if I made any mistakes, please let me know what I need to do and I apologize ahead of time!

Any help at all would be GREATLY appreciated! If any additional info is needed to help solve my problem, I will provide it. I'm seriously desperate at this point. Thank you!

---

### Post by Favux on 2011-01-21
Hi ticktoast,

Welcome to Ubuntu forums!

You should be able to get it working by following the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  We should also figure out your model.  It will be on the label on the bottom of the tablet and we can get the product ID by entering in a terminal:
```
lsusb
```
and looking in the output for a line with Wacom in it.

Hope this helps.

---

### Post by ticktoast on 2011-01-22
[FONT=Verdana][SIZE=2]Thanks for the tutorial
Unfortunately, that was one of the ones I've already gone over (multiple times) and I can't seem to even get past the first step... I installed all the drivers, but after the reboot it still does not respond at all... 

I'm probably doing something wrong, knowing me... but I can't seem to figure out what..?

As for the tablet model, it's a CTH460/K[/SIZE][/FONT][FONT=Verdana][SIZE=2][/SIZE][/FONT]

---

### Post by Favux on 2011-01-22
Hi ticktoast,

"056a:00d6" tells the story.  Vendor ID = 056a = Wacom & Product ID = 00d6
The d6 is one of the new models.  You can confirm this by entering in a terminal:
```
lsusb | grep Wacom
```
The output should look something like:
```
Bus 005 Device 002: ID 056a:00d6 Wacom Co., Ltd
```
What to do is described in the box of model types at the top of the HOW TO.  You're in luck because your model was added to the X driver xf86-input-wacom a couple of days ago.  So you no longer have to do anything with xf86-input-wacom but re-clone the git repository which is part II.

For the wacom.ko you still need to add your model if you use the linuxwacom 0.8.8-10 version.  See post #2 on the HOW TO thread on adding the 5 new models.  However the input-wacom 0.10.10-1's wacom.ko already has your model added.  So you could just compile it.  Choice is yours.  Explanation and link in post #2.

---

### Post by ticktoast on 2011-01-23
I must be doing something wrong... I followed everything, step by step, and my tablet still doesn't react to the pen.

Well, the tablet registers the fact that it's being touched, as the light does change with touch. What I mean is that the cursor doesn't respond to the touch.

I'm beyond frustrated at this point... I haven't used a tablet since I was running Windows so this is totally new to me. I've had no problem using Ubuntu until this. It's rather stressful. Heh... sorry about the griping. I'm just at that desperate point, y'know?

---

### Post by Favux on 2011-01-23
Hi ticktoast,

I understand.

Since you listed the post as Ubuntu Studio and your info. says the same is it safe to assume your actually in and using Ubuntu Studio?  That flavor of the distro has given us troubles before.

First thing is to check in Troubleshooting near the bottom of the HOW TO.  Check on the part about the 64-bit install and see if you need the additional 64-bit flag.

---

### Post by ticktoast on 2011-01-23
I checked to see, and it doesn't look like I need the 64-bit.

And yes, I am running Ubuntu Studio. Is there any chance that that's the issue?

---

### Post by Favux on 2011-01-23
Probably.  It always seems to give problems and the problems seem different.  I'll have to try to remember what we did.  What is you kernel?
```
uname -r
```

---

### Post by ticktoast on 2011-01-23
The kernel is 2.6.35-24

---

### Post by Favux on 2011-01-23
No, I need the full name, for example:
```
2.6.31-22-generic
```
or use
```
uname -a
```

---

### Post by ticktoast on 2011-01-23
Oh! I'm sorry!
The full name is 2.6.35-24-generic

---

### Post by Favux on 2011-01-23
OK, so we know the kernel headers command was right.  Did you notice any errors when you were compiling?  Or any problems with the copy (cp) commands?

Let's make sure your wacom.ko is auto-loading:
```
lsmod | grep wacom
```

---

### Post by ticktoast on 2011-01-23
Well, if there were any errors I didn't notice them. But I'm not always the most attentive person, to be honest... 

The command you gave me doesn't give me anything, though. It just goes back to the blinking cursor.

(Thank you so much for your help, by the way!)

---

### Post by Favux on 2011-01-23
Sorry, watching the game.  OK, we found the problem, it isn't auto-loading.  We want to add 'wacom' without the quotes at the bottom of the file modules in /etc.  So:
```
gksudo gedit /etc/modules
```
save, close and reboot.  sudo makes you root/super user.  gksudo is the graphical version of sudo.  You use it when using a graphical program like gedit.  The rest is the directory path to the modules file.

---

### Post by ticktoast on 2011-01-23
Okay
Now when I run the command, I get..
morgan@Morgan:~$ lsmod | grep wacom
wacom                  29670  0

---

### Post by Favux on 2011-01-23
Am I to gather your tablet still doesn't work despite the fact wacom.ko is now loaded?

---

### Post by ticktoast on 2011-01-23
Ahhh.. yes. That is the case, it would seem. Yikes.

---

### Post by Favux on 2011-01-23
OK, let's do part I first and look at the output.  Towards the end of the ./configure output you should see:
```
----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
......

  BUILD OPTIONS:
            wacom.o - yes
......
```
Errors should appear before it (post any) and we want to see the wacom.o because that is the wacom.ko and that means it has been configured.  Also in the text following it should tell you where it is.

---

### Post by ticktoast on 2011-01-24
Okay... I got this back:

  BUILD ENVIRONMENT:
       architecture - i686-linux-gnu
       linux kernel - yes 2.6.30
      kernel source - yes /lib/modules/2.6.35-24-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - no 
             xidump - no 
        libwacomcfg - no
         libwacomxi - no
          xsetwacom - no
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - IsXExtensionPointer key-events

But now, I'm a bit confused. Before, I didn't see the i686.. I could've sworn it had said i486... Oh goodness...

---

### Post by Favux on 2011-01-24
That looks good.  It says it has built the wacom.ko.  Don' worry about the i686 thing.  So no errors, just maybe some warnings that we can ignore?  Now when you copy (cp) the wacom.ko into place are there any errors or problems?

---

### Post by ticktoast on 2011-01-24
There's no error messages, but nothing comes up when I enter it. Just the blinking cursor, still.

---

### Post by Favux on 2011-01-24
OK, show me the text below the BUILD OPTIONS: stuff.  It should say where the wacom.ko is.

Oh, wait a minute.  I see what you are saying.  If the copy command works it just returns to the prompt without any fuss.  It's only if it has a problem does it complain.  It would say something about not being able to stat.  So you copied the wacom.ko successfully.  Then when you do the 'sudo depmod -a' there should be a little delay before it returns to the prompt.  That means rebuild all module dependencies by the way.  And again you have to be root/super user (sudo) to have the permissions to change system files.

---

### Post by ticktoast on 2011-01-25
Okay.. I did that and rebooted..
Is there another step afterwards? Because it still isn't responding...

---

### Post by Favux on 2011-01-25
Yes, assuming the newly compiled wacom.ko is in place you now have one of the two drivers working.  The wacom.ko is the usb driver so now there is the correct usb communication between your tablet and Ubuntu.  Next you have to tell Ubuntu what to do with the raw usb data coming in.  That's what the X driver xf86-input-wacom does.  It converts the raw usb data into commands that the Xserver understands.  The Xserver is the X windowing system.  That's what draws the gui (graphical user interface) on your screen.

So now you do part II.  Again paying attention to each step and if you notice a problem or error stop and let me know.

---

### Post by ticktoast on 2011-01-25
I repeated part II, and didn't get any results even after another reboot...
I must be doing something very wrong. I didn't notice any errors, but I still can't get it to work.

---

### Post by Madouc on 2011-02-02
i seem to have as problem very much like the one of ticktoast.

i've done steps I and II. but no response from my wacom cth-460/k(a)

i'm running 2.6.35-25-generic

dmesg just gives me this:
[  655.420050] usb 2-1: new full speed USB device using uhci_hcd and address 3

another wacom tablet initialises normally:
[  651.608316] usb 1-3.3: new low speed USB device using ehci_hcd and address 11
[  651.705371] input: Wacom Graphire2 4x5 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input11

---

### Post by Favux on 2011-02-02
Hi Madouc,

Welcome to Ubuntu forums!

If you check the model box near the top of the HOW TO you'll see you have one of the 5 new models.  Did you add your model to the linuxwacom wacom.ko source code before doing part I?  Or your alternative is to install input-wacom.  Both described in post #2 on the HOW TO thread.

---

