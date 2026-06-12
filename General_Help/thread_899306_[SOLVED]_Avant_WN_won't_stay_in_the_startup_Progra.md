---
title: "[SOLVED] Avant WN won't stay in the startup Programs menu, what do I do?"
date: 2008-08-24
forum: General Help
---

### Post by kelinu on 2008-08-24
Hi,
My problem is when i put programs in the System->Prefernces->Sessions (when I close, restart, log off etc. the entry goes away.

How can I fix this? You see, I need AWN to start on startup.

MY problem is [like this guy's problem]("http://ubuntuforums.org/showthread.php?t=626767&highlight=programs+won%27t+stay+sessions")

Any Help is Much appreciated,
Thanks

---

### Post by gjoellee on 2008-08-24
does this happen with other programs?

---

### Post by kelinu on 2008-08-24
yes it does, gets very annoying

---

### Post by gjoellee on 2008-08-24
hmmm... lets try a "stunt" or just a test:)

add the programs to startup (in sessions), and keep them running, and then go to the "sessions options" tab, and and click on "remember currently running applications", and restart your machine. 

Hope it works! *crossing fingers*

---

### Post by kelinu on 2008-08-24
ok then i will see what happens
i will update you if it works

---

### Post by bthoward on 2008-08-24
Makes me wonder if somehow you may not own parts of your home directory.  Do you know how to check for that?

---

### Post by kelinu on 2008-08-24
nope it didn't work

no i don't know how to check for that, could you please tell me, thanks

---

### Post by gjoellee on 2008-08-24
> **kelinu said:**
> nope it didn't work

no i don't know how to check for that, could you please tell me, thanks

you may not be administrator! OMG, why didn't I think of that first!

Go to System->Administration->Users and Groups, and click on your account, and unlock it, then clock in your account again and click on properties. Does it look like this?

---

### Post by kelinu on 2008-08-24
ok i unlocked it an yes it does look like that, can i proceed to making awn startup automatically now?

---

### Post by gjoellee on 2008-08-24
well if your user account is an administrator you should, if not you may take a look an [www.launchpad.net]("http://www.launchpad.net") and report a bug

I am on a lookout for a fix :)

---

### Post by bthoward on 2008-08-24
try running "sudo chown <your username>:<your username> ~ -R"

---

### Post by kelinu on 2008-08-24
ok then, let me try i am not going to mark this thread as solved for now just in case someone else has a suggestion....thanks for the help

---

### Post by kelinu on 2008-08-24
It didn't work :( what do i do?

BOOHOO

---

### Post by bthoward on 2008-08-24
Don't mark as solved until you have it working...  But once you run that command it'll appear to have done pretty much nothing.  Then try changing your setting.

---

### Post by kelinu on 2008-08-24
> **bthoward said:**
> try running "sudo chown <your username>:<your username> ~ -R"

I did this and this is what it gave me:

> chown: cannot access `/home/michael/.gvfs': Permission denied


???

---

### Post by dje on 2008-08-24
if bthowards command fails to work try creating a new user from System >> Administration >>  Users and groups and try logging in as that user, adding awn to the startup and seeing if it sticks for that user

dje

---

### Post by dje on 2008-08-24
> **kelinu said:**
> I did this and this is what it gave me:



???

that error is normal, you can ignore it. does awn stick in your startup programs now?

dje

---

### Post by kelinu on 2008-08-24
I will try that, but if it does stick what is the use in knowing that, How can i get it to stick on MY user?

---

### Post by bthoward on 2008-08-24
It was supposed to fail there... Sorry I forgot to mention that..  But once you were done did you test things...

Instead of testing things like you were doing before do me a favor and try it this way.  From the console type "gnome-session-properties" and hit enter.  Then try to add AWN to the start up like you've been doing then when you're done look back in the console window and see if it said anything that may help us help you...  

I gotta get to bed here soon though...  I decided I needed to boost my number of Thanks' so I figured I'd post helping people for a few hours...  But now its 6AM here and I need to get some shut eye before the sun comes up!!! haha.

---

### Post by dje on 2008-08-24
> **kelinu said:**
> I will try that, but if it does stick what is the use in knowing that, How can i get it to stick on MY user?

if it turns out that you cannot get it to work on your user you can copy your files and settings over to the new user and use that. it's a last resort but it may be the only solution that works?

dje

---

### Post by kelinu on 2008-08-24
> **bthoward said:**
> It was supposed to fail there... Sorry I forgot to mention that..  But once you were done did you test things...

Instead of testing things like you were doing before do me a favor and try it this way.  From the console type "gnome-session-properties" and hit enter.  Then try to add AWN to the start up like you've been doing then when you're done look back in the console window and see if it said anything that may help us help you...  

I gotta get to bed here soon though...  I decided I needed to boost my number of Thanks' so I figured I'd post helping people for a few hours...  But now its 6AM here and I need to get some shut eye before the sun comes up!!! haha.

Hi,
I did this and this is what Mr.Terminal said:
> ** (gnome-session-properties:6838): WARNING **: Could not save /home/michael/.config/autostart/avant-window-navigator.desktop file


What in the world?

---

### Post by kelinu on 2008-08-24
HEHE a smiley came coincidence,

Here in malta its quarter to 3, time differences hehe

---

### Post by kelinu on 2008-08-24
> **dje said:**
> if it turns out that you cannot get it to work on your user you can copy your files and settings over to the new user and use that. it's a last resort but it may be the only solution that works?

dje

OK dje, only for last resort though...

---

### Post by dje on 2008-08-24
try running:
```
sudo chown -R $USER:$USER $HOME/.config/autostart
```

then running gnome-session-properties again and trying to add awn to startup

dje

---

### Post by bthoward on 2008-08-24
Ok so that error means that I'm a genius....  All kidding aside I think its still a permissions issue somehow....

Lets try navigating down into there...

in the console type "cd ~/.config/autostart/"
then try typing "touch myself"    #sorry that was the funniest file name I could think of right now...
then type "ls" do you see a file called "myself"?
If you do then something is odd.  Do you see a file already called avant-window-navigator.desktop? if so do an "ls -la" and paste the output of that command.

---

### Post by kelinu on 2008-08-24
> **dje said:**
> try running:
```
sudo chmod -R $USER:$USER $HOME/.config/autostart
```

then running gnome-session-properties again and trying to add awn to startup

dje

the outcome of that is this 

> michael@m-viz:~$ sudo chmod -R $USER:$USER $HOME/.config/autostart
chmod: invalid mode: `michael:michael'
Try `chmod --help' for more information.


---

### Post by bthoward on 2008-08-24
He meant chown not chmod...  (honest mistake)

---

### Post by dje on 2008-08-24
> **bthoward said:**
> He meant chown not chmod...  (honest mistake)

argh, thanks I'm not with it right now :D

dje

---

### Post by kelinu on 2008-08-24
ok i did it with chown, this is what came

> michael@m-viz:~$ sudo chown -R $USER:$USER $HOME/.config/autostart
michael@m-viz:~$ 


---

### Post by dje on 2008-08-24
> **kelinu said:**
> ok i did it with chown, this is what came

thats what should happen, try running gnome-session-properties and adding awn to startup now

dje

---

### Post by kelinu on 2008-08-24
I just tried adding AWN to the startup menu again, closed, opened the startup menu again and GONE.

No luck again BOOHOO

---

### Post by kelinu on 2008-08-24
Tried it with the terminal as well (gnome-session-properties), and this message came again:

> ** (gnome-session-properties:6918): WARNING **: Could not save /home/michael/.config/autostart/avant-window-navigator.desktop file

This is so annoying

---

### Post by bthoward on 2008-08-24
Actually hell lets try this...

Open a console then type "sudo gnome-session-properties" then do your thing.

---

### Post by kelinu on 2008-08-24
> **bthoward said:**
> Actually hell lets try this...

Open a console then type "sudo gnome-session-properties" then do your thing.

Outcome of that 
> michael@m-viz:~$ sudo gnome-session-properties
could not connect to the session manager


---

### Post by bthoward on 2008-08-24
So did you do as I asked before and look to see if that file in the .config directory already existed?

---

### Post by kelinu on 2008-08-24
No it doesn't exist...

---

### Post by bthoward on 2008-08-24
What happens if you go to that directory in a console and try to run "touch avant-window-manager.desktop"?

---

### Post by kelinu on 2008-08-24
which directory - .config?

---

### Post by kelinu on 2008-08-24
WHOOAH apparently there is an autostart, sorry guys! This is how a found it:

> [michael@m-viz:~/.config$ ls
autostart  epdfview  Screenlets  Trolltech.conf   user-dirs.locale
awn        gtk-2.0   totem       untitled folder
compiz     menus     tracker     user-dirs.dirs


---

### Post by bthoward on 2008-08-24
Do an ls -la and post that then do cd autostart and run ls -la again and post that too.

---

### Post by kelinu on 2008-08-24
> **bthoward said:**
> Do an ls -la and post that then do cd autostart and run ls -la again and post that too.

Hmmm....this what came

> michael@m-viz:~/.config$ cd autostart
bash: cd: autostart: Not a directory

---

### Post by bthoward on 2008-08-24
Ok thats your problem.  Type "cat autostart" and paste output.  This is looking very promising!

---

### Post by kelinu on 2008-08-24
> **bthoward said:**
> Ok thats your problem.  Type "cat autostart" and paste output.  This is looking very promising!

Output:

[email]michael@m-viz:~/.conf[/email]ig$ cat autostart
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Screenlets Daemon
Exec=/usr/local/share/screenlets-manager/screenlets-daemon.py
X-GNOME-Autostart-enabled=true
Name[de_DE]=Screenlets Daemon

---

### Post by kelinu on 2008-08-24
So you mean this looking good, promising, good/YEEEEEEEEEEEEEEEEEES!

---

### Post by bthoward on 2008-08-24
So some screenlets thing you were using was rude....  For now lets rename autostart.  Run "mv autostart autostart.old" 

Then you'll be able to add AWN using the gui tool.

Then click thanks on a post or two of mine.... ;)

---

### Post by kelinu on 2008-08-24
YEEEEEEEEEEEEEEEEEEEES IT STICKED!!!! THANKYOU SO SO MUCH!!!!!!!!!!!!

WOOHOO SO THIS MEANS I CAN GET SCREENLETS TO START UP AUTOMATICALLY AS WELL!!!


THANKS SO SO SO MUCH


oH YEA!!

---

### Post by bthoward on 2008-08-24
Thanks for the click....

Glad we could get you going.

---

### Post by kelinu on 2008-08-24
> **bthoward said:**
> Thanks for the click....

Glad we could get you going.


ThankYOU! :D:D:D

---

### Post by kelinu on 2008-08-24
Thankyou for all the help, marking this thread as solved now...

---

