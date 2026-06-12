---
title: "Big problem with x servers"
date: 2015-10-30
forum: Hardware
---

### Post by dridrilamenace on 2015-10-30
[SIZE=2]Hi
So here's my problem:
I had to run my computer without the gpu (an nvidia geforce gtx 650ti), otherwise the screen would do as if the computer was not running) :([/SIZE]
That's because there wasn't any driver for it. So i downloaded the driver on the nvidia's website (the x86 352.55 version). I tried to run it by the the command
sudo nvidiaXXX.XX.run 
but it failed because I was running an x server. :mad:
 So I tried to exit the x server by using the following command:
sudo service lightdm stop
Then I tried to install the driver but it failed (it said that it failed to create something like "kernel". And now I can only use the terminal. I tried to restart with ctrl-alt-delete,but it says that the computer is running with low graphic mode and that I need to configure it. I tried the command:
sudo service lightdm restart
But the terminal says "failed to find a discrete vga device". ](*,)
Is there any way to solve this mess?
Thank you beforehand.
edit: I use ubuntu 15.10 64 bits if it can help...

---

### Post by Bashing-om on 2015-10-30
dridrilamenace; Hummmm ...

That card is well supported by Nvidia for us and the driver (352) is in our software repository.
We now have great tools for graphics:
post back - Between code tags - the outputs of terminal commands:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list
sudo find / -name "NVIDIA-Linux-*"
dpkg -l | grep -i nvidia

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

See what it will take to clean this up and install a driver.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dridrilamenace on 2015-10-30
The first command I wrote on the terminal was this one:
```
sudo nvidiaXXX.XX.run
```
And the others were like this:
```
sudo service lightdm stop
sudo service lightdm restart
```
I don't know if I was clear enough (if yes that's my fault, not your) but when I launch my computer I'm stuck on the terminal or on a window which tells me that the computer will run in low graphics mode because he doesn't recognize any GPU or VGA device :(
Btw: Thank you for code tag trick :)
edit 2: It's still imposible to run the PC with the GPU or the screen does as if it wasn't running.
I'll try tomorow these commands. And thanks for the help :)

---

### Post by Bashing-om on 2015-10-30
dridrilamenace; Hey ... 

Panic not, proceed in a calm and orderly manner.

All we have here is a problem within the X layer, the kernel remains intact ..

No you are following old guides - as you profess to be using 15.10 . 15.10's init system is systemd, and you are attempting to apply 'upstart' commands - systemd can not comply .

so, provide the requested outputs, let's see what the situation is, and then we consider what we can do to get the graphic's driver to properly install.
One can not install a different driver so long as an 'old' driver and it's config files is on the system.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by dridrilamenace on 2015-10-31
Good evening/morning.
I taped the outputs you suggested in the first reply.
The only driver that my computer found is the intel driver (his CPU is an intel core i3). And he didn't found any nvidia driver.

---

### Post by Bashing-om on 2015-10-31
dridrilamenace; Wheellll ...

That :
> 
The only driver that my computer found is the intel driver (his CPU is an intel core i3). 

If there exist a Nvidia card installed in that system, then it is turned off in bios.
Check in your bios settings what is going on. If the hardware is disabled in bios, the system will not see it.

When you post the requested outputs, we can be the more specific with offered advise.

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by dridrilamenace on 2015-10-31
Ah, this is the point were I wasn't clear.
When I (re)installed ubuntu, the graphics board wasn't plugged-in.

---

### Post by Bashing-om on 2015-10-31
dridrilamenace; Soooo ..

> 
When I (re)installed ubuntu, the graphics board wasn't plugged-in.


All good now ? Or are we back to clean up of the system in preparation in properly install the proprietary Nvidia graphic's driver ?

[INDENT][INDENT]what are we going to do
[/INDENT][/INDENT]

---

### Post by dridrilamenace on 2015-10-31
I think I'll tell you my story from the beginning.
First, I had ubuntu 14.04 32bits. I wanted to replace it by a 64 bits version. The driver was (I think) already outdated, so I already had to unplug the graphics board. I used unetbootin to install ubuntu 15.04 64 bits with the graphics board unplugged. Once the OS installation was complete I tried to do as someone suggested me to do 8 months ago in this thread:
[http://ubuntuforums.org/showthread.php?t=2260539](http://ubuntuforums.org/showthread.php?t=2260539)
But it didn't worked. Then after purging the drivers I tried to install the proprietary driver this way:
```
cd Téléchargements
chmod +x NVIDIA-linux*

sudo ./NVIDIA-linux*sudo
```
It didn't worked because "I was running an X server"
Then I used this code
```
sudo service lightdm stop
```
Then I retried to do the former commands but the instalation failed (it could not load the kernel said the terminal. And now when I turn on my computer I'm stuck whith a windows which tells:
"The computer is running on low graphics mode" and it invites me to configure it manually. and I can use also the terminal and the options that the window proposes.
Ask me if you want something more precise about one point.

---

### Post by Bashing-om on 2015-10-31
dridrilamenace; Well, then ...

In small steps to arrive at a conclusion.
Does the system see the Nvidia card now ?
```

lspci | grep "VGA\|3D"
sudo ubuntu-drivers devices

```


can do nada
[INDENT][INDENT][INDENT]'til it is there
[/INDENT][/INDENT][/INDENT]

---

### Post by dridrilamenace on 2015-11-01
I wrote the codes, here's the results for the first one:
```
00:02.0 [red]VGA[/red] compatinle controller:Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
```
And for the second command:
```
== cpu microcode.py ==
driver  :  intel-microcode - distro non-free
```
Keep in mind that I'm using another computer to write anything in this thread :oops:
edit: and it's still impossibble to run the computer with the graphics board plugged-in :(

---

### Post by Bashing-om on 2015-11-02
dridrilamenace; Hummm ...

Still no evidence of a Nvidia graphic's card.

Can not work with what is not identified, nor will the system work if directed to use hardware that it can not find. 

[INDENT][INDENT]what are we to do ?[/INDENT][/INDENT]

---

### Post by dridrilamenace on 2015-11-04
I read this thread: [https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)
I tried to load failsafe. I don't know if it worked but now, the computer is not running in low graphics mode anymore. The booting proceeds normally.
However, when I try to login to my session, there is a long loading time and at the end, there is a terminal screen which tells something but it last less than a second (I don't hace the time to read) and I'm back to the login screen.
Fortunately, I'm able to login to the console.
Is there anyway to solve this new problem?

---

### Post by Bashing-om on 2015-11-04
dridrilamenace; Sure !

> 
I'm able to login to the console.
Is there anyway to solve this new problem?


My thought process is always from the terminal ( as opposed to a console ) .
How about we look at this from terminal ?
To do so reboot the system and as soon as the bios screen clears depress and hold a shift key -> grub boot menu .
With the highest version kernel selected to boot, press the 'e' key for edit mode -> boot parameters screen.
Here arrow down to the line starting with linux and across to "quiet splash", replace these terms with the term "text" ( with out the quotes)- this is assuming you have 14.04 installed, else the boot parameter is different - 
key combo ctl+x to continue the boot process to terminal - TTY1.
Login here in this terminal with username and pass word, there is no response to the screen when the password is entered. enter password blindly and hit the enter key .

You are now the master of your system, you tell the system directly what to do . In this case we want the system to start the GUI layer so we see what the system reports. As you are now aware, the GUI is a very complex layer and many issues may effect it.

I do want to know that "you" are authorized to access your desktop.
What now returns:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
Now once affirmed that you are authorized, let's see what does result when we start that desk top environment:
```

sudo service lightdm start

```
observing for reported errors, maybe we get a good hint, if there are problems - as to where to go looking .. else, well my thought process is to look at the log files to see if the system tells us what is not going on.

There is not a thing wrong with using the link cited in your last .. We can use it as a common denominator in the prosecution of this issue, if that is the way you prefer to proceed. There are many paths to an end .

[INDENT][INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]to restoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dridrilamenace on 2015-11-04
Ok, I can't try for now, I'll tell you the results tomorow.
See you ;)

---

### Post by dridrilamenace on 2015-11-07
I have done the modifications that you suggested first (replacing "quiet splash" by "text"). Now when I try to login the black screen shows more commands (but I can't read then because it still lasts less than one second) before sending me back to the login screen.
For the commands on TTY1:
```
Xauthority:
-rw------1 login2 login2 59 nov. 5 20:09 .Xauthority
ICE:
-rw------1 login2 login2 15400 oct. 30 16:58 .ICEauthority
/home:
drwxr-xr-x  4  root  root  4096 spt. 26 17:55 .
drwxr-xr-x 24 root  root 4096 oct. 23 19:03 ..  
drwxr-xr-x 38 login2 login2 4096 sept. 26 17:20 login1
drwxr-xr-x 20 login2 login2 4096 nov. 5 20:09 login2
```
login1 is the one I used on ubuntu 14.04 32bits & login2 is the one I have on ubuntu 15.10 64 bits.
Edit: I changed the results of the commands. And I forgot to say  that "." ".." "login1" and "login2" which are at the end of each line are all in blue.

---

### Post by Bashing-om on 2015-11-07
dridrilamenace; Eurah ....

Let's see if we can unconfuse me. Are we dual booting ? else why are old 14.04 files still around .
Show us what we are working with:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```

login2 has no home directory ... ouch, what is going on here . We work to find out.

So what is the booting initiate system ?
```

ps -p1 | grep systemd && echo systemd || echo upstart

```

sometimes I do wonder
[INDENT][INDENT][INDENT]this time I just do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by dridrilamenace on 2015-11-07
I have done once more the command ls /home, I will edit the result in my former post.
I did all the commands you suggested today. There is a lot of informations that I don't understand shown on the terminal.

---

### Post by Bashing-om on 2015-11-07
dridrilamenace; Hey ..

> **dridrilamenace said:**
> I have done once more the command ls /home, I will edit the result in my former post.
I did all the commands you suggested today. There is a lot of informations that I don't understand shown on the terminal.

Show the outputs, and by all and any means let us discuss what ever you do not understand .
Never ever do anything you are not comfortable with; this forum also functions to teach.

[INDENT][INDENT]inquiring minds
[INDENT][INDENT][INDENT]need to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dridrilamenace on 2015-11-07
When I did
```
sudo fdisk -lu:
UnitsA: sector of 1 * 512=512 bytes
sector size (logical/physical):512 bytes/4096 bytes
I/O size (minimum/optimal): 4096 bytes/ 4096 bytes
```
And that's the first of the seven (or eight I don't know) that the terminal shows.

---

### Post by Bashing-om on 2015-11-07
dridrilamenace; Hey ...

I do not know ..

please show the command and the entire/complete/whole output.

[INDENT][INDENT]dancing in the dark
[INDENT][INDENT][INDENT][INDENT]is not fun
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dridrilamenace on 2015-11-07
```
sudo fdisk -lu:
UnitACsA: sector of 1 * 512=512 bytes
sector size (logical/physical):512 bytes/4096 bytes
I/O size (minimum/optimal): 4096 bytes/ 4096 bytes

Disk /dev/ram8A: 64 MiB, 671088 bytes, 131072 sectors
UnitACsA  :  sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O    size (mininmal/optimal): 4096 bytes / 4096 bytes
```
Next it shows 8 identical paragraphs (you just replace ram8A by ram9A and so on.
Then we have this:
```
Disk /dev/sdaA : 465,8 GiB, 50010786016 bytes, 976773168 sectors
UnitACsA  :  sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O    size (mininmal/optimal): 512 bytes / 512 bytes

Disk label type: dos
Dish identifier: 0*000d89ff

PACrefACrique AmorA§age   Start      Fin Sectors Size     Id Type
dev/sda1  *            2048 968454143 968452096 461,8G 83 Linux
dev/sda2          968456190 976771071 8314882       4G  5 extended
dev/sda5          968456192 976771071 8314880       4G 82 exchange partition Linux / Solaris
```
I have to rest (I live in Europe), so that's all I'll answer for today.
See you tomorow, and thanks for helping me ;)
Edit: "AC" propably means "é" (just a way to pronounce this vowel differently) and "A§" means "ç" (you pronounce the "C" like a "S").

---

### Post by Bashing-om on 2015-11-09
dridrilamenace; Well ...

It appears that ubuntu is installed to the hard drive, As to what is going on with ram ... 
> 
Disk /dev/ram8A: 64 MiB,

I have no idea of where that is coming from, or what is setting it up.

Your install medium, is that a desktop install ? Such that we have additional tools available in the live desktop environment from the liveDVD's boot menu to try and boot the install.
And/or (RE-)install grub to the hard drive.

[INDENT][INDENT]sometimes, I just do not know
[/INDENT][/INDENT]

---

