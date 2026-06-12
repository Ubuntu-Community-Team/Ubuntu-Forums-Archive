---
title: "Fujitsu c-500 Linux install  --solved"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by munchen800 on 2009-08-31
michael@michael-tab:~$apt-get RANT

OK so last year I bought one of those Fujitsu Stylistic LT C-500 tablets off ebay. It shipped to me with a 6gb HDD, no CD, 1 usb w/o BIOS option to boot to usb, 128mb RAM, a D-LINK PCMCIA WIFI card, and Win2k. Well it only took about a month for Win2k to crap out on me, SURPRISE SURPRISE a crappy Windows OS that stopped working. Well I had a 60gb laptop HDD laying around so I figured an upgrade was in order. :) However I was faced with a problem, how do you install a OS with nothing to boot to, no CD, no working OS on the HDD, no PXE(which is available with the docking station-but I didn't have one). 

My line of thinking at the time was Windows XP. Doing some research I found people got the Win2k drives to work in XP. EPIC FAIL!!! I pulled the HDD put it in my laptop installed WIN98 put it back in the Tablet, fixed all the errors, then did a in place upgrade to XP. No luck with the drivers though. So passed a week of my life I can never get back.

Next line of thought--"Well I can just use WIN98". FUNNY RIGHT!! Well the Tablet worked, kind of. It is funny the things we take for granted these days. Like bluetooth, functioning usb, and a 32bit GUI. Well Win98 doesn't have any of these things. No bluetooth support of any kind. D-link does not make a WIN98 driver for the card it shipped with so I had to fall back on a old usb WIFI NIC. HAHA It barely worked, all I could do was connect to the internet. Well that is fine except I store all my music and Videos on a Ubuntu based file server, ans I couldn't connect to it. So I needed something better. Another month of my life I will never get back.

Now the fun stuff--"LINUX". Many failures but in the end success, but not a wast of time because I learned a lot. Here is the short list of the Distro's I tried , Fedora 8, 9 and 10, Suse 10.1, .2, Backtrack 2, 3 HDD installs, Slax 5, 6 also HDD installs, Knoppix, DSL, and of course Ubuntu. Now I tried Ubuntu 8.04.1 first, of course, However there is a bug with the touch screen driver, AKA fpit, and when I went with intreped my setting were off the first time. So I went through the others listed above, but in the end(12 months later) Ubuntu 8.10 Works Great.

OK I am done, Now I will tell you how to get it working.

FIRST: USE UBUNTU 8.10 !!IMPORTANT!! Download burn to cd.

NEXT: Pull the HDD out of the tablet and put it in a laptop or use and adapter to put in a desktop. There is no way around this. Run the install. After that STOP AND THINK. Do you need any drivers for WIFI(prol not but make sure). Once you put the HDD Back YOU WILL NEED INTERNET!! Also a usb hub with a keyboard and mouse during set up helps but at least a usb keyboard is necessary. Now did you install, does it run, is your PCMCIA WIFI working? GOOD 

While it is still in the laptop/desktop run your package manager. Install:
Setserial
Fpit

I also installed Fluxbox For day to day usage. You will find with only 128mb RAM Gnome runs slow.

NEXT: Put the HDD back in the tablet. Start in up, It my say something about LOW-GRAPHICS Mode, if it does let it auto-reconfigure this first time only. 

Lets get the touch screen working
OK open your terminal. RUN 
**dmesg | grep /dev/ttyS***

I should print out something like this

/dev/ttyS0, UART, 16550A, Port: 0x03f8, IRQ:4
**/dev/ttyS1, UART, 16550A, Port: 0xfd68, IRQ:5**
/dev/ttyS2, UART, unknown, Port: 0x03e8, IRQ:4
/dev/ttyS3, UART, 16550A, Port: 0x02e8, IRQ:3

It might be somewhat different but what you are looking for is **0xfd68. **Write down the IRQand the ttyS number. You will need them soon.

Now RUN
**sudo gedit /var/lib/setserial/autoserial.conf**

Comment out every line except the one line that has the serial port that you noted earlier. Then change **16550A** to **16450** on the serial port needed. It should look like this. 

**/dev/ttyS1 uart 16450 port 0xfd68 irq 5 baud_base 115200 spd_normal skip_test**

MAKE SURE THE IRQ MATCHES WHAT YOU WROTE DOWN OR IT WILL CAUSE THE SYSTEM TO CRASH!!!!!! SAVE and EXIT

Next RUN
[B]dpkg-reconfigure setserial
[/B]
Using the arrow keys and enter set it to[B] manual

[/B]and last but not least RUN
**sudo gedit /etc/X11/xorg.conf**

It will look something like this

Section "Device"
            Identifier          "Configured Video Device"
EndSection

Section "Monitor"
            Identifier          "Configured Monitor"
EndSection

Section "Screen"
            Identifier           "Default Screen"
            Monitor              "Configured Monitor"
            Device               "Configured Video Device"
EndSection

Now I was Puzzled. There is no ServerLayout Section. This was the Problem I ran into the first time. This Time However I made one. :) Add this above the [B]Section "Device"

[/B]Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen    0  "Default Screen" 0 0
    Input Device    "Mouse1"  "SendCoreEvents"
EndSection

Then Add This Below **Device "Configured Video Device" EndSection**

Section "InputDevice"
    Identifier    "Mouse1"
    Driver    "fpit"
    Option    "Device"    "/dev/ttyS_"     # <----Add the ttyS number we wrote down #
    Option    "BaudRate"    "9600"
    Option    "Passive"
    Option    "TrackRandR"    "true"
EndSection

That should do it. Restart the the tablet and use the touchscreen.

I would like to thank the entire Linux community for making this possible. I must have look at 15 different forum postings about this, and through a combination of the relevant parts my Fujitsu C-500 is running wonderful and is OPEN-SOURCE. I hope this will help someone else out the way others helped me. If you have any questions just ask of e-mail me. Once again thank You EVERYONE The Linux Community is the BEST. Take Care.

---

### Post by cssetti on 2009-09-16
The C-500 at least has a lot of info online, i'm working on a LT P-600 and i can't find hardly ANY information on the net!!

I have tried countless things, but one question, what if there is no results for the dmesg | grep /dev/ttys* ?

I know my touch screen was working because it had windows 2k on it when my friend let me borrow it to install xubuntu jaunty


Here is the best site i've found yet for some info about the p-600
[http://chiyostetanus.bravehost.com/p600.html](http://chiyostetanus.bravehost.com/p600.html)

but that didn't work either

---

### Post by Ondrush on 2009-09-23
hi, i just bought this tablet and tried xubuntu (i tried ubuntu 8.04, xubuntu 9.04 and now there runs xubuntu 8.10) on it and everything but touchscreen works fine. i followed your instructions but i have problem with Section ServerLayout. if i add this section to the xorg.conf, X-server runs only in low graphics mode and it says "Error parsing config file". has anyone tip how to get it works?

---

### Post by Favux on 2009-09-23
Hi Ondrush,

Welcome to Ubuntu Forums!

Maybe try changing this line in "ServerLayout":
```
Identifier "X.org Configured"
```
to?:
```
Identifier "Default Layout"
```

---

### Post by Ondrush on 2009-09-23
Favux: Thanks, but it wasn't it. munchen800 has in his section ServerLayout space between "Input" and "Device"... trivial mistake, i should seen it before...

---

### Post by munchen800 on 2009-10-20
It you run into the problem ondrush had then you set up the xorg.conf wrong

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen    0  "Default Screen" 0 0
    Input Device    "Mouse1"  "SendCoreEvents"
EndSection

Section "Device"
            Identifier          "Configured Video Device"
EndSection

Section "Monitor"
            Identifier          "Configured Monitor"
EndSection

Section "Screen"
            Identifier           "Default Screen"
            Monitor              "Configured Monitor"
            Device               "Configured Video Device"
EndSection

Section "InputDevice"
    Identifier    "Mouse1"
    Driver    "fpit"
    Option    "Device"    "/dev/ttyS_"     # <----Add the ttyS number we wrote down #
    Option    "BaudRate"    "9600"
    Option    "Passive"
    Option    "TrackRandR"    "true"
EndSection

This is what it should look like, sorry if it got a little confusing in the original post. If and when it starts in low-graphics mode do a auto-reconfigure then make the changes shown above. The **Identifier     "X.org Configured"** tells xorg to use the hardware the way it was auto-configured. The only thing we really want to add is the touchscreen as a mouse. I am not sure why but xorg will not add the **Section "ServerLayout"** on its own. So all you should have to add is the **"ServerLayout"** and the **"InputDevice"** for **"Mouse1"**.
OK back to the point (sorry I tend to ramble) You can just copy and paste the layout above and just add the number for the tty on the **"Mouse1"**.

As far as the **dmesg | grep /dev/ttys*** It lists all the serial devices attached to the computer, so I am assuming that if it doesn't list anything then there are not any serial devices or you didn't run as root. That is an assumption though perhaps post whatever is does (error, or whatever) and I can help.

Once again Thanx Guys.

---

