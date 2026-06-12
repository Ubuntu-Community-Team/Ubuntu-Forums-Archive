---
title: "Help with Card reader, Power management and TOuch pad"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by eBast on 2007-04-01
I have been using Ubuntu 6.10 on my Compaq Presario M2000 series laptop for over 3 months now.  I am extremely happy with the system except for some minor quirks.  I will list them, and hopefully will get help here...

1. My machine has a inbuilt card reader, which does not work. So I am now connecting my digital camera via the usb cable, which works flawlessly, but still I would like to use the card reader.  Partially corrected, thanks to teaker1s, would like a permanent solution

2. The power management is not working correctly, I think, because at around 70 % battery power remaining, the machine hibrinates on me without any warning. This happened twice, when I was on a lecture,so I would like to correct this.  This strangely happens only when open office impress is on in full screen mode, other wise the pc will go till about 10 % and then only hibrinate. I have checked the power management applet, but couldnt find any settings for setting the percentage power remaing to hibrinate.

More over the remaining time calculation also seems to be incorrect. Now as I am typing the battery is down to 22 % but remaining time calculated is 12 hours 16 mts which is unlikely. 

3. I have a synaptics touch pad, the sensitivity of which seems to be low.  i.e. it is not recognizing the double taps correctly, so I am forced to use the left and right tap buttons. Is there any way to calibrate the touch pad ?  Already corrected ... tweaker1s helped me out ..thankyou

HOpe I am clear with my problems, and I would like tell u at this point that I am only comfortable with GUI, I can use the text mode only when I am given detailed instructions as in Ubuntuguide.org.

Expecting replies...
Thank you

---

### Post by teaker1s on 2007-04-01
touchpad there is **gsynaptics** for gnome and** ksynaptics** for kde I believe

---

### Post by eBast on 2007-04-01
> **teaker1s said:**
> touchpad there is **gsynaptics** for gnome and** ksynaptics** for kde I believe

Thank you for your quick reply, installed gsynaptics after a search in the forum, edited xorg file and now I have complete control over the touch pad


THankyou

Now thats one problem less from my list.  Hope I get help for the other two too....:)

---

### Post by teaker1s on 2007-04-02
okay a suggestion for your card reader, it's part of a wiki page I started and people added to, I haven't got a card reader-but this may help.

[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29%7C%28hp%29#head-0b198b90ec3b7cc470b197a54622354457513e6c]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29%7C%28hp%29#head-0b198b90ec3b7cc470b197a54622354457513e6c")

---

### Post by eBast on 2007-04-02
> **teaker1s said:**
> okay a suggestion for your card reader, it's part of a wiki page I started and people added to, I haven't got a card reader-but this may help.

[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29%7C%28hp%29#head-0b198b90ec3b7cc470b197a54622354457513e6c]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29%7C%28hp%29#head-0b198b90ec3b7cc470b197a54622354457513e6c")

Thank you once again :) .  I got my card reader working albeit temporarily as suggested in the wiki.  Fortunately I saved the command as a txt file, so i can issue the command when ever i want to use the card reader.

Any suggestions to make this a permanent remedy ?

Thank you

---

### Post by teaker1s on 2007-04-02
make a script, with the command in it (basically make the txt file executable) now is when the script is clicked you can load the media card reader. you could use update rc.d to give runlevels and automate it
[http://www.debian-administration.org/articles/28]("http://www.debian-administration.org/articles/28")

---

### Post by eBast on 2007-04-02
> **teaker1s said:**
> make a script, with the command in it (basically make the txt file executable) now is when the script is clicked you can load the media card reader. you could use update rc.d to give runlevels and automate it
[http://www.debian-administration.org/articles/28]("http://www.debian-administration.org/articles/28")

As I said before, I am not comfortable with text interface let alone make a text file executable.

This is the command that I use to get my card reader working .......  sudo setpci -s 06:09.3  4c.b=0x02.


Can you tell me how to make a script of this ?  :confused: 

Thank you..

---

### Post by teaker1s on 2007-04-02
rename script so the extention is **.sh **eg.
eg.    [COLOR="Red"]myscript.sh[/COLOR]  now right cilck on the file and select properties, you can now decide who can execute/read/write etc.

also right click and properties "opens with" select
[COLOR="Red"]x-terminal as root[/COLOR]
that way you dont need to do more than a double click

I'm not any expert in scripts, but I've tested it with synaptic and it works

---

