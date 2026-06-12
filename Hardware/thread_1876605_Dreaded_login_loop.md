---
title: "Dreaded login loop"
date: 2011-11-06
forum: Hardware
---

### Post by Strugglintoworkit on 2011-11-06
Hi,

Please can you help me solve this login loop issue I have?

I running Xubuntu Lucid on an old Toshiba satellite.  

I've been using this install for a few weeks and have performed several updates and installed various programs.

A few days ago I went to log in, entered my password and it looked as if I was going to get to the desktop but then reverted back to the login screen.  I powered it down for a few hours and next time it was fine.

Yesterday I went to use it and it's now permanently loopin back to the login screen.  I've read up quite a bit and this seems a common issue and I've tried various suggestions relating to .ICEauthority but nothing seems to work for me.

I'm new to all things Linux and on a steep learning curve, please help.

Thanks

---

### Post by LinuxFan999 on 2011-11-06
I had this exact same problem with Xubuntu lucid on an old Compaq laptop. My solution (maybe the only real solution) was to reinstall Xubuntu, and during installation, enable auto-login.

---

### Post by Toz on 2011-11-06
Have a look at the log file ~/.xsession-errors. There may be some clues there as to what is going on in there.

---

### Post by brotherz on 2011-11-06
> **Toz said:**
> Have a look at the log file ~/.xsession-errors. There may be some clues there as to what is going on in there.

To amplify on the above response, you need to do several steps to get to this file. From your log-in screen, hit the key combination Ctrl-Alt-F2, which will put you in a terminal. Enter your usual name and password. Now you will have the opportunity to create a root password, which is going to help you shortly.  To create the root password type 'sudo passwd root'. You will be prompted for your usual password. Give it, and then you will be asked to create a password for root.  Enter that new password.  When you are finished, return to your log-in screen by the key combination Ctrl-Alt-F8.
Now, select a different log-in user, which is root, and use the new password you just made for root.  This should get you into your system.  From here on be careful because you are running as root. Open a terminal. Enter cd /home/[your user name].  This puts you in your own home directory.  Look there and see if you can find the .xsession-errors file mentioned above.  You will have to 'cat' the file.
What to do at this point depends on what you find.
This procedure helped me recently when I had messed up one of my files and couldn't log in as regular user.    (As root user, I was able to edit the messed-up file then type 'shutdown -h now' in the terminal and close everything down.  Upon reboot, the regular log-in worked.)  
Good luck.

---

### Post by Toz on 2011-11-06
There is no need to enable the root account to view the contents of a user log file. Ctrl+Alt+F1 and log in using your normal user account id and password. Any changes requiring user privileges can be made using sudo (see: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo"))

---

### Post by Jose Catre-Vandis on 2011-11-06
Check your / or ~/ is not too full ?

---

### Post by Aerilus on 2012-01-22
thank you, looking at the logfile in my home directory .xsession-errors.old (its a hidden file) revealed that there was a permission error (i absolutely hate permissions more in linux than i could have ever imagined in windows) with /home/"username"/.iceauthority so i gave my user access to that file and then i was let back in now I have to figure out where my panels went to. 

a few notes I was not able to press ctrl+alt+f1-f6 to get to the console mode because my monitor would then say that it did not support the resolution or refresh rate of console mode. I instead was able to gain access to the system by clicking on my user name looking at the bottom of the page at session and changing the session to xterm. then I was able to launch thunar and mouse pad to avoid doing everything by the console.  my system if encrypted as well so some forms of access were also unavailable to me

---

### Post by Chasehead on 2012-03-20
I was having the same problem but I just fixed it. I was able to use GNOME and Lubuntu on 10.04but could not get into Xubuntu with the login loop issue. However I was able to use Xubuntu when I first installed it but not very so long later I could not load it. 

What I did was go into Synaptic Package Manager and looked up 'xubuntu'. I scrolled down to the package called 'xubuntu-default-settings' and checked 'Mark for Reinstallation'. Then I reboot my computer, selected 'Xubuntu Session' at the GDM login screen, and I was back in business! Let me know if this works for you. I don't remember how to do this on the command line unfortunately...

---

### Post by ccrs8 on 2012-03-21
This happens to me as well every once in a while, but once it starts happening it happens for a week before mysteriously stopping for a month or so.  I never get unending loops - at most I have to log in 3 times before it "takes."  I also had this happen a few times over a two week period when using classic Gnome Ubuntu 11.04, but it happens a lot more with Xubuntu 11.10.  Very strange.  I'll have to take Chasehead's suggestion next time it happens.

---

