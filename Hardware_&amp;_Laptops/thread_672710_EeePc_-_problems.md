---
title: "EeePc - problems"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by greenwom on 2008-01-19
I'm writing this from my eeepc, so if there  a few typos...

There are a bunch of guides and multiple scripts out there.  I'm trying to avoid them, 

I've stuck with this guide:  [https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC)

I've got solid wifi, sound, everything is working with gusty installed to the "hard drive"
My problem is that I do not have the the following hot keys working: 
     * wifi on/off
     * audio up/down/mute
     * I haven't tested the LCD /vga port hot key on a real display but nothing happens

it apears that nothing happens when I close the lid.

So help me sort through the clutter and get me up to speed please, I can live with this setup but I'm sure it can be fixed.

---

### Post by Daelyn on 2008-01-22
[http://wiki.eeeuser.com/](http://wiki.eeeuser.com/)

Dedicated site to the Asus EeePC and all that comes with it.

There is custom installers for ubuntu etc there as well as info enough to make your eyes bleed.

---

### Post by greenwom on 2008-01-22
That's a great site for the xandros OS but I have gusty installed.  

Right now I don't have "hot keys" functions but everything else is doing ok.  
I'm also looking for a good guide on configuring compiz.

---

### Post by Daelyn on 2008-01-22
> **greenwom said:**
> That's a great site for the xandros OS but I have gusty installed.  

Right now I don't have "hot keys" functions but everything else is doing ok.  
I'm also looking for a good guide on configuring compiz.

[http://wiki.eeeuser.com/#installing_operating_systems](http://wiki.eeeuser.com/#installing_operating_systems)
Are details of how to install the customized xubuntu, details on gutsy etc etc.

Well, to be honest, I do not know exactly how much they cover, but if I had a Asus EeePC (I'm soon gonna get one :P ) I would go there instantly and follow the ubuntu/xubuntu guide :)

If it does nto help, well, sorry mate, we'll investigate som further here.

---

### Post by victorbrca on 2008-01-23
Download the latest version of eeeXubuntu and use it. Everything works with no need for extra scripts...

[http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization](http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization)

Vic.

---

### Post by victorbrca on 2008-01-23
And here's another one..

[http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/)

---

### Post by greenwom on 2008-01-26
I've read through most of these links.  I'm happy with the metacity install with the regular gusty CD.  I'm still no a xfce fan.  Anyway.
So all is working with the exception of the hot keys.  eeexubuntu reports that they've fixed them, just not how and they don't say if they fixed the function-f5 hot key to toggle to the VGA port.  Anyone see  that

---

### Post by steveguy on 2008-02-05
Like you, I'm not a fan of xfce - but I found the easy way to get my eeePc running Kubuntu (my preference) was to install eeeXubuntu, then apt-get install kubuntu desktop. Then I just removed the packages I didn't want. Works like a charm (and much easier than hacking it yourself!)

---

### Post by greenwom on 2008-02-05
> **steveguy said:**
> Like you, I'm not a fan of xfce - but I found the easy way to get my eeePc running Kubuntu (my preference) was to install eeeXubuntu, then apt-get install kubuntu desktop. Then I just removed the packages I didn't want. Works like a charm (and much easier than hacking it yourself!)

Good call on that...  I hadn't thought about that.  Can you verify if your vga out works

---

### Post by Daelyn on 2008-02-06
Good tip!

Will do the same when I get my EeePC :)

The simplest solutions are simply not thought of. LOL

---

### Post by scaine on 2008-02-07
I just installed Ubuntu 7.10 from CD, then installed the custom kernel (you double click on the deb file - it's that simple) and followed the (very) simple instructions here :[http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to:_use_custom_Eee_Linux_kernel](http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to:_use_custom_Eee_Linux_kernel).

Everything working except that apps that use the webcam crash when Compiz Fusion is turned on.  Which doesn't bother me at all.

---

### Post by greenwom on 2008-02-07
Here's an odd one, I had the volume control function keys working via another thread's instructions and now they no longer work.....

a few of these options are driving me a bit nuts although the computer is very functional..

---

### Post by victorbrca on 2008-02-08
> **greenwom said:**
> Here's an odd one, I had the volume control function keys working via another thread's instructions and now they no longer work.....

a few of these options are driving me a bit nuts although the computer is very functional..

I removed my eeeXubuntu install and installed Ubuntu following the instructions on the link scaine gave, and it woks for me. I had to re-install the script and reboot after running the first update.

[Script]("http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to_use_the_ubuntu-eee_script")


The only thing weird is that fn+F6 is supposed to overclock to 900MHz, I get the warning saying that it changed to 900MHz, but my conky stays the same at 675MHz.

Vic.

---

### Post by greenwom on 2008-02-09
I haven't used this scripy yet, I've accomlshed most of the steps already ia other means.
Can any one tell me if this script or the EEEcubuntu distrobution has the vga out working.

Right now I need to restart X with the external monitor hooked up.  The I get a twi-view style dual screen..  I would really like to be able to toggle to the 2nd display and turn off the laptop's screen.  Without having to log-out and in.

---

### Post by i.am.technofreak on 2008-06-06
I use a script in /usr/bin called extmon, from eeeuser forums, that replaces the lcd with an external something, at full res.
hit ALT-F2 and extmon toggle does it.  I'm still trying to figure out how to tie it to Fn-F5

heres the script:
```
#!/bin/bash

sleep=5s #set the length of time to wait between polls in daemon/monitor mode.

function getXuser() {
       #This checks the current user and assigns authority if necessary
       user=`finger| grep -m1 ":$displaynum " | awk '{print $1}'`
       if [ x"$user" = x"" ]; then
               user=`finger| grep -m1 ":$displaynum" | awk '{print $1}'`
       fi
       if [ x"$user" != x"" ]; then
               userhome=`getent passwd $user | cut -d: -f6`
               export XAUTHORITY=$userhome/.Xauthority
       else
               export XAUTHORITY=""
       fi
}

function vga-is-connected {
    #this checks for a physical connection
    return $(xrandr --prop |grep -q "VGA connected")
    }

function vga-enable {
    # this sets up the VGA out. Depending on the size of the screen and the ability of 
    # your video  card, you might want to try connecting differently.
    echo Enabling VGA output
    # these commands are a true dual-screen setup, with the mouse going from one to the other
    # Note that you must use the correct device names here for it to work right.
    # on the Eeepc, you can't have a monitor wider than 2048x2048. With the Eee's 800x480,
    # you are left with  monitor of dimensions 1248x1568 or less.
    #$ xrandr --output VGA --right-of LVDS --auto    # [LVDS] [VGA]
    #$ xrandr --output VGA --left-of LVDS --auto    # [VGA] [LVDS]
    #$ xrandr --output VGA --above LVDS --auto    # [VGA]/[LVDS] #vertical placement

    # This command makes both screens mirrored, with the resolution of the VGA monitor
    xrandr --output VGA --auto --output LVDS --off
    }

function vga-disable {
    # Simply kill the VGA output. You likely don't need to tweak this one.
    echo Disabling VGA output
    xrandr --output VGA --off --output LVDS --auto
    }

function vga-is-active {
    # this line crudely checks to see if the default for the main screen is the active one
    # For other laptops/computers you would need to find the resolution and replace this with
    # the default for your system. See header for info.
    default_res='800 x 480'
    if xrandr --prop | grep -q "current $default_res"
        then return 1
        else return 0
    fi
    }

function vga-toggle {
    if vga-is-active;
        then vga-disable;
        else vga-enable;
    fi
    }

function vga-monitor {
    #monitors the VGA port, and automatically switches to it when it can
    vgaactive=0
    while true;do
    if vga-is-connected; then 
        if vga-is-active
            then vgaactive=1;
            else vga-enable
        fi 
    else     
        if [[ $vgaactive == 1 ]] 
            then vga-disable;vgaactive=0;
            #else echo -n;#do nothing
        fi 
    fi
    sleep $sleep
    done
    }

function print-help {
    echo "\
    enable,on    turn on vga output
    disable,off    turn off vga output
    monitor        Watches for when a VGA connector is plugged in, and will then
            automatically turn on the VGA connection. When the VGA connector is 
            removed, it will then disable the output.
    daemon        same as monitor, but forks into background, and silences output
    status        Returns true if VGA connector is enabled. No real uses come to mind,
            but it was easy to implement.
    toggle        If VGA is active, kill it. If it's not, attempt it.
    help        print this handy message
    --help        I hate getting an error for --help, so it's in here too.
    status        returns the status"
    }

##MAIN

for x in /tmp/.X11-unix/*; do
   displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
   getXuser;
   if [ x"$XAUTHORITY" != x"" ]; then
       export DISPLAY=":$displaynum"

       case $1 in
        enable)  vga-is-connected && vga-enable ;;
        on)    vga-is-connected && vga-enable ;;
        disable) vga-disable ;;
        off) vga-disable ;;
        toggle) vga-toggle ;;
        status)  exit vga-is-active ;;
        monitor) vga-monitor;;
        #same as monitor, but forks into the background and runs silently
        daemon)  (vga-monitor>/dev/null&) ;;
        help) print-help ;;
        --help) print-help ;;
        *)    echo "*usage: $0 enable|disable|toggle|status|daemon|help"    ;;
       esac
   fi
done
```

then make it executable from any user without root(a good thing)
```
sudo chmod 777 /usr/bin/extmon
```

---

