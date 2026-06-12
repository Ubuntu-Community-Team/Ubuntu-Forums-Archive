---
title: "How to install *.bundle&quot; file?"
date: 2008-11-24
forum: General Help
---

### Post by kaushikashwin on 2008-11-24
i downloaded vmware which is with extension of bundle like "vmware.bundle".how to install it?am newbie to linux world n plss explain in detail.thnkx in advance

---

### Post by kaushikashwin on 2008-11-24
okay i figured it out

---

### Post by jakupl on 2008-11-24
please mark this thread as solved, you will find it under "thread tools"

---

### Post by munzli on 2008-11-25
and why not post the solution for the next person that's looking for this ;)

in a terminal
```
sudo sh VMware-Player-2.5.1-126130.i386.bundle
```

---

### Post by OpenThinking on 2008-11-25
> **munzli said:**
> and why not post the solution for the next person that's looking for this ;)

Thanks a lot! This was the info I needed!

---

### Post by 1oki on 2008-11-25
yeah same here! lol thanks!

---

### Post by ianormiston on 2008-12-02
Perfect - Thanks :-)

---

### Post by jhj614 on 2008-12-02
> **munzli said:**
> and why not post the solution for the next person that's looking for this ;)

in a terminal
```
sudo sh VMware-Player-2.5.1-126130.i386.bundle
```

Thanks to muzli!  It is important to share with others one's findings, which can save people a lot of time.

---

### Post by dasajed on 2008-12-24
Thanks munzli!

---

### Post by alixthedark on 2009-01-18
Thanks munzli! really helped!

---

### Post by killpotts on 2009-03-16
It doesn't work for me. I get this error:

```

sh: Can't open VMware-Player-2.5.1-126130.i386.bundle
```

I even tried downloading the 64 bit version instead, and that gave the same error. 

I even tried using dir to go through the directory and directly ctrl+shift+V -ctrl-shift-C the filename and it still wouldn't work, so I know I am typing the version right...:(

---

### Post by snova on 2009-03-16
> **killpotts said:**
> It doesn't work for me. I get this error:

```

sh: Can't open VMware-Player-2.5.1-126130.i386.bundle
```

I even tried downloading the 64 bit version instead, and that gave the same error. 

I even tried using dir to go through the directory and directly ctrl+shift+V -ctrl-shift-C the filename and it still wouldn't work, so I know I am typing the version right...:(

Where did you download it to? You must be in that directory before you can run the command. It should work if its in your home directory; but, for example, if it were on your Desktop you'd have to first:

```
cd ~/Desktop
```

Also, if you aren't sure what the filename is, just type the first few characters and press the Tab key, it will complete the rest.

---

### Post by Totonno on 2009-03-22
thank you for posting the incredibly easy solution for this issue :D

---

### Post by smurray on 2009-04-10
holy crap, I'm glad you posted that solution, after the second post I was about to go back to making the red spot on my forhead a little bigger...

---

### Post by monkeyslayer56 on 2009-04-23
> **munzli said:**
> and why not post the solution for the next person that's looking for this ;)

in a terminal
```
sudo sh VMware-Player-2.5.1-126130.i386.bundle
```

ya i found this on google since i had never seen  a bundle file before thanks for this incredibly easy solution

---

### Post by Out For Booty on 2010-03-17
i was able to install by double clicking the .bundle file  then right click -> open with -> sudo sh     that was the seemingly simpler way so you don't have to load terminal into the directories and then run after typing the name. 

Hope i helped

---

### Post by caoinan on 2010-04-05
Thanks, that was simple.

---

### Post by nickthrolson on 2010-04-16
thanks so much helped me a bunch not knowing a lot about terminal commands

---

### Post by AndrewRenn on 2010-04-25
Thanks munzli! :)

---

### Post by Tsu Dho Nimh on 2010-05-03
> **munzli said:**
> and why not post the solution for the next person that's looking for this ;)

in a terminal
```
sudo sh VMware-Player-2.5.1-126130.i386.bundle
```
I need to install a VMWare .bundle on a 64-bit system running 32-bit Ubuntu. Sudo sh doesn't work because of the mis-match.

How can I force architecture?

---

### Post by snova on 2010-05-03
> **Tsu Dho Nimh said:**
> I need to install a VMWare .bundle on a 64-bit system running 32-bit Ubuntu. Sudo sh doesn't work because of the mis-match.

How can I force architecture?

Until I realized you actually had a 64-bit machine I was going to suggest a soldering iron... that'll teach me to read more carefully. But what do you even hope to achieve with this? You can't run 64-bit code until you install a 64-bit operating system.

(dpkg can be made to install a package for the wrong architecture, but as this is not dpkg, but apparently an installer script, "forcing" it may well mean editing code somewhere.)

---

### Post by Tsu Dho Nimh on 2010-05-04
> **snova said:**
> Until I realized you actually had a 64-bit machine I was going to suggest a soldering iron... that'll teach me to read more carefully. But what do you even hope to achieve with this? You can't run 64-bit code until you install a 64-bit operating system.

(dpkg can be made to install a package for the wrong architecture, but as this is not dpkg, but apparently an installer script, "forcing" it may well mean editing code somewhere.)

I have 32-bit Ubuntu (9.04) installed on a 64-bit AMD system: nothing unusual there. The VMWare .bundle is also 32-bit software. 

Is there any way to convert the .bundle to something where architecture can be forced? If I can get past the install it should work. The older player was not a .bundle and I didn't have this problem.

---

### Post by snova on 2010-05-04
> **Tsu Dho Nimh said:**
> I have 32-bit Ubuntu (9.04) installed on a 64-bit AMD system: nothing unusual there. The VMWare .bundle is also 32-bit software.

Ah, sorry, I was confused on that part.

> Is there any way to convert the .bundle to something where architecture can be forced? If I can get past the install it should work. The older player was not a .bundle and I didn't have this problem.

As I understand it, it's a shell script. It's hardly a file format so much as it is an installer, much as any Windows .exe, albeit more easily edited.

Semi-broken software being at fault, there's no great solution I can suggest; I really don't know what to do here.

---

### Post by West201 on 2010-10-07
> **munzli said:**
> and why not post the solution for the next person that's looking for this ;)

in a terminal
```
sudo sh VMware-Player-2.5.1-126130.i386.bundle
```


Thanks !!! Just the info I needed :)

---

### Post by manishlogan on 2011-02-26
Thanks a ton for the solution.

---

### Post by clarke_iitg on 2011-03-23
please see the official description from ubuntu:

[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

---

### Post by mihirpatel12 on 2011-04-12
works perfect ..... thanks :popcorn: :)

---

### Post by utkatt on 2011-07-09
thanks a lot munzli :)

---

### Post by jasperytlau on 2011-07-22
Hey there, Im sorry. Im very new to Ubuntu and Im hoping to learn a lot more about it. I dont know what I have done wrong but I typed the sudo as Munzli said but it says cant open the file. Could someone please help me out. Thank you so much

---

### Post by Randymanme on 2011-11-16
I met a gentleman at last night's Ubuntu Round Table group who advised  me to right-click the package and tick it as executable (which it  already was), and then drag and drop it from the Nautilus window into  the terminal.  The terminal charted the path by default.  I prefaced the  path with  "sudo sh,"  hit "enter" and the VMware installer took care  of it from there.

In my case, the command was: '/home/randymanme/VMware-Player-3.1.5-491717.i386.bundle'

---

### Post by deboga on 2012-01-04
Thank you very much.

---

### Post by anton_bors on 2012-02-21
Also a big thx for you !!
:p

---

### Post by alfresco_0101 on 2012-03-25
Thanks a lot...save me couple of more pages to browse and find...

---

### Post by Gurmeet0108 on 2012-04-11
Same here... THNX A LOT [URL="http://ubuntuforums.org/member.php?u=141266"]munzli :):)
[/URL]

---

