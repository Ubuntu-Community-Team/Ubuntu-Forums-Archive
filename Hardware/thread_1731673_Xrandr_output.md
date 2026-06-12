---
title: "Xrandr output"
date: 2011-04-17
forum: Hardware
---

### Post by qkzoo on 2011-04-17
I'm trying to set the screen resolution on my desktop, a Dell Dimension 2400 with a Dell CRT monitor.  I went into terminal and typed in "Xrandr" to see what the output was:

> 
andrew@andrew-Dimension-2400:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
andrew@andrew-Dimension-2400:~$ 


Under display preferences, the monitor is not detected.  This whole thing started because I wanted to be able to use an Xrandr command to change screen resolution, using Newrez for instance.

Now I get a "Failed to get size of gamma for output default" - I don't know what that means...

---

### Post by qkzoo on 2011-04-18
When I do an Lspci in terminal, the system lists my graphics controller as an Intel graphics card, so I'm assuming the video card drivers have been loaded properly.  However, desktop effects can not be enabled, and it still isn't detecting my monitor, and I can't change the resolution to anything other than the default.  I tried creating a xorg.conf file, but I must have screwed something up, because it wouldn't boot properly after the changes.  I will do a clean install with any suggestions when somebody pipes up with help, until then, I stuck XP back on this machine to make it useable.

---

### Post by qkzoo on 2011-04-19
I could really use some help here.  I've searched Google, I've searched these forums, all information I find seems to be really old and out of date, or irrelevent.  I guess to help narrow down this problem, I could ask a simpler question: 

Is this a driver issue or a monitor issue?  Ubuntu, no matter what I tried did not detect my monitor. 

Where do I go from here?

Edit: I'm trying to install 10.10 but I also have a copy of 10.04 and 11.04.

---

### Post by georgemc on 2011-04-19
I do not have your exact setup, however, I did had to overcome the "Can't detect the monitor" thing.  I knew that my monitor was able to display at 1280X1024 however the system never gave me that choice.

Programs that can help:

cvt
xrandr

Also might have to edit /etc/X11/xorg.conf

First I would suggest to look at the MAN pages of cvt and xrandr.  Yes xrandr is a beast.

Now get the "modline" for your setting with cvt.

```

cvt 1280 1024

```The output should look some thing like this:

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

Now we have to tell the system via xrandr this new configuration, so we will use 3 xrandr commands.  We will make a "newmode", then use "addmode" to add the mode to our display device, and them finally set the mode.

Use the contense of the cvt Modline.

```

xrandr -newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```My video device is VGA-1, yours might be some thing else.

```

xrandr --addmode VGA-1 1280x1024_60.00

```Now set the mode.

```

xrandr -s 1280x1024

```If this all works then you should have the new resolution.  I also had to set the new resolution after each reboot.

The error codes are cryptic and a pain, and I do recall I did a lot of rebooting and hitting Fn-F2 and restarting the gdm service till I had it all worked out.

Doing a search for cvt and xrandr on this site produces thousands of posts, kinda hard to sift through.

Hope this can point you in the right direction.

George

---

### Post by qkzoo on 2011-04-20
First off, thank you for the response.  I've been digging through this site and the web for almost three days trying to get this thing to work, unfortunately, not having much luck!

Ok, I have tried what you suggested, but it still fails.  I type the CVT command, and get this:

```

andrew@andrew-Dimension-2400:~$ cvt -v 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```Next, I type the xrandr command and get this:

```

andrew@andrew-Dimension-2400:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19

```> Failed to get size of gamma for output default Does this mean that the monitor is not being detected still?  Any other ideas?

---

### Post by qkzoo on 2011-04-24
Anybody?

---

### Post by qkzoo on 2011-04-27
Help, please!

---

