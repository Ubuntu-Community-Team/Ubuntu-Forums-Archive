---
title: "ATI Drivers Install"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by paradroid90 on 2009-04-13
Hi Guys and Girls.

Having Problems with Ubuntu 8.10. Installed yesterday and complete Newbie to Linux but had a problem installing ATI Card Drivers

Games like Open Arena,Scorched 3D,Nexiuz etc worked fine under the open source drivers but games like Free droid 3d and glest were glitchy as hell.

Then Installed the ATI Drivers via Hardware Updates and games lock up on the menu screens. But Freedroid and Glest run fine.

Already read on the forums that that ATI Drivers from AMD website are not the way to go.

Advice on this subect would be appricated.:p

---

### Post by silentrebel on 2009-04-13
I do not have the command with me now but I remember something along the lines of this:

sudo apt-get install envyng-gtk

This should help you find the best ATI driver for your card, in most cases.  Just choose the ATI option.  Then choose the driver that is compatible and recommended.  If such a driver is not suggested, you'll have to risk using one of the other offered drivers.  If I find any other useful information, I'll let you know.  Keep me posted.
Good luck.

---

### Post by paradroid90 on 2009-04-13
Hi,

Thanks for your response and i used your command line in terminal as instructed. Which worked and updated. But i still get glitches when running games like track balls for some reason. Have downloaded the lastest drivers from AMD site now and from what i have read in the forums so far that these drivers are the best to use. Bit baffled as im a newbie at Linux what the docs are refering to?????

If any one could help that would be great. Its listing the following

To install the ATI Proprietary Linux driver using the Automatic option, follow
these steps:
1 Launch the Terminal Application/Window and navigate to the ATI Propri-
    etary Linux driver download.
2 Enter the command sh ./ati-driver-installer-9.2-x86.x86_64.run to launch the
    ATI Proprietary Linux driver installer.
The ATI Proprietary Linux Driver Setup dialog box is displayed

Question is how do you navigate????

Must admit loving the change and i dont mind getting my hands dirty!!!!

:lolflag:

My Pc is

AMD Athlon 3800+ Dual Core
2GB Ram DDR2
X850XT Graphics Card 
ABIT-S62NX Motherboard

---

### Post by silentrebel on 2009-04-13
If you are asking how to navigate with the terminal here is a quick guide:

username@computer:~$
This is the prompt for navigating. *username *is the account in which you are. *computer *is the name of your computer.  Everything between the : and the $ is the current path.  ~ is short hand for this path : /home/username.

To navigate, use the cd command

cd place (to access a directory named *place* within the current path)
cd ..  (to open to the parent directory (up one level))
dir or ls (to list the files and directories in the current path)

That should get you started, I would suggest you search Google for basic ubuntu commands if you need more. 
This link is helpful too: [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php) 
If this isn't what you meant, let me know.

---

### Post by paradroid90 on 2009-04-14
Hi, and once again thanks for your response.

I am getting confused with terminal commands the ATI drivers are sitting on my desktop and i am typing the commands but i dont seem to get any response just keep getting cannot find file

Im Loving Ubuntu just messing about with Wine installed GTA,Starcraft and Red Alert and C and C which are working fine.

Ill get there

:lolflag:

---

### Post by silentrebel on 2009-04-14
The problem is that Bash (the terminal dude) is not very smart...  It will always assume you know what you are doing, executing devastating commands without a second thought and remaining silent unless it is terribly stuck.  It is for this reason that you have to tell it exactly where to look for a command, even if you are already there!

I assume that you cd'ed to your Desktop where you said the drivers are.  When you run commands like *cd*, *dir*, *mv*, *cp*, it looks for the specified command in special directories.  The same thing happens when you run a command like *nvidia-drivers* (for example).  *nvidia-drivers* is not in those special directories though; hence the error.  To get this to work you have to do the following from the directory of the drivers:

```
sudo chmod +x nvidia-drivers
```
where *nvidia-drivers* is the file you want to execute.  This command makes the file an executable.  This is the only way Ubuntu knows what to do with it as there is no *.exe* as in Windows.  

Next, use this command:
```
sudo ./nvidia-drivers
```
where *nvidia-drivers* is the file you want to execute.  The *./ * tells the bash to look in the current directory for the command (and not in the special directories).

I hope this helps, 
Let me know,
Good luck 
P.S. Be sure you read peyre's post below.  He seems to know more about this situation in particular than I.

---

### Post by peyre on 2009-04-14
Welcome aboard, paradroid!  I'm new too, though it looks like I have a slight head start on you, and also enjoying the Heron.  Thanks silentrebel; your instructions are better and probably more thorough than I could have given.

paradroid, one bit I'd like to add is about that one instruction that says "[FONT="Courier New"]Enter the command sh ./ati-driver-installer-9.2-x86.x86_64.run[/FONT]".  [font="Courier New"]sh[/font] is used for executing scripts.  That mysterious [font="Courier New"]./[/font] will be counterintuitive to someone coming from the DOS/Windows world.  Basically, you have to use that sometimes to execute something.  I think without it, bash assumes you were trying to type a command, and since it doesn't find a command by that name, it throws up its hands as if to say "I'm too lame to see if there's an executable in this folder instead." ;)

---

### Post by paradroid90 on 2009-04-18
Hi Guys,

Bit of an update!!!!

Got the installer running but now says i need to be SuperUser status???

Bit strange as i am the only account on my Linux Box and therories???

Thanks

:guitar::guitar:

---

### Post by paradroid90 on 2009-04-18
Dont worry been a bit thick lol

Have now latest ATI drivers Installed at last :D

Thanks for all your help!!!

Next question coming soon lol

---

### Post by peyre on 2009-04-18
That means it needs to run with root privileges.  This of course is part of the system that protects you from drive-by malware installs, among other things--preventing rogue processes from using your login to install themselves.

If you're running it in the command line, that means you need to precede your commands with sudo: e.g., [FONT="Courier New"]**sudo** install-with-all-these-ridiculous-switches[/FONT] instead of just [font="Courier New"]install-with-all-these-ridiculous-switches[/font].  If you're trying to open something from the GUI (meaning Thunar, the file manager), you can hit Alt-F2 (the equivalent of clicking Start, Run in Windows), and enter [font="Courier New"]gksudo thunar[/font].  You can also create a launcher that executes that command (I call mine "SUPER Thunar").  (gksudo is graphical sudo)

If you're using sudo or gksudo and it's still giving you that error, I can think of a couple possibilities.  One is that you might have fat-fingered your password (I do it occasionally).  The other is that somehow your account might not have rights to administer the system.   Open System, Users and Groups (or whatever the equivalent is in mainstream Ubuntu), unlock if necessary, then get Properties of your account and click the User Privileges tab.  Make sure "Administer the system" is checked.

---

### Post by paradroid90 on 2009-04-20
Hi Guys,

Im back again lol...........Installed the latest ATI Drivers from the Website but im getting alot of Mouse Lock Up's in certain game.

Games im having issues with are

World of Padman
Sauerbraten
Vegastrike - Strange this one wont boot then locks the mouse on desktop when returning to terminal on the desktop
Nexuiz
Open Arena - Locks up when i moved res upto 1024x768 from native
Warzone 2100 - Locks up also when gets to 1024x768

Used the Installers instructions as describe

Any help for the newbie would be appricated

:confused:

---

