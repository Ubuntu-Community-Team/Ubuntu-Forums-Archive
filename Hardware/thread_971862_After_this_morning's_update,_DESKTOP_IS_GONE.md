---
title: "After this morning's update, DESKTOP IS GONE"
date: 2008-11-05
forum: Hardware
---

### Post by inverseroom on 2008-11-05
I'm running 8.10 on an HP dv1000.  I have never had a problem with this laptop before, and have been running Intrepid completely smoothly for weeks.  This morning a large update came through update manager requiring restart, and when I restarted, only my desktop image came up.  No GUI otherwise.  When I hold down the power button, I do get the restart/shut down/suspend/hibernate dialogue.  I have restarted three times, and each time the desktop is blank.

One other possibly relevant thing.  After the updates were downloaded, but before I restarted, I opened up Evolution, and I got a dialog: "Do you want to make Evolution your default email client?"  This gave me pause.  Evolution always has been exactly that, and has never asked me this before.

Please help!  I am something of a novice in the shell and don't even know how to access it in this situation, let alone what to type into it.

---

### Post by inverseroom on 2008-11-05
Should I burn an install disc and reinstall Ubuntu?  Will my home folder be retained if I do?  I have it backed up, but the last backup was about a two weeks ago--not smart, I guess.

---

### Post by malleus74 on 2008-11-05
You could always dd over your home folder or tar it up before you start trying to reinstall from the command line.

Just do a search on the forums and there's a lot better info on both ideas than I could give you :)

---

### Post by a2lkulkarni on 2008-11-05
Are you able to boot in single user or safe mode?

---

### Post by inverseroom on 2008-11-05
I'm afraid I don't know how to...does it work like in Windows, hold ctrl while booting?

Not sure what "dd over" the home folder means, can you explain?

---

### Post by Gizkaguy on 2008-11-05
> **inverseroom said:**
> I'm afraid I don't know how to...does it work like in Windows, hold ctrl while booting?

Not sure what "dd over" the home folder means, can you explain?

He means use the dd command in the terminal. Open a terminal (If GNOME, Applications -> Accessories -> Terminal) and type "man dd."

This will give you an explanation on it.

There should be a safe boot-like option in GRUB.

---

### Post by ktemkin on 2008-11-05
I wouldn't necessarily jump ship yet.

Can you:

1) Press CTRL+ALT+F(1-6) to access a virtual terminal?
2) Press ALT+F2 in GNOME to access the run dialog box?

---

### Post by jimv on 2008-11-05
Did you try a failsafe gnome session?  You can choose it from the login screen where you type your username/password.

---

### Post by inverseroom on 2008-11-05
> **ktemkin said:**
> I wouldn't necessarily jump ship yet.

Can you:

1) Press CTRL+ALT+F(1-6) to access a virtual terminal?
2) Press ALT+F2 in GNOME to access the run dialog box?

OK, yes, that got me into the terminal.  I want to clear up a misunderstanding though--my home folder is probably perfectly fine.  That's where I keep my desktop image, which comes up when the computer boots.  The desktop image is there, but no task bar, no icons, etc.  Just the blank desktop image.

I only asked about the home folder because I'm wondering if I can reinstall the OS without erasing my files and settings.  I'm certain it's all there, it's just that GNOME isn't starting up.

I'm in recovery mode now and will try to dpkg.

---

### Post by inverseroom on 2008-11-05
dpkg moved some stuff around but didn't fix the problem...let me try the failsafe GNOME session...

---

### Post by inverseroom on 2008-11-05
Sorry, I can't find a way into the failsafe GNOME session?

It's very strange.  keyboard shortcuts work--I can get a login/logout screen, I can get the restart/hibernate/suspend screen; the cursor appears and I can move it around.  But there is nothing on the desktop.

---

### Post by inverseroom on 2008-11-05
Reinstalled GNOME from the shell.  Nothing.

---

### Post by inverseroom on 2008-11-05
OK, sorry to belabor this.  From the shell I used ls to check for all my files.  They are all still there.  "ls Desktop" actually showed me the files that I know are sitting on my desktop.  But when I boot, their icons, and the panel, do not appear on the screen.

Could someone tell me specifically what command to type to copy my entire home folder to my backup drive, so I can reinstall 8.10?  Or maybe one of you has some way to restore my desktop...or can I run the backup utility from the shell?

---

### Post by anamorgan on 2008-11-05
Run your pc in safe mode and delete ubintu. Then restrat and reinstall ubuntu, u=i have faced some errors initially using ubuntu too.

---

### Post by issih on 2008-11-05
To copy your home directory you want something like :

```
cp -r ~/* /backup/location
```

however before you go too crazy lets just try something simple, does alt+F2 bring up the run dialog window?

If so try running some things from there.g. type "firefox" and see if it runs.

Also try running gnome-panel from that dialog, with a bit of luck that might give you back your menu's if not your desktop.

If that can't be done then you will need to do these things from the failsafe terminals, but thats a bit trickier.

Let us know how it goes

---

### Post by inverseroom on 2008-11-05
I'm afraid alt+F2 doesn't have any effect.  Can I run gnome-panel from the terminal?

---

### Post by mgangav on 2008-11-05
you should be able to run gnome-panel from the terminal.

Actually, I think I had a problem like this myself after an upgrade. I ended up having to move my xorg.conf file to another location, restart Ubuntu in recovery mode and repair x-server (or something like that).

Can you log into any other accounts normally?

---

### Post by inverseroom on 2008-11-05
My setup is pretty simple--only one account, and I have everything set to log me in automatically.  I just tried xfix (?) in recovery mode and no dice.  I've been trying to run gnome-terminal from the virtual terminal but get a "cannot open display"...when try another program such as firefox it's "no display specified."

---

### Post by mgangav on 2008-11-05
Before trying xfix, did you shift your xorg.conf file to another directory? This is to try to get the computer to think that the xorg.conf file is missing, and the run xfix in recovery mode.

You could make a new directory under /etc/X11 called backup or something then (within /etc/X11) ```
cp xorg.conf ./backup/
```
Then, run xfix under recovery mode.

Also, just for curiosity, are you running Ubuntu 8.10 Intrepid Ibex?

---

### Post by inverseroom on 2008-11-05
Yes, I am running 8.10.  I installed the RC a couple of weeks ago and it was going fine until this morning's updates.

I'd be grateful if you'd walk me through the process you're talking about there, mgangav.  I'm not comfortable enough in the shell to do it right given the way you're describing it.

That said, I'm seriously leaning toward a fresh install, then a simple-backup recovery from the backup I made a couple of weeks ago.  I think this is all the result of a failed attempt to fix the slow scrolling in Firefox--I couldn't install the packages for some reason, and I suspect something went missing.

Ideally, I would be able to run simple backup from the shell, then get to restore my current home folder after a fresh install.  Anyone know how to do this?

---

### Post by issih on 2008-11-06
If you want to try running graphical apps from the failsafe terminals you need to prefx any command with: "DISPLAY=:0.0"

try running:

```
DISPLAY=:0.0 gnome-panel
```

to see if that fixes anything.

---

### Post by inverseroom on 2008-11-06
Excellent, thank you!  I'm not at home but will try this after work.

---

### Post by InfiniDimm on 2008-11-06
I'm having a similar problem, just updated to Ibex recently and had some troubles with my ATI Radeon 9700 drivers. I had it working fairly well but when i tried to change the resolution things went... wrong. 
After logging in the screen gets completley blurry and totally useless. I have been trying to reset the resolution to the previous one using xrandr from the failsafe terminal, but get various error messages. When trying to do it from the log-in screen by pressing Ctrl+Alt F1 i get "Can't open display"

When starting up the machine i get a message saying (EE) No devices detected, and the option to use old config-files, try to reconfigure the stuff myself etc. The xserver log-file gives ends with "Fatal server error: no screens found"

I've tried "sudo dpkg-reconfigure xserver-xorg" with no luck, and i'm running out of imagination.. Oh, the DISPLAY=:0.0 gnome-panel returned 
No protocol specified
Can't open display

I tried running xfix from the recovery mode (do you get any kind of confirmation of the outcome of the xfix-process) but it didn't do me any good. still the blurry picture when logged in.

Suggestions?

---

### Post by mgangav on 2008-11-06
> **inverseroom said:**
> Yes, I am running 8.10.  I installed the RC a couple of weeks ago and it was going fine until this morning's updates.

I'd be grateful if you'd walk me through the process you're talking about there, mgangav.  I'm not comfortable enough in the shell to do it right given the way you're describing it.

That said, I'm seriously leaning toward a fresh install, then a simple-backup recovery from the backup I made a couple of weeks ago.  I think this is all the result of a failed attempt to fix the slow scrolling in Firefox--I couldn't install the packages for some reason, and I suspect something went missing.

Ideally, I would be able to run simple backup from the shell, then get to restore my current home folder after a fresh install.  Anyone know how to do this?
Sorry for being so vague in my reply. Here is what I did to fix my problem:

I) I moved my xorg.conf file to a backup folder to fool Ubuntu into thinking that it was missing. I eneter the following at the terminal:
```
cd ./etc/X11
```
then, I made a folder called backup (It may ask you for a password)
```
sudo mkdir backup
```
then, I moved xorg.conf to the newly made backup folder:
```
sudo cp xorg.conf ./backup
```

II) Now after doing all this, I restarted the computer, and went into recovery mode during the boot process. After that, I choose the xfix option. When xfix finished, I choose to continue the regular boot process. Even I after this, the desktop was acting a bit strange, so I rebooted the computer again. Every thing was back to normal after this.

Hope this helps!!!

---

### Post by jimv on 2008-11-06
Ok, to do the Gnome Failsafe session:

While you're on the login screen, click Options on the bottom left, then click Select Session...

Select Failsafe GNOME, and click Change Session.  Then login.

---

### Post by Kamilion on 2008-11-06
hmmm...
I remember seeing something similar in LP bugs.

There was an update for compiz in proposed that made it to mainline today that blacklists two intel graphics chipsets that are currently known to crash with this symptom.

try this from the shell:
```
sudo apt-get update && sudo apt-get upgrade
```

That should sync updates then pull down the new packages and install them.

Your desktop effects will be disabled until the problem is resolved with compiz/intelgfx drivers, but you should be able to login.

Bug #259385: Intrepid Compiz hangs on login for i830MG and i845 video cards
[https://bugs.launchpad.net/ubuntu/+bug/259385](https://bugs.launchpad.net/ubuntu/+bug/259385)

Bug #259385: i830MG/i845 Blacklist committed to intrepid-updates:
[https://bugs.launchpad.net/ubuntu/+bug/259385/comments/95](https://bugs.launchpad.net/ubuntu/+bug/259385/comments/95)

If that doesn't resolve the problem, try removing compiz:
```
sudo apt-get remove compiz && sudo apt-get remove compiz-core
```

If you still can't get it to work, download & burn the intrepid ISO, 'try ubuntu' and then you can find your harddrive in the places menu to copy your home folder to a drive/partition that won't be reformatted while you reinstall. Don't be afraid to right click on folders and "Create Archive" to compress them if you need to.

Hope this helps!

---

### Post by inverseroom on 2008-11-06
Hi everyone---well, I tried everything, and none of it worked.  The only thing that came close was running gnome-panel from the shell...that "DISPLAY" tip did the trick.  But it didn't take.  In fact, it enabled me to discover that all kinds of things had gone wrong...Ubuntu wouldn't recognize external drives...Nautilus wouldn't let me open stuff...images froze on the screen...

In the end, I did a fresh install from the CD, updated, and ran sbackup restore.  I had to re-do some settings and ask a few email correspondents to send their messages again, but otherwise all is well.  Not sure what happened, but I'm going to back up more often now.  Thanks so much for all your help.

---

### Post by inverseroom on 2008-11-06
BTW Kamilion, I'd already reinstalled when you posted that, but I think that might have been the problem.  The failed package installations I did right before this happened involved video drivers.  Live and learn.

---

### Post by Kamilion on 2008-11-10
Ooh, thanks. I didn't know about sbackup. I'll have to start using that myself, normally I just tar up my homedir and use synaptic to save my installed package list, reinstall, load the package list into synaptic, and untar my homedir.

Relatively simple, and a lot easier than windows... (Ever try to move a homedir from C:\Documents and Settings\<user>\ to another computer? NT tried to be smart and store the user's registry in their homedir, but any other copy of windows can't load it because the system Security ID (SID) is different. Argh?)

Well, fair trade, I tried to pass on some knowledge and ended up learning something myself. Don't you love the linux community? :guitar:

---

