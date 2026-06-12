---
title: "Serial port strangeness..."
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by narom on 2007-07-02
Hi all!!

I've done quite a bit of searching around about this and can't quite find the same problem.  I have a number of uses for the serial ports on my laptop; connecting to Cisco and sun devices, modems, that kind of thing.

I'm a recent conver to Ubuntu away from Fedora and have only just needed to start using the various serial ports on my laptop.  They work as expected under Fedora and using windows.  However, under Ubuntu (I've tried both Edgy and Feisty) I'm not having the same joy.  I've installed minicom and the likes.  All the devices get created, /dev/ttyS0, S2, ttyUSB0, etc.

The problem is that when I try to use them nothing.  minicom connects to the device, just nothing displaying from either the device or when I type.

For example, if I connect to a Sun box (an old 220R) using minicom with /dev/ttyS0 (or S2), 9600, 8-n-1 it initialises the link but nothing else.  Can't type anything in, don't receive any updates to the screen.  Same when I try to send AT commands to the modem or my 3G card.

I don't think it's a hardware issue.  I've tested it on a couple of laptops of different types and still nothing.  Am I missing something really obvious?

Thanks kindly,

Paul

---

### Post by narom on 2007-07-03
Anyone able to help?  Am I missing something that obvious?

;-)

Kind Regards,

Paul

---

### Post by frogbert on 2007-07-10
I'm getting the exact same issue. Any ideas folks?

---

### Post by narom on 2007-07-11
Looks like a udev issue.  I've got a USB serial converter and it seems to work.  Can only assume that the hardware I'm using can't easily be identified and set up correctly.

---

### Post by eastburn on 2007-07-13
f you have not already fixed this problem check out my write up over in the hardware forum. Its titled "Fix for brltty interfering with USB devices."

---

### Post by jokerjens on 2007-07-15
I think I have the exact same problem. I cannot open /dev/ttyS0. I have tried using cu:

$ cu -l /dev/ttyS0 -s115200
cu: open (/dev/ttyS0): No such device
cu: /dev/ttyS0: Line in use

Is the driver missing? I tried following the "Fix for brltty interfering with USB devices." guide without any success.

I also tried using minicom and GtkTerm both with the same result.

Have anybody got an idea about what can be wrong, or how to debug it. E.g. is it possible to verify if a proper driver is installed?

/jokerjens

---

### Post by RawMustard on 2007-07-16
yep something is completely screwy with ubuntu and serial, soon as you plug in a device it wants to take over.  I have a feelling it's the almighty kernel from hell that tries to run everything even when you tell it not to :(

---

### Post by eastburn on 2007-07-18
Hello Everyone,

I too had similar problems.  Seems the issue is with a demon process called brltty that is used for sight impaired persons using brail devices.  When you plug  certain USB devices that need the ttyUSB0 file, this brltty demon takes over then disconnects the ttyUSB0 file after a few seconds.

I found a solution to this by commenting out the rule file for the brltty demon.  I have posted instructions on how to do this over in the hardware & Laptop section of the forum.  It's listed under the subject header "Fix for brltty interfering with USB devices."

I hope this will be of assistance to you.  Let me know if it works.

---

### Post by eastburn on 2007-07-18
Here is the link to the brltty fix post.

[http://ubuntuforums.org/showthread.php?t=500186&highlight=brltty]("http://ubuntuforums.org/showthread.php?t=500186&highlight=brltty")

---

### Post by jimbob on 2007-07-18
Has anyone tried to *[COLOR="Blue"]apt-get remove brltty [/COLOR]*?  That should definitely clear the problem.

It should not be installed by default anyway IMHO.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Kowalski_GT-R on 2007-07-19
> **narom said:**
> 

I've installed minicom and the likes. 


I don't think it's a hardware issue.  I've tested it on a couple of laptops of different types and still nothing.  Am I missing something really obvious?



Paul

I have a similar issue.
I have to use the serial port for the mouse on an old pc.

Hardware was working under win 98,

yesterday I installed Xubuntu and mouse wasn't working

Are there some programs I should use?Again, am I missing something obvious?

Log in is ok with the keyboard, after that how can I access the terminal without the mouse?

any ideas to solve that issue? I only want to have mouse working, other hardware is detected and runs fine.
thank you

---

### Post by Shinoda on 2007-11-02
> **Kowalski_GT-R said:**
> I have to use the serial port for the mouse on an old pc.

Hardware was working under win 98,

yesterday I installed Xubuntu and mouse wasn't working
See if [this]("http://ubuntuforums.org/showthread.php?t=202972#post1176847") helps.
> **Kowalski_GT-R said:**
> Log in is ok with the keyboard, after that how can I access the terminal without the mouse?
By default Ctrl+Esc is supposed to bring up the Applications menu in Xubuntu, but at least for me it works arbitrarily. In alternative you can always run [FONT=Courier New]xfce4-terminal[/FONT] through Alt+F2 or use a CLI (Ctrl+Alt+{F1|F2|...}; [Ctrl+]Alt+F7 returns you to the GUI).

---

### Post by FrankIOM on 2007-11-17
Hi

I am having the same problem as everyone else on this list but mine is with my PCMCIA card
 I am new to Linux and am running Ubuntu 7.10 on my HP Laptop. At present I am busy trying to learn how to use the OS. 

My current only problem is trying to get my 3G PCMCIA card working with KPPP. The system is recognising the card and the light if flashing when I follow the instructions from Sierrawireless and type pccardctl info in the terminal window the information comes up. My problem is that I need to set the card up as a serial device, the instructions tell me to locate file "serial_cs.c" and then edit it with the supplied information. I cannot find a file with this name.  So I thought never mind if a run "dmesg | grep tty" as instructed it would tell me which serial port is in use etc. this did not work. the next step was to use "wvdialconf create" it did not find the modem but asked if I would like to allocate one using (if I remember) setserial with the warning if you set the wrong one the system may clash and lock up . This is were I stopped. My thought is this, How can I find out which serial ports are in use so that I can safely allocate a spare one to my modem ? then is there a nice easy way of setting up this port or is the setserial the easy way, could I have some instructions on this. I think that once this is done my modem will work as I have done the settings in KPPP, at present all I get is an error message saying the modem is busy on every serial port, I have interpretted this as an error - can't find the modem

Thanks in advance for the help. Once all has settled I will feed back to Ubuntu about my laptop so they can add it to the list of working PC's

---

