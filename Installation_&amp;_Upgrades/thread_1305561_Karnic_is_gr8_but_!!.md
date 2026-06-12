---
title: "Karnic is gr8 but !!"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by drvista on 2009-10-30
karmic is super and realy the best ever linux i used but
1. fn+f5 or f6 doesn't work ??? the control volume
2.video aspect ratio all pictures are taller ??
can any one help me
using amilo pi 1505

EDIT [COLOR="Red"][CENTER]**[SIZE="4"]This is  Fix Fn F5/F6 [/SIZE]**[/CENTER][/COLOR]

1) Back up your current evdev driver, just in case. This line will back up to your home directory (~/), you can modify it if you want; just remember where you put it for later.


 > cp /usr/lib/xorg/modules/input/evdev_drv.so ~/






2) This will download the current evdev source for you:



> 
apt-get source xserver-xorg-input-evdev




3) Inside the folder for the evdev version you just downloaded, you'll find a 'src' folder. Look for the block that contains:

 

>    /* Filter all repeated events from device.
       We'll do softrepeat in the server, but only since 1.6 */
    if (value == 2
#if GET_ABI_MAJOR(ABI_XINPUT_VERSION) <= 2
        && (ev->code == KEY_LEFTCTRL || ev->code == KEY_RIGHTCTRL ||
            ev->code == KEY_LEFTSHIFT || ev->code == KEY_RIGHTSHIFT ||
            ev->code == KEY_LEFTALT || ev->code == KEY_RIGHTALT ||
            ev->code == KEY_LEFTMETA || ev->code == KEY_RIGHTMETA ||
            ev->code == KEY_CAPSLOCK || ev->code == KEY_NUMLOCK ||
            ev->code == KEY_SCROLLLOCK) /* XXX windows keys? */
#endif
            )
	return;





[COLOR="Red"]**Above  it**[/COLOR], on a new line, copy and paste the following code:


   >  /* fix events for volume keys */
    if(ev->code == KEY_VOLUMEDOWN || ev->code == KEY_VOLUMEUP) //MODIFY THIS LINE
    { 
    //post a keydown and then a keyup, as media keys have no automatic key-up
    xf86PostKeyboardEvent(pInfo->dev, code, 1);
    xf86PostKeyboardEvent(pInfo->dev, code, 0);
    return;
    }  



Then install the needed packages for compiling

>  sudo apt-get install build-essential libtool automake gcc xorg-dev xutils-dev




Compile. Firstly, we'll need to make sure you have everything set up to compile. Install anything this step requires, or just continue if it tells you you're 'already newest version'. You'll need to type in your password to give yourself installation rights.

> cd xserver-xorg-input-evdev-2.2.5
chmod +x autogen.sh
./autogen.sh
make
sudo make install
sudo cp /usr/local/lib/xorg/modules/input/evdev_drv.so /usr/lib/xorg/modules/input/


Recovery

If your keyboard/mouse stopped working, don't panic! Instead, switch to one of your virtual terminals by pressing CTRL+ALT+F2. Then, execute the following command:

Code:

> sudo cp ~/evdev_drv.so /usr/lib/xorg/modules/input/

That will restore your original driver. Then, restart the computer with the following commands.

Code:

> sudo shutdown -r 0


###############################################################################
#**[COLOR="Red"]Fix Aspect ratio[/COLOR]**
#Add "xrandr --fbmm 239x212 --rate 60 --dpi 96" to startup
###############################################################################

---

