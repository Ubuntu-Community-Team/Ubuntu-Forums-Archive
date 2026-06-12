---
title: "Can i re-install ubuntu without losing my things?"
date: 2008-08-06
forum: General Help
---

### Post by collinge on 2008-08-06
The computer was working fine, then we shut it down. In the morning it would not load up after the log in screen. We have tried all we can think of and all the advice we have been given but nothing has worked. Can we re-install Ubuntu without losing all of our pictures and music and documents? If we re-install will it fix the problems?

---

### Post by mikjp on 2008-08-06
Yes, if you have put /home on a separate partition. No, if you did not.

But you could use a live CD to copy your files from the hard disk to an external hard disk or USB memory before doing a reinstall.

You might, however, fix the system. Reinstalling is not necessary. If you have got to the login screen, the system is in fact loaded. Does it not accept your password?

You could try to press Alt+Ctrl+F1 and go to text mode to copy your files. You might boot into single user mode, as well. There are many possibilities you probably have not tried yet.

Greetings,

mikko

---

### Post by overdrank on 2008-08-06
> **collinge said:**
> The computer was working fine, then we shut it down. In the morning it would not load up after the log in screen. We have tried all we can think of and all the advice we have been given but nothing has worked. Can we re-install Ubuntu without losing all of our pictures and music and documents? If we re-install will it fix the problems?

Hi and if you have a separate home partition then you can. If you have the live cd you can use it to create a partition and move all your data to before the reinstall.

---

### Post by collinge on 2008-08-06
[http://ubuntuforums.org/showthread.php?t=881134](http://ubuntuforums.org/showthread.php?t=881134)
this was my origional post, but it was getting me nowhere... I have tried all the advice, nothing has worked.
also, when i do Ctrl+ALt+F1 the text is huge, and I cannot scroll to the bottom. How do I boot into single user mode?

---

### Post by vlovich on 2008-08-06
I had a similar problem caused by my fingerprint scanner.  If you have one, keep reading, otherwise skip to the post below.  The one thing I would recommend you do, before doing anything, is swipe your finger a bunch of times (say like 5).  If that works, then you know you have to do that every time you get a password prompt (i.e. login, sudo, synaptic, etc).  To disable it, modify the /etc/pam.d/common-auth file (although I would recommend you post that file to this forum to get some feedback on the precise modifications that need to be made).

---

### Post by vlovich on 2008-08-06
I'm not sure of the particulars of you're case, but if you have your home partition on a separate physical partition, you should be OK re-installing Ubuntu without losing your personal settings (do not format your home partition).  There is no guarantee that this will fix your problem.  However, if it is the system settings that somehow got messed up, then yes this will fix it (since installation generally wipes the root partition).  If it's your own personal settings, this won't, since those exist in your home directory.

That being said, it is possible you may lose some program settings (i.e. any changes you made in /etc) and you will lose anything in your root partition (the place where programs are installed).

Personally, I have a similar problem.  My partition corrupted, and I ran fsck, causing my system to become generally foobarred.  Networking doesn't work (my wifi & LAN) so I can't re-install packages.  Important gnome libraries are missing or corrupt.  My point is that I'm hesitating about re-installing Ubuntu, because I'm not too keen on restoring my system settings.

I would still recommend a back-up of data that you truly can't lose.  There are several ways you can probably do this:

Proposal 1:  Use a live-cd (requires a CD with Ubuntu on it)

Boot into the live-cd (just as you would have done during installation).
Use the GUI to back-up your files somewhere (i.e. USB key).
Then continue with re-installing on your root partition.

Proposal 2:  Use a virtual terminal (requires command-line)

Before logging in, hit Ctrl+Alt+F1.  This should bring you to a virtual terminal (F2, F3, F4 etc.  F7 is typically your GUI).

Login with your credentials.

If you are successfully able to login, then plug in a USB key and transfer your files to it (the USB key should appear in /media/<NAME OF USB KEY>).  cp -ri <file or directory to copy> <destination>.  The -r flag indicates recursive (for directories), and the -i flag indicates it will ask you when it's about to overwrite something.

If you have a back-up big enough (i.e. iPod), you can even do
cp -ri $HOME /media/<NAME OF IPOD>.  You can check running the following command:

```

if [ $(du -s $HOME | awk '{print $1}') -gt $(df | grep /media/<NAME OF IPOD> | awk '${print $4}') ]; then echo "Enough space"; else echo "Backup medium too small"; fi

```

Proposal 3:  SSH in (requires command line)

If the virtual terminal doesn't work (and it may not if you have an onboard nVidia card using the stock proprietary drivers), and you have SSH set up (I can never remember, but I believe Ubuntu generally installs with SSH on), you should be able to get command line acces to your machine through ssh.

ssh <username>@<ip address>.

Then follow the steps to back-up your data as above.

Proposal 4:  Hook-up your laptop drive to another computer (requires an external USB-enclosure).

Remove the hard drive from the laptop.

Place it in the USB-enclosure.

Connect the enclosure to another computer.

Copy the necessary files to the other computer.

NOTE:  If the other computer is a Windows computer, you will need something that can access Linux partitions.  [http://www.fs-driver.org/](http://www.fs-driver.org/) for the driver.  [http://www.go2linux.org/accessing-linux-drive-ext-with-vista](http://www.go2linux.org/accessing-linux-drive-ext-with-vista) for the installation guide (although I didn't need a reboot, so YMMV)

Good luck.

---

### Post by vlovich on 2008-08-06
> **collinge said:**
> [http://ubuntuforums.org/showthread.php?t=881134](http://ubuntuforums.org/showthread.php?t=881134)
this was my origional post, but it was getting me nowhere... I have tried all the advice, nothing has worked.
also, when i do Ctrl+ALt+F1 the text is huge, and I cannot scroll to the bottom. How do I boot into single user mode?

The text is huge because virtual terminals are generally something like 80x25 characters, which means there are a lot of pixels per character (screens are typically at least 1280x800 pixels).  There is no scroll support (as far as I know) in a virtual terminal.  You are always at the end in a virtual terminal - you couldn't scroll down anyway.

If you see a lot of text already when you hit Ctrl+Alt+F1, it's probably just useless (at least in your case) boot-info.  Try entering your login info anyways.  If you are really uncomfortable, hit Ctrl+Alt+F2 and that should bring you to a fresh virtual terminal.

Not sure what you mean by single user mode.  If you're referring to the admin recovery boot-option, it's highly unlikely that's what you want.

---

### Post by collinge on 2008-08-06
okay, I added a new administrative user and that fixed the problem,,,, THANK YOU EVERYONE FOR YOUR ADVICE. it was much appreciated

---

### Post by vlovich on 2008-08-06
Oh, and if you need to figure out whether or not your home directory is in a separate directory, do the following:

```

df $HOME
df /

```

The first column must contain different values (i.e. sda2 and sda3).

---

### Post by collinge on 2008-08-06
how do i set the newly created user to 'owner' . I cannot move files from one user to the other.

---

### Post by mikjp on 2008-08-06
With chown on the command line. Try ```
man chown
``` for more information.

Greetings,

m

---

