---
title: "Compaq v2405 - need install help"
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by neomatrix on 2005-12-31
Hi,
I just bought a v2405US and I want to try linux for the first time. I saw at Distrowatch that Ubuntu is on top. I followed the install instructions for v2405 at [http://worldclock.blogspot.com/2005/11/not-witherspoon-but-silverstone.html](http://worldclock.blogspot.com/2005/11/not-witherspoon-but-silverstone.html). Everything was ok until startx when I receive a fatal error "screens not found". Other postings here discuss the same issue which is probably caused by incorrect setting for the monitor in xorg.conf

If somebody has the same machine runing ubuntu, please could you tell me what you have in your xorg.conf?

---

### Post by Sef on 2006-01-06
Did you try this as well:

> punkr0x 

I'm currently working on getting a Presario V2000 (with an AMD Sempron) set up with ubuntu, I've found I have to put the line
Option "noaccel"
in my xorg.conf for the video card, and also have to boot the livecd with the "noapictimer" command in order to get the clock running at the proper speed.

[http://ubuntuforums.org/showthread.php?t=85143&highlight=v2405]("http://ubuntuforums.org/showthread.php?t=85143&highlight=v2405")

---

### Post by garretthylltun on 2006-03-04
Boot up your computer.
Select "Recovery Mode"

Type the following:

```
sudo apt-get install xorg-driver-fglrx xorg-driver-fglrx-dev fglrx-control
```

Say yes to downloading and installing

When it is complete, type the following:

```
cp /etc/X11/xorg.conf xorg.conf.backup
```

That copies the file you are about to edit to a backup just in case.

Then type:

```
pico /etc/X11/xorg.conf
```

You will now be in an editor with the file needed.  Arrow down or PgDn until you see a section of text that looks like this:

```
Section "Device"
        Identifier        "ATI Technologies, Inc. Radeon Xpress 200M (RS480)
        Driver            "ati"
        BusID             "PCI:1:5:0"
```

The line you want to edit is the "Driver" line.  Change the "ati" to "fglrx".  

```
Section "Device"
        Identifier        "ATI Technologies, Inc. Radeon Xpress 200M (RS480)
        Driver            "fglrx"
        BusID             "PCI:1:5:0"
```

Then press the CTRL and X keys to exit.  It will ask you if you want to save, press Y for yes, and then it will want the file name, but it's already set, just hit the enter key.

Now CTRL+ALT+DEL, or if that doesn't kick, then type "exit" at the prompt an d hit enter.  This should reboot you, if not, power down and restart your computer.

Now, when it boots up this time, just let it all start up as it should.  The GDM window should be there again, just type your user and pass, and Gnome should kick right in for you.

If it doesn't, then sorry, I have no other ideas.  The above is what worked for me on my V2405US

Good luck,
-Garrett

---

