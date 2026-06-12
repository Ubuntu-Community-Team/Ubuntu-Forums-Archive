---
title: "Broken nipple/nubbin mouse on laptop"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by jexxie on 2007-08-10
Hi all,

I've recently setup Ubuntu Fiesty on my Dell Latitude D400, which is a notebook which has both a synaptic touch and a nipple mouse, nubbin mouse, or PointingStick (whatever you call it, there's no 'standard name' to my knowledge.)

The downside is that I've broken the nipple mouse on the notebook.  It will randomly send input when I'm not touching it in extreme ways, so it sends the pointer shooting in the top right or bottom left corners of the screen.  Now, rather than scapping the laptop, or eating a $120 repair bill for a new laptop keyboard, I'd rather just disable this in the OS itself.  As I'm dual-booting Windows XP and Ubuntu, downloading the Glidepoint drivers from Dell allowed me to disable the nipple input in Windows.  Now for Ubuntu...  I've Googled around a bit, couldn't find anything pertinent, so I thought I'd peek under the hood myself.

There's a pretty easy way to fix this.  Let's get started.

A legend of what the stuff below means:
# means that you can select the text after the # and it will run.
Anything else is notes or instructions from me, please read them and follow them explicitly.

Here's the terminal commands to get this setup:
Start up your terminal!  Applications -> Accessories -> Terminal
# sudo su -
Type in your user password
# nano -w /etc/X11/xorg.conf
Press Ctrl-W   (telling the text editor to search)
Search with this string:
Configured Mouse
Search again, (Ctrl-W) ignoring the first line it found.
The line highlighted will look like this:
        InputDevice    "Configured Mouse"
Please put a # at the beginning of the line, so it looks like this:
#        InputDevice    "Configured Mouse"
Press Ctrl-O to save, press enter to confirm.

Next, we need to restart the computer for our changes to take effect.

Voila!  Annoying broken input device disabled.

Any comments or critiques on how I can make this more clear for everyone is greatly appreciated.

---

### Post by feighery on 2007-10-16
Cheers for this. I too have a dell laptop with the broken nipple and work won't replace it for me. I am not using ubuntu but this worked non the less. As for the guide, I don't think it could be any simpler.

Cheers

---

### Post by isellapples on 2007-11-25
hey, cheers for the guide - i followed it and it disabled the nipple fine. but then for no reason, the nipple turned itself back on and wont go away :( any other ideas? i would still like to use the touch pad, so dont really want to disable it in the bios

---

### Post by jexxie on 2008-02-08
isellapples, what version of Ubuntu are you running?

---

### Post by delrawlings on 2008-04-01
This issue was really beginning to bug me. I setup Xubuntu on my Dell C610 and played around with xorg.conf to no avail. I tried the hashing out of the configured mouse amongst other things and had no joy I'm afraid.

At the end of the day, I got so hacked off with not being able to disable it through Xubuntu, I removed the keyboard and disconnected the 4 core ribbon cable running from the nipple to the motherboard connector.

While not being a good ubuntufied answer, it certainly solved the problem permanently, and left the keyboard and touchpad working perfectly.

---

### Post by jexxie on 2008-04-01
That's definitely a good option -- I couldn't figure out how to pry my D400 apart to do this.

---

### Post by prshah on 2008-04-01
> **isellapples said:**
> the nipple turned itself back on and wont go away :( any other ideas? i 

If you know the driver for the "nipple", you can blacklist it by adding it to the /etc/modprobe.d/blacklist.

If you don't know the driver, posting the output of ```
lspci 
``` and ```
lsmod
``` will help.

You will also have an option to disable it in the Notebook BIOS.

---

