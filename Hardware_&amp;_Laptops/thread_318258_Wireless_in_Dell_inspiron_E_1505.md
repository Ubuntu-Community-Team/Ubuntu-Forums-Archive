---
title: "Wireless in Dell inspiron E 1505"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by Stephen47 on 2006-12-13
I have the above computer. I went to HOWTO: Dell Inspiron E1505 Wireless (Broadcom 1390 WLAN) and followed the instructions at:[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092). when I got to the command line: sudo apt-get install linux-headers-`uname -r` I assumed 'uname" was my username I got a message saying: E: Command line option 'r' [from -r] is not known. what am I doing wrong?

---

### Post by Fully216 on 2006-12-13
You always have the option of installing the linux-headers via SPM.  There is no -r option to apt-get (see man page).  You just need the linux-headers of the kernel version you are running, so you can try it without the switch.

---

### Post by theturtlemoves on 2006-12-13
> **Stephen47 said:**
> I have the above computer. I went to HOWTO: Dell Inspiron E1505 Wireless (Broadcom 1390 WLAN) and followed the instructions at:[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092). when I got to the command line: sudo apt-get install linux-headers-`uname -r` I assumed 'uname" was my username I got a message saying: E: Command line option 'r' [from -r] is not known. what am I doing wrong?

You're doing fine, except for a minor misunderstanding. uname isn't your username, uname is just uname. It's a command that outputs the kernel version number, so when you put 'uname -r' in the apt-get command, it automatically replaces 'uname-r' with the output of the command 'uname -r'.

So use this command EXACTLY as written (no substitutions, no removal of quotes) and continue.
```
 sudo apt-get install linux-headers-`uname -r`
```

---

### Post by Fully216 on 2006-12-13
Interesting theturtlemoves, did not know that.  You learn something new every day.  Thanks!

---

### Post by Stephen47 on 2006-12-13
ok I did that and then there is just a blinking cursor in terminal without steve@stevelaptop first. Is this right? I typed in the next command:wget [http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE) and nothing happened just the blinking cursor on the next line. did I do something wrong?

---

### Post by Fully216 on 2006-12-13
do you have an internet connection when you do so?

you can always download the driver via web browser instead of the cli.

---

### Post by theturtlemoves on 2006-12-14
> **Stephen47 said:**
> ok I did that and then there is just a blinking cursor in terminal without steve@stevelaptop first. Is this right? I typed in the next command:wget [http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE) and nothing happened just the blinking cursor on the next line. did I do something wrong?

Ok, step by step.

When you entered the previous step, did it ask you for your password? If so, after you entered it, did it actually install the kernel header package?

---

### Post by Stephen47 on 2006-12-14
ok I did it again and got as far as sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist. I got a permission denied message. now what?

---

### Post by theturtlemoves on 2006-12-14
that howto seems to have a couple of errors. Try this.
```
echo "blacklist bcm43xx" | sudo tee /etc/modprobe.d/blacklist
```

Can't think why the author didn't fix that...

---

### Post by a3quit4s on 2006-12-14
Hey Stephen, I have the same Laptop any other problems with the install other than the Wireless?

---

### Post by Stephen47 on 2006-12-14
theturtlemoves: I'll give that a try and report back
a3quit4s: yes I am having resolution problems. See:[http://www.ubuntuforums.org/showthread.php?t=292152&page=3](http://www.ubuntuforums.org/showthread.php?t=292152&page=3)
Also it says: In a terminal, go to the directory where you extracted ndiswrapper.
how do I do that?

---

### Post by Stephen47 on 2006-12-15
bump
someone must be able to help me here

---

### Post by theturtlemoves on 2006-12-15
Start a terminal (Applications>Accessories>Terminal) and in it type "cd <directory>" where <directory> is the directory you want to go to.

---

### Post by Stephen47 on 2006-12-15
is my home folder a directory? if so when I run the cd command I get a no such file or directory message. do I use the brackets< >?

---

### Post by Fully216 on 2006-12-15
Yes, the home directory is a folder.  Within the directory structure of you system, it is located in /home/<your user name>/

If you downloaded ndiswrapper to your desktop, it will be found here:  /home/<your user name>/

You do not use the brackets.  Just put in the brackets the important information.  For example, my user name could be josh.  If that is the case, my home directory would be /home/josh/  so to get to it I would type 'cd /home/josh/' (without the apostrophes).

to find out where you currently are within the directory structure, just type 'pwd' which stands for print working directory.  You can find a list of other extremely useful commands at 

[http://www.computerhope.com/unix/uhelp.htm](http://www.computerhope.com/unix/uhelp.htm)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

Another note, you might want to read this to get you up to speed on some of the details regarding the command line interface (CLI)  [http://en.wikipedia.org/wiki/Command_line_interface](http://en.wikipedia.org/wiki/Command_line_interface)

---

