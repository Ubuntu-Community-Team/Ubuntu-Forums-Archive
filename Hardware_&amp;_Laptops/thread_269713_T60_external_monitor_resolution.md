---
title: "T60 external monitor resolution"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by phileas on 2006-10-02
Hi dear fellows,

I have the following problem:

IBM T60 with intel embedded graphics max res 1024x768
External DELL monitor max res 12..x1024

I wish to use a docking station and work on the external screen. However, if I do so, the max resolution on the external monitor is limited by the max resolution on the LCD screen of the laptop. 

How can I go about changing this ?

Txs mates,

phileas

---

### Post by phileas on 2006-10-02
Please, help me on this, I am hopeless.
Anyone? 
phileas

---

### Post by phileas on 2006-10-04
I am amazed, nobody had this resolution issue? I looked everywhere, and I am unable to fix it. I also can't switch the display to an external screen correctly, since when I close the lid of the laptop, the external screen also goes black. 
Pleaaase, help,
phil

---

### Post by nosmada on 2006-11-15
I am currently on the same issue, I haven't fixed the resolution issue yet but about the screen going blank, all you need to do is change the power management preferences:

System > Preferences > Power Management

Select the *Running on AC* tab and at the bottom it should have a section called *Actions* and an option that says "When laptop lid is closed:" and have these options on a drop down: [Do nothing] [Blank screen] [Suspend] [Hibernate]. Of course to have the screen not go blank set it to [Do nothing].

You can do this for *Running on Battery* also but I don't recommend it. There are although some options for when your battery is almost fully drained to turn off.

---

### Post by amohanty on 2007-03-14
You need to do two things:
1. In the BIOS set the display option to analog - not vga+lcd (search around for it)
2. Keep the lid open till you are logged into gnome, then close the lid, you should be fine.

Regarding resolution:
do a - 
sudo dpkg-reconfigure xserver-xorg
When you get to the resolution part select only two resolutions - the one for the LCD and one for the laptop monitor.

Then when you boot up with the docking station, the screen shoudl automatically pick up the higher res.

HTH
AM

---

