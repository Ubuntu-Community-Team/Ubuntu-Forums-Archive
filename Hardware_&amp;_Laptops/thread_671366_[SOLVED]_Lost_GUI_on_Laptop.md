---
title: "[SOLVED] Lost GUI on Laptop"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by MacDuff on 2008-01-18
I thought I was past needing this kind of help but today I tried to attach a CRT monitor to my laptop.  When I switched the laptop to the CRT monitor everything worked but the resolution was only 800x 600.  When I tried to change the screen settings to those of the monitor I was using everything went to heck.

The computer is a dual boot Acer 1680  (Ubuntu 7.1 and Windows XP).  It boots  to windows fine but when I boot to Ubuntu I can get recovery mode but cannot get any of the suggested commands, to reconfigure the xserver, to work.  One error message told me I had no Xserver.org installed.

Can anyone tell me how to restore the Gnome GUI without having to re-install Ubuntu?

Thanks
Mac

---

### Post by jerrykenny on 2008-01-18
Next time you boot ubuntu edit the grum modeline . . . . press "e" after selecting it.

Remove the last option which i think says "splash"

hit enter, then "b" for boot . . . . 


next bit . . . . .


login (it'll be all text)

####sudo -s   (enter your password again)

####cd   /etc/X11/

#### ls

the command ls should list the files in the current folder, there will be xorg.conf . . . . . which is probably screwed, and hopefully xorg.conf.somethingelse   this might be a 4 digit number, or the word backup.


#### cp   xorg.conf   xorg.conf.dud
####  mv   xorg.conf.whatever    xorg.conf

good luck

---

### Post by MacDuff on 2008-01-18
Not sure what you mean by:
> edit the grum modeline . . . . press "e" after selecting it.
The system tries to boot three times then presents me with a command line 
" mac@Aspire1680: $ "

I was able to get to the X11 directory and the contents are:
app-defaults  xinit  xorg.conf.4     Xsession
cursors  xkb  xorg.conf.failsafe   Xsession.d
default-display-manager  xorg.conf   xorg.failsafe.1  Xsession.options
ron5w    xorg.conf.1  xorg.donf.failsafe.bak   Xwrapper.config
rgb.txt   sorg.conf.2  Xresources
X   sorg.donf.3   xserver

What do I do now as I am not sure what your last suggestions actually mean, sorry for my ignorance.
  
Mac

---

### Post by jerrykenny on 2008-01-18
Maybe i wasnt too clear, . . . . i want you to hover over the grub-ubuntu option, not to press enter, but press e instead . . . . 


failing that boot off your installation disk, but instead of just hiting enter, . . . . .   


type      rescue      then hit enter, this might let you boot into your old system . . . . make another attempt at the shuffling around xorg.confs

maybe even type apt-get update   then apt-get upgrade

---

### Post by jerrykenny on 2008-01-18
Hi Mac,    sorry, i see youve gotten in OK . .. 

there are lots of xorg.conf files in there, so probably your xserver, or possibly nvidia-settings has been creating new xorg.conf  files and backing them up anyway . . . . 

The file you really need to be intact is xorg.conf

the others are backups . . . . 

to create a new xorg.conf you can also try 

sudo dpkg-reconfigure xserver-xorg




if that seems to work, then type sudo gdm

---

### Post by jerrykenny on 2008-01-18
Still there ?

I should give an overview . . . . 

1  editing the grub option removes the useless-but-pretty red line which entertains you as the system boots up, . . . . . but it also obscures vital information about your system . . . . it also makes the text on your text screen so big it spills out all over the place.

2  Sudo -s  gives you the administrative power to change/edit/shuffle vital system files.

3  I'm fairly sure the absolutely vital file (xorg.conf) has been screwed, you need to either restore a previous version (which the cp command might do) or create a brand new one (which the sudo dpkg -high thngy will do)

If the above doesnt work, still dont despair, theres lots of other things to try, i'm just not sure what stage your at right now.

---

### Post by MacDuff on 2008-01-18
Thanks for the clarification,  Got it.

When I hit "e" I get a menu but it does not have "Splash" as the last line.  Just so I know we are on the same page, here is the menu:
root  (hd0,2)
kernel /boot/vmlinux-2.6.22-14-generic root =UUID=37515922-1b78=4828 ->
initrd /boot/initrd.img-2.6.22-14-generic
quiet

do you want me to deleted the line "quiet"

Mac

---

### Post by jerrykenny on 2008-01-18
No, quiet is OK, I'm surprised "splash" isnt there.

So can you confirm that you can boot the thing OK, and that the text screen you can see is OK ? and  readable ?  if so, can you log in as yourself, and it accepts you password ok ?

(it might not even prompt you to log in untill you hit <enter> )

STOP PRESS  WAIT  !!!

LOOK AT THE LINE THAT SAYS 

kernel /boot/vmlinux-2.6.22-14-generic root =UUID=37515922-1b78=4828 ->

i WANT YOU TO HOVER OVER THAT LINE AND PRESS "e" again,

pretty sure the option "splash" will be at the end of it.

delete it out, hit return once, then b" for boot.

---

### Post by MacDuff on 2008-01-18
It seems we have possibly been working at cross purposes.

I understand you want me to navigate to the /etc/X11 sub-directory and replace the existing xorg.conf with one of the other similar files. After I replace the original, I should re-boot Ubuntu, is that correct?  This will continue until I have found a file that will cause Ubuntu to boot properly, I assume.

The choices I have are:
xorg.conf.1
xorg.conf.2
xorg.conf.3
xorg.conf.4
xorg.conf.failsafe
xorg.conf.failsafe.1
xorg.conf.failsafe.2
xorg.conf.failsafe.bak

Presumably one of these will restore my previous GUI interface on the laptop LCD screen.  This may seem elementary but I make the assumption that I copy each of these in turn over top of xorg.conf, using the command you provided and assuming I want to  to replace xorg.conf with xorg.conf.1,  I would enter  "cp xorg.conf.1 xorg.conf"

Is that correct ?

Which of the above xorg.conf.xx files will be the most recent. Or put another way, which one should I start with to replace the xorg.conf file?

Mac

---

### Post by jerrykenny on 2008-01-18
Incidentally, i see you are dual booting, if you have the live cd, and you actually have networking capacity with the live cd, just boot with that, and we can proceed more directly . . .

---

### Post by MacDuff on 2008-01-18
OK jerrykenny I built this system using the alternate CD but I do have a live CD

I will boot up with that right now.

Mac

---

### Post by jerrykenny on 2008-01-18
Ace !  

look at your desktop for an icon that might represent your old ubuntu installation, there will probably als be one there for you windows partition,

if not dont worry, . . . . open your file browser and look in  /mnt  see whats there ?

---

### Post by MacDuff on 2008-01-18
I cannot find any icons on the Live CD desktop other than  "Examples" and "Install"

When I look in [Places] [My Computer] I can see Filesystem as well as CD=RW/DVD-ROM

Opening Filesystem mnt shows me an empty file

What next?

---

### Post by jerrykenny on 2008-01-18
open a terminal and type 

sudo -s          (try cut n paste)



 fdisk -l /dev/sda


then cut n paste the output here and i'll give you the next step:)

---

### Post by MacDuff on 2008-01-18
Sorry jerrykenny, but I cannot cut and paste because the computer I am having trouble with cannot be booted up or at least I do not know how since I cannot get a GUI.

I am using another computer to post messages to the forum.

Anyway when I tried your suggestion to fdisk -l/dev/sda the response was
" bash: fdisk-l/dev/sda: No such file or directory"

Mac

---

### Post by jerrykenny on 2008-01-18
Ok,  i thought the broken computer wouldve booted off the live cd but nevermind . . . . there needs to be spaces in the commands


so the broken  pc, . . . .

1/   is there just a black background with white text ?

2/  if so can you hit <enter> and get a prompt to login ?

3/  if so, then log in . . . . . 

4/  type   <  sudo     -s >    without the arrows

5/  put your password in again

6/  type    <   dpkg           -phigh        xserver-xorg    >    without the arrows

7/  type   <gdm>     without the arrows


If you get stuck at no1, ie the text is all over the place, you need to reboot, without the "splash" option, you almost had it just a while back, when you were into the grub menu . . . . you just needed to go down one line and press "e" for a second time.

---

### Post by jerrykenny on 2008-01-18
Cant you boot into single user mode ?  that should let you login and type the above commands

---

### Post by MacDuff on 2008-01-18
jerrykenny:

I did not seem to be getting anywhere.  In fact I was digging myself deeper into a hole.  I have the laptop working on the CRT monitor (sort of - I have lost my network configuration for some reason)  and I will try to re-configure the video settings so that I can use it on the laptop LCD screen.

If that does not work, I will blow Ubuntu out of the laptop and re-install it.

 VERY FRUSTRATING for you.... and me!

I appreciate your trying to help me but I guess I had better brush up on finding some way to manually set the video drivers as that seems to have been what started the problem.  It appears that Ubuntu cannot yet deal with two different monitors on a single system, or perhaps it is the Acer system that cannot deal with Ubuntu using two monitors.  Either way I have a problem.  I don;t want to return to Windows XP but if all else fails, I may have to.

Thanks again for your attempt to solve my problem

Mac

---

### Post by clsgis on 2008-01-18
> **MacDuff said:**
> Sorry jerrykenny, but I cannot cut and paste because the computer I am having trouble with cannot be booted up or at least I do not know how since I cannot get a GUI.

I am using another computer to post messages to the forum.

Anyway when I tried your suggestion to fdisk -l/dev/sda the response was
" bash: fdisk-l/dev/sda: No such file or directory"

Mac

I think you're having trouble typing commands into the shell prompt.  Probably because with the teensy little font this forum uses, you can't tell where the spaces are in the commands.  The command "fdisk -l /dev/sda" has three words in it.  The spaces in between the words are part of the shell grammar.  They are mandatory.
[SIZE="6"][FONT="Courier New"][B]
fdisk      -l      /dev/sda[/B][/FONT][/SIZE]

The first word is the name of the program you want to run.  The next word modifies its behavior.  When you run out of modifiers, the rest of the words are usually the names of the files you want the program to open.  The shell needs the spaces to break the line up into words.  In MS-DOS, the whole line is shown to the program just as it was entered, so every program has to know how to deal with file wildcards and stuff.  In unix, the shell processes the command line into a list of words.  It expands filename wildcards, and it can do a lot more complex labor-saving substitutions.

---

### Post by MacDuff on 2008-01-19
clsgis:

Thats one of the reasons why I love Ubuntu... the really excellent user support through the forums.  Actually, I am pretty sure that I did enter the command properly.  I have used Linux commands a number of times in the past without problem.  But I obviously did not transcribe it properly when replying to the post.  Frankly, transposing characters is more of a problem for me.

That was a great catch and when time permits later this weekend to get back to the problem, I will make sure the commands are entered properly.  

Paying close attention to the details, as you obviously did,  can save a user with a problem a huge amount of frustration.  It is particularly important with newbies because we are struggling with EVERYTHING and can easily make tiny errors that completely confuse us. 

Thanks.

Mac

---

### Post by jerrykenny on 2008-01-19
aaah good thinking CLS, I should've used a larger font at the start.

MacDuff, dont wipe ubuntu, as the problem is really very minor, . . . . . albeit tricky to sort. . . . anyway give this one shot

1/  Start ubuntu in SINGLE USER (is it called safe) mode - thats the 2nd option on you start screen

2/ Log in as yourself as soon as you are prompted.

type these commands (no capitals)

[SIZE="4"][B]sudo   -s

dpkg-reconfigure   -phigh   xserver-xorg

gdm
[/B][/SIZE]

---

### Post by MacDuff on 2008-01-19
Hi jerrykenny:

Just got back and tried your last suggestion.  Larger type face does help by the way.

On startup after the desktop loaded a message window appeared:
" Internal Error
Failed ti Initialize HAL! "

I re-started the computer and everything seems to be working just as I remember it.

You people who provide support on the Forums are a godsend to Ubuntu.  I cannot speak too highly of you.

FYI, it took me about three months of slugging to get comfortable with Ubuntu and of course I still don't know nearly enough, witness this recent problem, but I have installed Ubuntu on two friends hardware and they have not had any problems at all. They do not, however, make many demands on it other than web browsing, e-mail and occasional photo editing and CD burning. 

I, on the other hand, have pushed things pretty far and have been bitten a number of times.  However after the first three re-installs, I have always been able to find a fix on the forums and each time a problem is solved, I become a little bit more knowledgeable.    I have Ubuntu running on three of my computers and hope one day to dump Windows entirely.  I may have to use Windows virtual machines but have to wait until VMServer or Virtual Box can recognize USB ports.

I will put your instructions in my "panic" file so that if it happens again, I can refer to it.

Thank you so much for your help.

Mac

---

### Post by jerrykenny on 2008-01-19
Excellent,   since you obviously possess the attribute "perseverance" you'll make out Ok :)

incidentally, loss, or corruption of that particular file "xorg.conf" is a major achiles heel of the linux ditributions (imho) now that you've cracked it once. you wont be so worried next time.

And there will be a next time, its probably the biggest deal breaker out there for lots of linux adventurers.

Lets make your system a bit more future proof by making a perfect copy of that file

open a terminal and type the command

[SIZE="6"][B]
sudo  cp    /etc/X11/xorg.conf    /root/xorg.conf [/B][/SIZE]

That will make a perfect copy of the rather fragile file in a safe place . . . . . . if your system ever borks again, you can log into single user mode. and copy that clone back again by typing

[SIZE="6"]**sudo  cp    /root/xorg.conf    /etc/X11/xorg.conf**[/SIZE]

I'm glad you're spreading the word about ubuntu / linux, its a great new wave:)

---

### Post by MacDuff on 2008-01-20
Done! jerrykenny

I will do that later today on all three of my machines that are running Ubuntu.  I will also make note to suggest that to the people to whom I have introduced Ubuntu.

I guess we can mark this post "solved" thanks to you and a good suggestion from clsgis.

With the move to high resolution monitors, the default font is a trifle small, especially for people who have vision impairment.  However it is only a matter of pressing [Ctrl]-[+] to enlarge the type face to any size the viewer wants.  Remembering that feature is the problem, unless one uses it frequently.  After all my years of experience I still forget about it. 

Cheers
Mac

---

