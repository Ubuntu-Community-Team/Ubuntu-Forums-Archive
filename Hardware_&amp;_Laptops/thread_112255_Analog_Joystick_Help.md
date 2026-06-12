---
title: "Analog Joystick Help"
date: 2006-01-03
forum: Hardware &amp; Laptops
---

### Post by sharke on 2006-01-03
To get my analog joystick to work
sudo modprobe ns558
sudo rmmod ns558
sudo modprobe ns558
I have to load it twice wont work if loaded once
How do i get this to be done at boot.
Regards
Sharke

---

### Post by jmb365 on 2006-02-07
[QUOTE=sharke]To get my analog joystick to work
sudo modprobe ns558
sudo rmmod ns558
sudo modprobe ns558
I have to load it twice wont work if loaded once
How do i get this to be done at boot.
Regards
Sharke[/QUOTE]
Here what you do:

gedit /etc/init.d/joystick

# --------Cut and paste lines below -----------------------------------------------
# Carry out specific functions when asked to by the system
case "$1" in
  start)
    echo "Enabling Joystick"
    modprobe ns558
    rmmod ns558
    modprobe ns558
#  and any other commands you need for your system...
    echo "DONE!"
    ;;
  stop)
    rmmod joydev
    rmmod analog
    echo "DONE!"
    ;;
  *)
    echo "Usage: /etc/init.d/joystick {start|stop}"
    exit 1
    ;;
esac

exit 0

# --------Cut above this line ------------------------------------------------------

Make it executable:
sudo chmod 755 /etc/init.d/joystick

Update the system to run it all run levels
sudo update-rc.d joystick defaults

Start the command
sudo /etc/init.d/joystick start

Enjoy!
JMB

---

### Post by oxpack on 2006-02-14
After each boot up the device files are gone that I just installed for the joystick. In particular are /dev/input/js0 ,/dev/input/js1, /dev/input/js2, /dev/input/js3.

I install them with the mknod command and actually had the joystick (MS sidewinder joystick) working at one point but they then disappear. It must be something in devFS that is clearing them but what?

Any help?

---

