---
title: "Dell D505 can not get to X window"
date: 2009-12-13
forum: Hardware
---

### Post by supert8ch on 2009-12-13
I have been using my laptop for awhile and thought I would put a external monitor on it. After doing this and going to the display properties it sowed me the external monitor. I made a change to it to not duplicate the laptop, i wanted extended desktop, not sure if that is right in Linux. But any ways it said it had to make a change to soemthing and to logoff. I did and now it only goes to terminal. I have no clue how to get back to my desktop. 

Anyone have some information on this???? please, I am very new to Linux. 
Oh ya and running Ubuntu 9.10

---

### Post by supert8ch on 2009-12-14
Anyone? Anyone at all have an idea how to help me?

---

### Post by goldshirt9 on 2009-12-14
so you boot into the command line terminal and not the  and not the gui environment ??

---

### Post by supert8ch on 2009-12-15
Yes when system boots up I get the command line showing in the top left and it blinks 3 times then the command log in screen shows. I can log in there but can not do any more. I can not remember what was said when I tried to start xserver, but will be at the system tonight after work. I am sure it is something with me trying to do the dual monitor and it broke it.

---

### Post by Sef on 2009-12-15
> But any ways it said it had to make a change to soemthing and to logoff.

What changes did you make?

---

### Post by supert8ch on 2009-12-15
I went the display setting and it showed me that it saw the external monitor. I changed it to mirror the desktop and that was when it said it had to restart to make the change. I did not pay attention to the details.

---

### Post by supert8ch on 2009-12-19
Can anyone here help me with the issue?

---

### Post by nothingspecial on 2009-12-23
Log into a recovery shell and type

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by supert8ch on 2009-12-23
Not being all that great here. I am assuming the recovery shell will be the command prompt?
I will be home soon and will try this out. Thank you for the information on this. Is this a Ubuntu fix or Linux in general fix? As the 2 are not the same things, right?

---

### Post by supert8ch on 2009-12-23
I ran the command at the command prompt and it came back asking for password. I entered it and then it came back to a system prompt. I rebooted and it does the same thing.
I reboot and get the Ubuntu icon in the middle of the screen and then it goes black and the command prompt flashes in the top left 3-4 times and then comes up with command box.
I ran "sudo service gdm star" and it asked for password and screen flashed 4 times with the command screen that was up and comes right back up to the command prompt.

---

