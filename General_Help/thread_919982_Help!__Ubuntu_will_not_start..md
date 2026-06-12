---
title: "Help!  Ubuntu will not start."
date: 2008-09-14
forum: General Help
---

### Post by sean.bailey00 on 2008-09-14
I am in a bit of a dilemma.  I had been trying to configure VirtualBox to work with a USB device, and found a forum that suggested I add a line of text to the file /etc/fstab.  The problem is, I believe that I put it in the incorrect place (I added it at the end).  Now whenever I try to boot up, Ubuntu will load, but stalls out at the step "Setting System Clock."  I tried to use sudo nano /etc/fstab , and can open it and edit it, but I cannot save.  Any suggestions on how I can either get it to save, or a different way to make Ubuntu boot? (Recovery mode does not work either).

---

### Post by dai_vernon on 2008-09-14
Booting from a Live CD would allow you to edit the file and save, as you can gain root access to your stuff from a live CD.  Would this solve your problem?  Maybe.  This isn't my forte, but give it a try - this is what I would do.

---

### Post by Pro-reason on 2008-09-14
We're not likely to be able to help if you don't even tell us what you did to the file.

---

### Post by sean.bailey00 on 2008-09-14
OK, I am using live CD, so I ran this in terminal:

gsku gedit /etc/fstab

And got this:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

Which is nothing like what it looks like.  I think Live CD uses some kind of temporary file, since it does not have to deal with different partitions.

---

### Post by sean.bailey00 on 2008-09-14
I added this line:

/proc/bus/usb usbfs devgid= enter vboxusers number HERE,devmode=664 0 0

to the end of the file.

Sorry, I do not remember what the vbox user number was.

---

### Post by sean.bailey00 on 2008-09-14
And before I changed /etc/fstab, I edited this file: /etc/init.d/mountdevsubfs.sh, but do not think that is causing my problems. ( dledted the # above the line "# Magic to make /proc/bus/usb work")

---

### Post by cariboo on 2008-09-14
Unfortunately all you edited were the livecd configuration files, your edits will be all gone the next time you boot. To edit your installation configuration files you will have to mount your hard drive and then edit the configuration files.

In a terminal typp:

```
sudo mount /dev/sda1 /mnt
```

where /dev/sda1 is the partition Ubuntu is installed to. Then to edit your fstab file you would hit Alt-F2 then enter:

```
gksu gedit /mnt/etc/fstab
```

Undo the edit you made, save and close the text editor, then reboot.

Jim

---

### Post by sean.bailey00 on 2008-09-14
OK, I'll try it.

---

### Post by Pro-reason on 2008-09-14
> **cariboo907 said:**
> 
where /dev/sda1 is the partition Ubuntu is installed to.

If he's a newbie, he might not know.

Let's do this a bit more graphically.

Boot from the Live CD.

Go to Places &#8594; Computer.

You will see all your partitions.  Find the one which is your main "root" partition, with Ubuntu installed.  Clicking on the icons will mount the partition.

Click on the little button that looks like a page of writing with a pencil.  That will display the path for the drive.  In my case, it is "/media/Ubuntu".

Your Ubuntu partition is now mounted, and you know where it is mounted.  You just have to put that path in front of any path on your system.

For example, I would hit Ctrl-F2 and type:
```

gksu gedit **/media/Ubuntu**/etc/fstab
```

Once you have opened your /etc/fstab in gedit, go to the end, and disable that line you added.  To do so, put a hash sign (#) at the beginning of the line.

Save and exit.

Reboot without the CD.

---

### Post by sean.bailey00 on 2008-09-14
It saved.  Rebooting...

---

### Post by Pro-reason on 2008-09-14
> **sean.bailey00 said:**
>   I tried to use sudo nano /etc/fstab , and can open it and edit it, but I cannot save.  Any suggestions on how I can either get it to save, or a different way to make Ubuntu boot? (Recovery mode does not work either).

Sorry, I skimmed over this bit the first time.

The fact that you were able to do &#8220;sudo nano /etc/fstab&#8221; shows that you did indeed manage to start Ubuntu, and log in.  It's just that the graphical environment didn't start.

To save in nano, simply press Ctrl-X to exit (as noted at the bottom of the screen).  It will ask you whether you want to save or not.  Hit Y.  Hit Enter to confirm.

Then do &#8220;sudo reboot&#8221;.

---

### Post by sean.bailey00 on 2008-09-14
OK.  I followed your instructions (the first ones, from the Live CD) and the line is no longer there.  I rebooted, but the same thing happened - it snagged at "Setting System Clock."  I had already done what you just suggested in nano, but it would not save - it said the file was read-only.  I tried to write-over the file as well, but, like before, it said it was read-only.  I did not check to see see if that line is still in the file from nano, but I do not think it would be.

---

### Post by sean.bailey00 on 2008-09-14
And perhaps I misunderstood you, but I did not login (as in enter a username and password) - it never got that far.  Ubuntu did start, but am I technically "logged in"?  That would effect my permissions, no?

---

### Post by Pro-reason on 2008-09-14
> **sean.bailey00 said:**
> And perhaps I misunderstood you, but I did not login (as in enter a username and password) - it never got that far.  Ubuntu did start, but am I technically "logged in"?  That would effect my permissions, no?

If you got to a command line, then you must have been logged in.  Whether you type a password or the system logs you in automatically, you are &#8220;in&#8221;.

Once you are on a command line, you can do commands such as &#8220;whoami&#8221; to see how you are logged in.  If you can use sudo to do anything at all (&#8220;sudo nano&#8221;, &#8220;sudo ls&#8221;...), then the problem is not one of permissions as such.  The partition itself may be mounted read-only.  In that case, you can do no administration whatsoever.  Remounting it read-write would be very tricky, and at that stage I personally would give up and use a live CD, as you did.

---

### Post by Pro-reason on 2008-09-14
> **sean.bailey00 said:**
> OK.  I followed your instructions (the first ones, from the Live CD) and the line is no longer there.

I'm very surprised to hear that the line has disappeared.  It makes me think that you were somehow looking at the wrong file.  But maybe the file has indeed been reset by the system somehow.

> **sean.bailey00 said:**
> And before I changed /etc/fstab, I edited this file: /etc/init.d/mountdevsubfs.sh, but do not think that is causing my problems. ( dledted the # above the line "# Magic to make /proc/bus/usb work")

I'm now interested in what you did here.

Here is the relevant part of the file from my system:

```
        #
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb
```

Did you simply remove the # on the first line there?  Since there is nothing after that symbol, removing it would have no effect at all.

---

### Post by sean.bailey00 on 2008-09-14
OK.  Would my best option from this point, then?  Do I have to re-install from scratch, or can I pull settings, files, packages, etc. from the defective instance?

---

### Post by sean.bailey00 on 2008-09-14
OK, the line did not just dissappear; I removed it, and rebooted, and the startup failed, so I rebooted again on the Live CD and looked at the file, and the line was not there.

And yes, all I did was remove that #, and I even went back and replaced it.

---

### Post by Pro-reason on 2008-09-14
Are you able to select a failsafe option from the GRUB menu?

---

### Post by sean.bailey00 on 2008-09-14
All I have is the normal partition and recovery mode.

---

### Post by sean.bailey00 on 2008-09-14
Thanks for your time; I do not know what timezone you are on, but it is almost midnight here, and I have to be at school in five hours.  I'll check back tomorrow.

---

