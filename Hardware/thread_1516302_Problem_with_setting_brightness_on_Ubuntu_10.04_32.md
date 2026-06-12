---
title: "Problem with setting brightness on Ubuntu 10.04 32bit - HP 6735s"
date: 2010-06-23
forum: Hardware
---

### Post by mambo on 2010-06-23
Hi,

I have HP 6735s, and Ubuntu 10.04. In laptop there is ATI 3200 graphics card.

I placed Brightness Applet on panel, and it worked well until i decided,to
use AMD/ATI Proprietary FGLRX driver, which i activate from Hardware Drivers menu in order to enable/install Compiz effects later.

Compiz effects worked well , but now my applet is not working.
Also i want to mention that FN+F8(F7) keyboard combination never worked.

Any easy steps to fix this, because i just started with Linux.

Thanks in advance.

---

### Post by Lem98 on 2010-07-01
> **mambo said:**
> Hi,

I have HP 6735s, and Ubuntu 10.04. In laptop there is ATI 3200 graphics card.

I placed Brightness Applet on panel, and it worked well until i decided,to
use AMD/ATI Proprietary FGLRX driver, which i activate from Hardware Drivers menu in order to enable/install Compiz effects later.

Compiz effects worked well , but now my applet is not working.
Also i want to mention that FN+F8(F7) keyboard combination never worked.

Any easy steps to fix this, because i just started with Linux.

Thanks in advance.

Please open a terminal, and type:

**for file in $(ls /proc/acpi/video/*/LCD/brightness) ; \** [PRESS ENTER]
  **do { echo $file && cat $file && echo ; } ; done** [PRESS ENTER]

BTW: from now onwards, you'll always press ENTER at the end of a command line, OK? I won't rewrite it. :)
You should get this particular output:

```
/proc/acpi/video/IGFX/LCD/brightness
levels:  30 37 44 51 58 65 72 79 86 93 100
current: 100
```

Try typing (using a printed low number and the right name of the file):

**echo 37 | sudo dd of=/proc/acpi/video/IGFX/LCD/brightness**


Does the brightness go down? Fine. :)


Now do this, always in the terminal:

[B]sudo service acpid stop
sudo acpid -nl
gnome-system-log &[/B]

In the graphic window, select syslog on the left, and go to the bottom in the right panel. Now press fn+f8 and then fn+f7. Do you see the output in the log?
Pressing the above keyboard combinations produces events, and they should have been logged. We now have to catch these events and bind them to proper actions.

Close the window, go back to your terminal and type:

**sudo killall acpid**

Let's begin the editing. Type:

**gksudo gedit /etc/acpi/events/video_brightnessup**

The file must contain this and only this text:

```
# /etc/acpi/events/video_brightnessup
event=video/brightnessup
action=/etc/acpi/video_brightnessup.sh
```

Save, and close gedit.

Type:

**gksudo gedit /etc/acpi/events/video_brightnessdown**

The file must contain this and only this text:

```
# /etc/acpi/events/video_brightnessdown
event=video/brightnessdown
action=/etc/acpi/video_brightnessdown.sh
```

Save, and close gedit.
With the above two scripts, we catch the events and bind them to actions. Let's write the proper action scripts, now.

Type:
**gksudo gedit /etc/acpi/video_brightnessup.sh**

The file must contain this and only this text:

```
#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/IGFX/LCD/brightness |awk '{print $2}')


case "$CURRENT" in

100)
echo -n 100 > /proc/acpi/video/IGFX/LCD/brightness;
;;
93)
echo -n 100 > /proc/acpi/video/IGFX/LCD/brightness;
;;
86)
echo -n 93 > /proc/acpi/video/IGFX/LCD/brightness;
;;
79)
echo -n 86 > /proc/acpi/video/IGFX/LCD/brightness;
;;
72)
echo -n 79 > /proc/acpi/video/IGFX/LCD/brightness;
;;
65)
echo -n 72 > /proc/acpi/video/IGFX/LCD/brightness;
;;
58)
echo -n 65 > /proc/acpi/video/IGFX/LCD/brightness;
;;
51)
echo -n 58 > /proc/acpi/video/IGFX/LCD/brightness;
;;
44)
echo -n 51 > /proc/acpi/video/IGFX/LCD/brightness;
;;
37)
echo -n 44 > /proc/acpi/video/IGFX/LCD/brightness;
;;
30)
echo -n 37 > /proc/acpi/video/IGFX/LCD/brightness;
;;
*)
echo -n 100 > /proc/acpi/video/IGFX/LCD/brightness ;
;;
esac
```

Save, and close gedit.
Be sure that the script is executable:

**sudo chmod +x /etc/acpi/video_brightnessup.sh**


Type:

**gksudo gedit /etc/acpi/video_brightnessdown.sh**

The file must contain this and only this text:

```
#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/IGFX/LCD/brightness |awk '{print $2}')


case "$CURRENT" in

100)
echo -n 93 > /proc/acpi/video/IGFX/LCD/brightness;
;;
93)
echo -n 86 > /proc/acpi/video/IGFX/LCD/brightness;
;;
86)
echo -n 79 > /proc/acpi/video/IGFX/LCD/brightness;
;;
79)
echo -n 72 > /proc/acpi/video/IGFX/LCD/brightness;
;;
72)
echo -n 65 > /proc/acpi/video/IGFX/LCD/brightness;
;;
65)
echo -n 58 > /proc/acpi/video/IGFX/LCD/brightness;
;;
58)
echo -n 51 > /proc/acpi/video/IGFX/LCD/brightness;
;;
51)
echo -n 44 > /proc/acpi/video/IGFX/LCD/brightness;
;;
44)
echo -n 37 > /proc/acpi/video/IGFX/LCD/brightness;
;;
37)
echo -n 30 > /proc/acpi/video/IGFX/LCD/brightness;
;;
30)
echo -n 30 > /proc/acpi/video/IGFX/LCD/brightness;
;;
*)
echo -n 30 > /proc/acpi/video/IGFX/LCD/brightness ;
;;
esac
```

Save, and close gedit.
Be sure that the script is executable:

**sudo chmod +x /etc/acpi/video_brightnessdown.sh**


Almost done. We've to slightly change the way acpid runs and catch acpi events. Type:

**gksudo /etc/init/acpid.conf**

and change the last line of the file, appending a trailing "-n". Change:

*exec acpid -c /etc/acpi/events -s /var/run/acpid.socket*
in
```
exec acpid -c /etc/acpi/events -s /var/run/acpid.socket -n
```

Save, and close gedit.

Now restart the acpid daemon. Type:

**sudo service acpid start**

Done. Enjoy your brightness keyboard combinations. :D
-- 
Bye, Lem

---

### Post by cr0cK on 2010-07-16
Thanks a lot Lem98 :) This worked with some little bit arrangements like /proc/acpi/video/VGA/LCD/brightness for the brightness path and possible values that were differents.

---

### Post by nzcarrick on 2010-07-28
Just wanted to say that this post help a ton. Thank you Lem98 for the level of detail and time you took to write this!

Regards
Carrick

---

