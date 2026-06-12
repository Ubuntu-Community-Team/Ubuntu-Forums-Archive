---
title: "Compiz Fusion Won't Work."
date: 2008-10-14
forum: General Help
---

### Post by nerd0795 on 2008-10-14
After trying sooo many times, posting on this forum for answers I've decided I will try once more.  

Graphic card: ATi Radeon Xpress 1250 (integrated graphics)

So I went searching on google and found a terminal command and I posted it
here is the results (the command is on the top row.)

```
alex@alex-desktop:~$ compiz --replace ccp
Checking for Xgl: not present. 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:05.0 0300: 1002:7941 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

When I try to enable desktop effects the screen kinda goes crazy (like when you change resolution) and it just saying "Not able to activate Desktop Effects".

I do have the drivers installed.  Also it used to work before and then it just stopped working.

Someone please help!

---

### Post by parajuito on 2008-10-14
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
try this guide

---

### Post by nerd0795 on 2008-10-14
> **parajuito said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
try this guide

:/  Nope didn't work.

---

### Post by parajuito on 2008-10-14
have you tried restoring your xorg file?
sudo dpkg-reconfigure xserver-xorg

or try reinstalling the drivers :S

---

### Post by nerd0795 on 2008-10-14
> have you tried restoring your xorg file?
sudo dpkg-reconfigure xserver-xorg

or try reinstalling the drivers :S

Yes.  i have.

---

### Post by loomsen on 2008-10-14
Which drivers do you use then? Or is this a quiz show?

Try compiz-check, or at least do:
```

cat /etc/X11/xorg.conf | grep Driver

```
and post its output.

If you're using radeonhd, get radeon instead and everything should work.

---

### Post by nerd0795 on 2008-10-15
> **loomsen said:**
> Which drivers do you use then? Or is this a quiz show?

Try compiz-check, or at least do:
```

cat /etc/X11/xorg.conf | grep Driver

```
and post its output.

If you're using radeonhd, get radeon instead and everything should work.

```
alex@alex-desktop:~$ cat /etc/X11/xorg.conf | grep Driver
	Driver      "kbd"
	Driver      "mouse"
	Option	    "VendorName" "ATI Proprietary Driver"
	Driver      "fglrx"
alex@alex-desktop:~$ 

```

---

### Post by loomsen on 2008-10-16
Don't know to much about ATI, but ba buddy was totally excited yesterday when fglrx for intrepid has been published. Maybe just try and install the latest driver for your card.

ATI lacks support in general tho.. Prepare for some seerioz googlin ^^

---

### Post by nerd0795 on 2008-10-16
I ended up creating a new user account for a guest.  and compiz worked on it.  But it still doesn't work on the admin (my account)

---

