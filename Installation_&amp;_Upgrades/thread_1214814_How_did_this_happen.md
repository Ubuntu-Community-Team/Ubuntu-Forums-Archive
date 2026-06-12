---
title: "How did this happen?"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by onexmadxdisaster on 2009-07-16
I am getting very frustrated with all this ubuntu stuff...
I bought the dell mini 9, and I didnt think I should have to pay extra for windows, so I figured I would try ubuntu. It isn't proving itself to me...
Despite not being able to use any of my regular programs, I was using this OS and coping.
I am not computer stupid.
I was browsing the internet when my update manager popped up, I was bored, so I let it do the update. When I grew tired of the internet,the update was STILL GOING. it had been a little while. So I plugged in my laptop and left it going. Well, turns out it fell asleep. Which means it disconnected from the internet. Which means the update didnt finish. And now my  built in wireless doesnt show up as an option, i can only connect to a wired network (Which sucks) and half of my programs wont launch, and once I open the programs, the title is in the middle of the top of the box, and there is no X button to close it, so I have to right click and close.
Any suggestions how to fix this stupid problem?

---

### Post by Ra-Hoor-Khuit on 2009-07-16
Connect via your wired connection and go to System/Administration/Update Manager and see if allowing the updates to finish will correct things.  You've probably got a lot of whargarbl going on because of the incomplete update.

To speed up the update process, you might want to first go to System/Administration/Software Sources (Ubuntu Software tab) and click on the dropdown menu at the bottom labeled "Download from:" and then on "Other" and then on "Select best server".  After a minute or so of testing this function will choose the fastest download server/location for you at that point in time.

If still no joy we can use the terminal to do this, but you sound like you might prefer to use the GUI method so that's why we're taking this particular route.  If you're comfortable with using the Terminal we can knock this out with a couple quick Cut and Paste operations.  Up to you.

---

### Post by irv on 2009-07-16
> **onexmadxdisaster said:**
> I am getting very frustrated with all this ubuntu stuff...
I bought the dell mini 9, and I didnt think I should have to pay extra for windows, so I figured I would try ubuntu. It isn't proving itself to me...
Despite not being able to use any of my regular programs, I was using this OS and coping.
I am not computer stupid.
I was browsing the internet when my update manager popped up, I was bored, so I let it do the update. When I grew tired of the internet,the update was STILL GOING. it had been a little while. So I plugged in my laptop and left it going. Well, turns out it fell asleep. Which means it disconnected from the internet. Which means the update didnt finish. And now my  built in wireless doesnt show up as an option, i can only connect to a wired network (Which sucks) and half of my programs wont launch, and once I open the programs, the title is in the middle of the top of the box, and there is no X button to close it, so I have to right click and close.
Any suggestions how to fix this stupid problem?

It sound like you are blaming Ubuntu for a problem you caused. If you would have done this in Windows you would have hosed up your windows install also.
To fix the problem you might try this: When you bootup and grub comes up hit the [Esc] key or just arrow down to Recovery mode. When the Recovery menu comes up try the Fix system option. It is like the repair in Windows. If it is so screwed up you might have to do a reinstall.
I have been using Ubuntu since 2005, and I have had less problems with it compared to Windows. I bought a new laptop with Vista, and it sucks, So I installed Ubuntu on it and never looked back.

---

### Post by onexmadxdisaster on 2009-07-16
Unfortunately Update Manager is one the multiple programs that wont load. Im not blaming ubuntu, I am just not necessarily happy with it. If it were windows I would probably be able to fix this problem myself. I had vista as well and did not like the updates. Thus why I wanted xp, but apparently that is a thing of the past in new computers. 
I just want to fix this so that I can use my wireless, I could care less if half of the programs on this laptop dont work, seeing as to how I only use it for internet and word processing, Not much you can do on such a small laptop...

---

### Post by onexmadxdisaster on 2009-07-16
This isnt the first problem I have had with ubuntu, such as little things I have chosen to ignore, like the fact that no matter how many times I change my settings the []("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7626091")clock display is always in 24 hour format. Im not saying I hate it, it would be great for people who want to learn a whole new system or need something simpler. Just not for me. 

I guess I havent done too much tech-y stuff as far as what you are referring to. I have never had to use terminal and wouldnt know where to begin. I do appreciate both of your help, I am just tired of feeling helpless with this system.

---

### Post by gamerchick02 on 2009-07-16
It sounds like you're going to have to do it in a terminal (you may want to print this stuff out so you can reference what I'm suggesting).

[LIST=1]
[*]Boot Ubuntu like you normally do.
[*]Then hit Cntrl-Alt-F2. This will drop you to a terminal.
[*]Login with your username and password.
[*]You should get a username@machinename prompt (your username and your machine name in the respective locations).
[*]Now, run 
```
sudo apt-get update
```
This will update your repositories.  You will have to type your password at the prompt. Do this and the command will run.
[*]Now run
```
sudo apt-get upgrade
```
This will update all of your packages and install all the new packages.
[*]Reboot.  You should be good to go.
[/LIST]

Good luck, and I hope I helped.

Amy

---

### Post by raymondh on 2009-07-16
These things happen.  Let's troubleshoot.

Try in terminal one at a time (applications > accessories > terminal > type or copy/paste *(you'll be prompted for a password which you won't see when you type it in)*)

```
sudo apt-get update
sudo apt-get upgrade
```  

Post back any errors

Of course, you have to be ethernet connected in the meantime.

Also, how many kernels are you running?  When you boot up, do you have various kernel-generic options (am not talking about kernel-recovery nor memtest)?

---

### Post by onexmadxdisaster on 2009-07-17
I'm just doing what I am told. This is what the mini laptop did....
[FONT=monospace]amelia@amelia:~$ sudo apt-get update
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
amelia@amelia:~$ [/FONT]

---

### Post by onexmadxdisaster on 2009-07-17
amelia@amelia:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
amelia@amelia:~$ 



Well then. I think it's trying to call me stupid and underpriveleged.... lol.

---

### Post by izizzle on 2009-07-17
Run ```
dpkg --configure -a
```

---

### Post by onexmadxdisaster on 2009-07-17
And I am not sure what the term kernel refers to. I haven't had this laptop for too long and I haven't ventured all of Ubuntu yet.

---

### Post by lisati on 2009-07-17
ok - making progress.
From the command line (instructions previously given), type in the following:
```
sudo dpkg --configure -a
```
All going well, this will help fix some of the problems. You should the be able to run update manager, or do the following from the terminal:
```
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by onexmadxdisaster on 2009-07-17
Okay, that seems to be working. But it sure is thinkin and workin hard on that one...
I gotta admit that I do like all the terms ubuntu uses. The names are so cute.
HEY! my update manager taskbar tray icon reappeared! PROGRESS! Still waiting to do the other two codes.

---

### Post by onexmadxdisaster on 2009-07-17
amelia@amelia:~$ sudo apt-get update
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_DK
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Translation-en_DK
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Reading package lists... Done
amelia@amelia:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
amelia@amelia:~$ 



Now time to cross fingers and reboot...

---

### Post by onexmadxdisaster on 2009-07-17
SUCCESS!
Using my wireless now, and all my programs run and function properly!
Thanks so much for the help. I have really gotta look into this stuff if I am going to be working on it...
Thanks again

---

### Post by raymondh on 2009-07-17
well done ... congratulations!!!!

May I recommed the [Ubuntu pocket guide]("http://www.ubuntupocketguide.com/index_main.html") which you can download (FREE) and peruse at your leisure.  Lots of good stuff :)

Happy Ubuntu-ing.

---

### Post by irv on 2009-07-18
> **raymondhenson said:**
> well done ... congratulations!!!!

May I recommed the [Ubuntu pocket guide]("http://www.ubuntupocketguide.com/index_main.html") which you can download (FREE) and peruse at your leisure.  Lots of good stuff :)

Happy Ubuntu-ing.

Thanks for the tip on the pocket guide. I even went out and downloaded it.

---

### Post by gamerchick02 on 2009-07-18
Good to hear.

Glad it's working for you now.

Amy

---

### Post by hetx on 2009-07-18
Kudos on sticking with it! But yeah, things like a messed up upgrade can mess up any OS. Atleast with Ubuntu the solution doesn't always have to be a complete re-install =P

---

