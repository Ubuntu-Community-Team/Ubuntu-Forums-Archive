---
title: "HOW TO: Setup up Eggdrop IRC bot easily"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by anil_robo on 2009-01-02
I needed to setup an IRC channel bot and battled with it for almost a week. Finally I've done it and am pleased to share this hassle-free tutorial with the Ubuntu community.

** What this will do for you:**
1. Setup an IRC channel of your choice
2. Keep a bot nickname of your choice in the channel to keep it alive

** Tutorial begins here:**
1. First install eggdrop using apt-get or synaptic if you prefer that:
```
sudo apt-get install eggdrop
```2. Download the simple.conf file from here: [http://www.egghelp.org/files/conf/simple.conf.gz](http://www.egghelp.org/files/conf/simple.conf.gz) and unpack it.
```
cd ~
wget http://www.egghelp.org/files/conf/simple.conf.gz
gunzip simple.conf.gz
```3. Open the simple.conf file in your home directory with a text editor of your choice (vi, nano, pico whatever). I'll use nano in my example because that's what I'm most familiar with:
```
nano simple.conf
```4. Now we are editing the simple.conf configuration file. This simple file has very self-explanatory comments to explain what each setting does. Edit them to suit your needs. There are very few things you need to change, and each line has instructions preceding it. The only thing you **must** take care of is this line:
```
set username "user"
```Here, you should replace the user within the quotes to your local username in the Ubuntu. If you don't know your local username, you can use whoami command to find it :)
If you still need help with a particular line in the simple.conf file, please ask here and I'll try to answer.
5. For some reason, I could get eggdrop to work only from /usr/lib/eggdrop directory, and only as a regular user (sudo will not work). So let's make the eggdrop directory writable first:
```
sudo chmod 777 /usr/lib/eggdrop -R
```(777 is not the most secure setting but it's good to begin with. You should try to lower this number later and use the lowest number that works for you)
6. Now let's run eggdrop for the first time using the simple.conf file.
```
/usr/lib/eggdrop -m ~/simple.conf
```Notice closely the terminal for any errors. Also login to the IRC channel you created to see if the bot is actually there. If everything goes fine, Eggdrop will create the channel or join if it already exists, and will sit there nicely.
7. in the IRC channel, you will also be given instructions to prove your ownership of the bot. By default, you can send HELLO as a private message to the bot and it'll recognize your ownership. Remember to login to IRC using the same nickname as you defined in the simple.conf file in the bot owner section.
```
/msg yourbotname HELLO
```(replace yourbotname with the bot nick you set in the simple.conf file)
8. Now let's set this bot to start with the Ubuntu startup.
First make a shell script that starts eggdrop with your conf file:
```
 sudo nano /etc/init.d/eggbot
```Text editor will open up. Type this:
```
#!/bin/sh
Echo "Starting Eggdrop IRC bot..."
cd /usr/lib/eggdrop
sudo -u username eggdrop /home/username/simple.conf
```(remember to replace username with your user name in Ubuntu)
Press ctrl+O to write the file, and then ctrl+X to exit the text editor.
9. Now let's make the file executable.
```
 sudo chmod a+x /etc/init.d/eggbot
```
10. Finally let's tell the system about the new file named eggbot we put in /etc/init.d directory so it updates its information:
```
 sudo update-rc.d eggbot defaults
```That's it!

If you're like me (and don't know much about Linux) you want to restart your computer to see if it actually works. Always check the IRC channel to see if the bot showed up there.

If you can contribute anything to this thread, or want to ask any questions, go ahead.

Wish you a very happy and Ubuntuous new year 2009 :popcorn:

---

### Post by Kapli on 2009-01-04
Thanks so much for this tutorial I now have my but up and running.
Now I just need to configurate it further and add loads of scripts so it can do stuff :D

---

### Post by dlap on 2009-01-22
Dear,

When i notice "/usr/lib/eggdrop -m ~/simple.conf" at my ubuntu terminal its says --> bash /usr/lib/eggdrop: is a map

What happend ? can u help me ?

---

### Post by anil_robo on 2009-01-23
Sorry no idea about that error. I'd suggest you double-check your simple.conf file again to see any missing values or commented lines that may be causing a problem. If I were you, I would also go to #egghelp channel in IRC to talk to the experts. If you're still stuck, I can send you my configuration file and you can use it as a last resort.

---

### Post by dlap on 2009-01-23
The Simple.conf is not the problem, the command to start is the problem.

And im Using Kubuntu 8.10 desktop

---

### Post by eldergod on 2009-01-25
The binary on 8.10 is actually /usr/bin/eggdrop
I put that in my .conf file and call the eggdrop with:
eggdrop -m ~/simple.conf

Hope that helps.

---

### Post by dlap on 2009-01-25
> **eldergod said:**
> The binary on 8.10 is actually /usr/bin/eggdrop
I put that in my .conf file and call the eggdrop with:
eggdrop -m ~/simple.conf

Hope that helps.

Okay thanks i did it and command is working but now he says something about "Tcl"

> Tcl error in file 'home/dlap/simple.conf':
invalid command name "}"
while executing
"}"
(file "/home/dlap/simple.conf" line 97)
* CONFIG FILE NOT LOADED (NOT FOUND, OR ERROR)

whats up with the Tcl where do i install that ?

---

### Post by pandaking on 2009-02-12
> **dlap said:**
> Okay thanks i did it and command is working but now he says something about "Tcl"



whats up with the Tcl where do i install that ?

I get the same problem - what did you do to fix it?

---

### Post by Kamzi on 2009-06-22
How can I use this method with the original eggdrop.conf?

---

### Post by hellmitre on 2009-10-19
Man, this is embarrassing. I've got everything you've done to the simple.conf file in mine, I'm running the command correctly as it prints in the console that it's made 2 channels and there are zero users on the server. Clearly it's connecting to the wrong server. Could you post what your server list looks like, perhaps?

---

### Post by PsySc0rpi0n on 2009-11-21
Hello

I can't get my bot in my channel...

I have allready done the /msg hello command, and the bot says that i am the owner and bla bla bla but the bot doesn't get in the channel... (modes on channel are [COLOR=Red]+imnsdt-k[/COLOR])

Do i have to register PsyBot nick so that it can enter the channel??? If it is not registered and the channel asks for registration, shouldn't i recieve a messagem from chanserv that that nick can't join the channel because it's not registered???

The configs i have made in the config file are:

The ****** means that i have that set to what it should be... :)



```

## EGGDROP BOT CONFIGURATION ## 
 
# These lines load all the modules necessary for a simple channel bot. 
loadmodule channels 
loadmodule server 
loadmodule ctcp 
loadmodule irc 
loadmodule notes 
checkmodule blowfish


set admin "PsySc0rpi0n <*****@*****.com>" 

set owner "PsySc0rpi0n" 

set notify-newusers "PsySc0rpi0n" 
 
# User name - set this to your username on the shell. 
set username "PsySc0rpi0n"


# IRC network - set this to the name of the network your bot will be on. 
set network "PTNet"  [COLOR=Red]-don't know if is correct here or if it should be irc.ptnet.org[/COLOR]
 
# IRC network type - to allow eggdrop to function optimally on your IRC 
set net-type 5 
 
set nick "PsyBoT" 
set altnick "PsyBoTBaY" 

set realname "PsyBoT" 
 
# Server list - make a list of servers your bot should try to connect to. 
# You will need to change this to servers on your IRC network. 
set servers { 
  irc.PTnet.org:6667
  rccn.PTnet.org:6667
  EUnet.PTnet.org:6667
  madinfo.PTnet.org:6667
  netc2.PTnet.org:6667
  netc1.PTnet.org:6667
  telepac1.PTnet.org:6667
  esoterica.PTnet.org:6667
  ip-hub.ptnet.org:6667
  nortenet.PTnet.org:6667 
} 
 
# Channels - you need to create a "channel add" setting for each channel 
# you want the bot to be on.
# Each channel add has options to configure how your bot should act on the 
# channel: 

# Flood settings can be set to 0:1 to disable detection. 
 
channel add #PsySc0rpi0nPrE { 
  chanmode "+imnsdt-k" 
  idle-kick 0 
  flood-chan 1:2 
  flood-join 0 :1
  flood-ctcp 0 :1
  flood-deop 0 :1
  flood-kick 0 :1
} 
 
# Additional channel settings - these further determine how the bot should 
# act on the channel(s) it's on. These settings are switched on/off using 
# the + or - symbol. + (plus) switches the option on, - (minus) switches it 
# off. 
 
channel set #PsySc0rpi0nPrE +enforcebans -dynamicbans -autoop -bitch +protectops +stopnethack +revenge 
 
 
# User file - set the filename for your bot's userfile. 
set userfile "PsyBoT.user" 
 
# Channel file - set the filename for your bot's chanfile. 
set chanfile "PsyBoT.chan" 
 
# Notes file - set the filename for your bot's notes file. 
set notefile "PsyBoT.notes" 
 
# These lines specify the logfiles the bot should keep. The first line 
# makes the bot to log all bot activity to the file "nicebot.log". The 
# second line makes the bot log all activity on the channel "#yourchan" to 
# "#yourchan.log". You can have up to five log files. If you don't want the 
# bot to keep log files, delete the three lines below. Otherwise, make sure 
# you change the channel names to the channel(s) your bot will be on. 
logfile mcobxs * "PsyBoT.log" 
logfile jkp #eggheads "#PsySc0rpi0nPrE.log" 
logfile jkp #PsySc0rpi0nPrE "#PsySc0rpi0nPrE.log" 
 
# TCL scripts - specify any TCL scripts you wish to load. 
source scripts/alltools.tcl 
source scripts/action.fix.tcl 
 
 
## THAT'S IT! ##http://ubuntuforums.org/showthread.php?t=1028042 
 
 
## Don't edit below unless required ## 
 
set help-path "help/" 
set hourly-updates 02 
set init-server { putserv "MODE $botnick +i-ws" } 
set ctcp-mode 2 
set double-mode 0 
set double-server 0 
set double-help 0 
unbind dcc n tcl *dcc:tcl 
unbind dcc n set *dcc:set 
unbind dcc n simul *dcc:simul 

```

---

### Post by roggaro on 2009-11-29
> **dlap said:**
> Okay thanks i did it and command is working but now he says something about "Tcl"



whats up with the Tcl where do i install that ?

i see that there is a couple who gets this problem, you did use apt-get install eggdrop? or the synaptic package manager?

the problem is that it doesn't find the modules, i'm currently looking for a way to fix this easy, so i'll get back to you as soon as i find a fix :)

---

### Post by DoHan on 2010-02-15
Hello and thank you very much for this tutorial! It helped a lot to get on the way with eggdrop but I needed to adjust it on the run to get eggdrop running with 9.10 server as base system. I would like to point out the necessary changes and comments that will ease your day significantly here.

First of all, it seem, that the delivered package eggdrop is broken. It does not work out of the box for some obvious reasons. The different files are stored in folders, where the binary does not expect them. So you get errors in the startup process.

Before posting the solution, that might help, just a short note on what I wanted to achieve. I created a designated user to run eggdrop and nothing else with very limited access. The sole purpose of this user is to get the bot up and running and grab th log files for later checking. This is of course not needed, it should work with any non-root userm, but I would recommend this way of handling to not risk problems with your main account if your bot gets hacked some day for some whatever reason.

So now to the adjustments. All you need to do is to grab the needed files of different directories and put them in your document root of your designated eggdrop user. Since I do not like to make copies of existing files, that might be changed in later updates, I just do symbolic links to the files to make the eggdrop binary find what it searches for in the right place.

```

ln -s /usr/lib/eggdrop/modules /home/youruser/modules
ln -s /usr/share/eggdrop/scripts /home/youruser/scripts

```Now, to get your eggdrop to run actually, you need to adjust your loading script a little.

```

#!/bin/sh
Echo "Starting Eggdrop IRC bot..."
cd /home/youruser
sudo -u youruser eggdrop /home/youruser/simple.conf

```

That should do the trick for those with problems here. The scripts folder adresses the missing Tcl scripts. I am sure, from efficiency point of view, one can clean the way to achieve that. My linux knowledge is limited. So I offer a way it works, you find a way to make it look good. :P

Greetings DoHan

---

### Post by pehden on 2010-07-06
Thanks to this I got mine working now only issue i have is making it restart with having to reboot the server.

> 

```

ln -s /usr/lib/eggdrop/modules /home/youruser/modules
ln -s /usr/share/eggdrop/scripts /home/youruser/scripts

```Now, to get your eggdrop to run actually, you need to adjust your loading script a little.

```

#!/bin/sh
Echo "Starting Eggdrop IRC bot..."
cd /home/youruser
sudo -u youruser eggdrop /home/youruser/simple.conf

```



---

### Post by DoHan on 2010-07-06
Hello pehden,

maybe first, I am not entirely sure, what you want to achieve. If I understood you right, you either want to restart the bot without having to restart the server, or you want to make it start automatically after you restarted the server. The first is simple:

Just kill the process and restart as done in the script.

```
ps aux | grep eggdrop
```

from there, grab the pid of the process and do

```
sudo kill pid
cd /home/youruser
sudo -u youruser eggdrop /home/youruser/simple.conf
```

The second is even more easy. It just needs a symbolic link in your /etc/rc2.d/

```
sudo ln -s /etc/init.d/eggdrop /etc/rc2.d/S99eggdrop
```

That will automatically start the script on bootup of your machine in runlevel 2, the default runlevel of Ubuntu Server. Make sure, the number after the S is higher than the one of your irc server to start. You'll find it there as well, in case you start one. This way, you make sure, the bot does start after the server is running. The higher the number, the later the processing of the script.

For the order freaks like me, I have adjusted the whole scenario a little for better overview and to get the linking a bit in place. For that I did the following:

First, I do not start the bot from a home directory anymore, but from the main bot directory /usr/share/eggdrop. I put a symlink to the needed modules in that directory and give it to the user, that should run the bot later. Furthermore, I placed the conf script under /etc/eggdrop. And thirdly, I adjusted the config file to put all logging to /var/log/eggdrop. Make sure, your user has at least write permission on that folder. The adjustments in short:

```
sudo ln -s /usr/lib/eggdrop/modules /usr/share/eggdrop/modules
chown -R eggdrop:eggdrop /usr/share/eggdrop
chown eggdrop:eggdrop /var/log/eggdrop
sudo mkdir /etc/eggdrop
```

Now copy your simple.conf to /etc/eggdrop and make sure, it is readable by your user. Then check the config and redirect your logging to /var/log/eggdrop

```
# These lines specify the logfiles the bot should keep. The first line
# makes the bot to log all bot activity to the file "nicebot.log". The
# second line makes the bot log all activity on the channel "#yourchan" to
# "#yourchan.log". You can have up to five log files. If you don't want the
# bot to keep log files, delete the three lines below. Otherwise, make sure
# you change the channel names to the channel(s) your bot will be on.
logfile mcobxs * "/var/log/eggdrop/eggdrop.log"
logfile jkp #channel1 "/var/log/eggdrop/#channel1.log"
logfile jkp #channel2 "/var/log/eggdrop/#channel2.log"
```

Finally adjust the startup script accordingly:

```
#!/bin/sh
Echo "Starting Eggdrop IRC bot..."
cd /usr/share/eggdrop
sudo -u youruser eggdrop /etc/eggdrop/simple.conf
```

Nothing of that really alters anything. The only benefit is, that things are better in place and where they would be expected. You find the confid file in your /etc directory, the logs in your /var/log directory and you don't need to put all in your user's home folder. You will find all remaining things in your /usr/share/eggdrop directory from there. I even went as far as putting that as home directory for my eggdrop user. But that's cosmetics.

I hope, this was a little help in getting a little structure into the eggbot. It is still a little tricky in the new Ubuntu 10 server as well, but should work fine as outlined here as well.

Greetings DoHan

P.S.: Still not a linux guru, so if you find anything to dso better, be incvited to share. ^^

---

### Post by karthick87 on 2010-11-06
Tried but got this error:

```
karthick@Ubuntu-desktop:~$ sudo /usr/lib/eggdrop -m ~/simple.conf
sudo: /usr/lib/eggdrop: command not found

```

---

### Post by DoHan on 2010-11-06
> **getyourkarthick said:**
> Tried but got this error:

```
karthick@Ubuntu-desktop:~$ sudo /usr/lib/eggdrop -m ~/simple.conf
sudo: /usr/lib/eggdrop: command not found

```

Hello,

as I see, you try to start with your local user, which of course is fine, unless you created a specific user for eggdrop, which is recommended. If starting is as the user, you logged in with, do the following:

```
/usr/share/eggdrop/eggdrop -m ~/simple.conf
```

Do not start the bot with superuser, so sudo without any user given. It will run with root priviliges, which is neither needed, nor recommened, but opens your system up wide.

---

### Post by karthick87 on 2010-11-06
Cant run 
```

karthick@Ubuntu-desktop:~$ /usr/share/eggdrop/eggdrop -m ~/simple.conf
bash: /usr/share/eggdrop/eggdrop: No such file or directory
```

---

### Post by DoHan on 2010-11-06
Sorry, my fault, still not awake here,

try the following please:

```
cd /usr/share/eggdrop
/usr/bin/eggdrop -m ~/simple.conf
```

If that does not work, check, if eggdrop is installed at all.

```
whereis eggdrop
```

If it is installed, it will show you all directories assigned to the bot. Otherwise, it will just show eggdrop: and nothing else. In case, it is not installed properly, please follow this guide from scratch on how to install and set it up. Thanks.

---

### Post by karthick87 on 2010-11-06
Getting error this time

```
karthick@Ubuntu-desktop:~$ cd /usr/share/eggdrop
karthick@Ubuntu-desktop:/usr/share/eggdrop$ /usr/bin/eggdrop -m ~/simple.conf

Eggdrop v1.6.19+SSL (C) 1997 Robey Pointer (C) 2008 Eggheads
[21:15] --- Loading eggdrop v1.6.19+SSL (Sat Nov  6 2010)
[21:15] Can't load modules channels: /usr/share/eggdrop/modules/channels.so: cannot open shared object file: No such file or directory
[21:15] Can't load modules server: /usr/share/eggdrop/modules/server.so: cannot open shared object file: No such file or directory
[21:15] Can't load modules ctcp: /usr/share/eggdrop/modules/ctcp.so: cannot open shared object file: No such file or directory
[21:15] Can't load modules irc: /usr/share/eggdrop/modules/irc.so: cannot open shared object file: No such file or directory
[21:15] Can't load modules notes: /usr/share/eggdrop/modules/notes.so: cannot open shared object file: No such file or directory
[21:15] Tcl error in file '/home/karthick/simple.conf':
[21:15] invalid command name "channel"
    while executing
"channel add #eggheads {
  chanmode "+tn-k"
  idle-kick 0
  flood-chan 10:60
  flood-join 5:60
  flood-ctcp 3:60
  flood-deop 3:10
  flood-kick 3:10
}"
    (file "/home/karthick/simple.conf" line 99)
[21:15] * CONFIG FILE NOT LOADED (NOT FOUND, OR ERROR)
karthick@Ubuntu-desktop:/usr/share/eggdrop$ 
```

---

### Post by DoHan on 2010-11-06
Try that one:

sudo ln -s /usr/lib/eggdrop/modules /usr/share/eggdrop/modules

And please be so kind and set your eggdrop up as is described here, for I keep pasting snippets of this very topic, so simple reading might solve your issues and get it to work. Thanks.

---

### Post by karthick87 on 2010-11-07
Now the module is loaded but still something goes wrong,,

```
karthick@Ubuntu-desktop:/usr/share/eggdrop$ /usr/bin/eggdrop -m ~/simple.conf

Eggdrop v1.6.19+SSL (C) 1997 Robey Pointer (C) 2008 Eggheads
[09:54] --- Loading eggdrop v1.6.19+SSL (Sun Nov  7 2010)
[09:54] Module loaded: channels        
[09:54] Module loaded: server          
[09:54] Module loaded: ctcp            
[09:54] Module loaded: irc             
[09:54] Module loaded: notes            (with lang support)
[09:54] Module loaded: blowfish        
[09:54] Creating channel file
[09:54] Couldn't create channel file: nicebot.chan.  Dropping


STARTING BOT IN USERFILE CREATION MODE.
Telnet to the bot and enter 'NEW' as your nickname.
OR go to IRC and type:  /msg NiceBot hello
This will make the bot recognize you as the master.

[09:54] * CAN'T WRITE TO TEMP DIR
karthick@Ubuntu-desktop:/usr/share/eggdrop$ 

```

---

### Post by Jebajseti on 2011-12-08
[COLOR=Black]sudo apt-get install tcl8.3-dev doesnt install for me anymore on oneiric, 
since package doesnt exist anymore. Any clue on that?[/COLOR]

---

