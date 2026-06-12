---
title: "Feisty on Thinkpad T60: video out problem"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by lamborghiniwang on 2007-05-31
I installed Feisty fawn (32bit) onto my Thinkpad T60, and most of the specially keys(hibernate, suspend, wireless on/off etc) works perfectly except the Fn+F7 keys which are supposed to control the video out when external monitor is connected. 
 I made a script (ibm-video.sh) as suggested by [Micampe@Thinkwiki.org]("http://www.thinkwiki.org/wiki/Talk:Fglrx"). 

**/etc/acpi/ibm-video.sh**
```

#!/bin/sh

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

getXconsole;

change_resolution() {
        if [ x"$XAUTHORITY" != x"" ]; then
                if [ x"`xrandr -q | grep $1[[:space:]]x[[:space:]]$2 | cut -b -1`" != x"*" ]; then
                        xrandr -d $DISPLAY -s $1x$2
                fi
        fi
}

change_monitor() {
        if [ x"$XAUTHORITY" != x"" ]; then
                aticonfig --enable-monitor=$1 &>/dev/null
        fi
}

if [ x"$XAUTHORITY" != x"" ]; then

        CURRENT=`aticonfig --query-monitor | grep Enabled | cut -b 21- | \
                        sed -e 's/lvds/LCD/g' -e 's/crt1/CRT/g' -e 's/tv/TV-Out/g' -e 's/,/ and/g'`

        CHOICE=`zenity --width=300 --height=350 --window-icon=/usr/share/pixmaps/ati.xpm \
                --title 'Video output switcher' \
                --text='Choose the video output\n\nCurrent setting: $CURRENT\n' \
                --list --radiolist --column 'x' --column 'video output' \
                true 'LCD' \
                false 'CRT' \
                false 'TV-Out' \
                false 'LCD and CRT' \
                false 'LCD and TV-Out' \
                false 'CRT and TV-Out'`

fi

case $CHOICE in
        LCD)
                change_monitor lvds
                change_resolution 1400 1050
                ;;
        CRT)
                change_monitor crt1
                change_resolution 1024 768 
                ;;
        TV-Out)
                change_monitor tv
                change_resolution 1024 768
                ;;
        LCD\ and\ CRT)
                change_monitor lvds,crt1
                change_resolution 1024 768
                ;;
        LCD\ and\ TV-Out)
                change_monitor lvds,tv
                change_resolution 1024 768
                ;;
        CRT\ and\ TV-Out)
                change_monitor crt1,tv
                change_resolution 1024 768
                ;;
esac

```
By manually running this script above, I can switch between external monitor and LCD, but I can't find a way to link it with the Fn+F7 keys. I tried to modify the /etc/acpi/events/ibm-videobtn as following as suggested by the post on thinkwiki.org, but it doesn't work.

**/etc/acpi/events/ibm-videobtn**
```

# /etc/acpi/events/ibmvideobtn
# This is called when the user presses the video button. It is currently
# a placeholder.

event=ibm/hotkey HKEY 00000080 00001007
action=/etc/acpi/ibm-video.sh


```

I also tried to create a shortcut using gconf-editor, but it seems gconf-editor doesn't recognize the Fn+F7 keys.

Is there a way for me to excute the */etc/acpi/ibm-video.sh* script when I click the Fn+F7 button? 
PS:My T60 has an ATI Mobility X1400 video card, and I have the ATI fglrx driver installed (version 8.34.8 which comes with Feisty Fawn)

---

### Post by lamborghiniwang on 2007-05-31
OK, I think I solved the problem myself. It seems all I need to do is to modify the file **/etc/modprobe.d/ibm_acpi.modprobe** into this:
```

options ibm_acpi hotkey=enable,0xffef experimental=1

```

The old hex number in the file was 0xff9f.
Now I can switch between LCD and external monitor, single or dual-display by simply click Fn+F7. :D

---

### Post by Nihil Videmus on 2007-06-19
I have the same issue w/my T60; how would I customize that script to run on a 24" 1920x1200 LCD? Thanks in advance for any help.

---

### Post by jpfinley on 2007-06-26
Thanks for posting this - I've run into this problem as well and haven't been able to find anyone in the same boat.

I'd love to try this script out, but I am running a T60 with the "Mobile 945GM/GMS/940GML Express Integrated Graphics Controller". Do you know if this would work with my laptop?

Thanks!

---

### Post by braverock on 2007-12-16
> **Nihil Videmus said:**
> I have the same issue w/my T60; how would I customize that script to run on a 24" 1920x1200 LCD? Thanks in advance for any help.

There is quite a lot of information on "Big desktop" mode here which *might* allow you to support different resolutions on the internal and external displays.

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-65328#screenswitch]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-65328#screenswitch")

Basically, you'll probably need to play with aticonfig and try to create a configuration that will work to support your external monitor, although I know that many people reported problems with the open source and proprietary ati drivers when they were first released.  I just run my external monitor at the same resolution as the internal panel, which isn't great, but works without too much fiddling.

Regards,

   - Brian

---

### Post by braverock on 2008-01-13
> **braverock said:**
> There is quite a lot of information on "Big desktop" mode here which *might* allow you to support different resolutions on the internal and external displays.

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-65328#screenswitch]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-65328#screenswitch")


Well, when I wrote that post, the link worked.  That page is now gone.  I found a cached version, so I'll quote from the IBM source document and hopefully help others out.

> 
How to Make a Hotkey for screen switching from LCD to CRT+DVI in Big desktop mode
Note: This behavior currently has been tested with and assumes that all monitors are capable of matching the panel native resolution. For ThinkPad T60p system, it is 1600x1200. The behavior with different resolutions is undefined at this stage and will possibly expose problems in the implementation.

   1. In a terminal window, use the su (switch user) command to obtain root privileges.
   2. Type aticonfig --dtop=horizontal to explicitly configure the system to Big desktop.
   3. Go to K Menu > Logout, and select Restart Computer to apply change in xorg,.conf.
   4. Create a script file that will enable CRT and DVI in big desktop mode. The example below is a script file that will automatically switch CRT+DVI as display device. The "xrandr -s 3200x1200" will change the resolution 3200x1200 (assuming both CRT and DVI to be UXGA) setting the system to big desktop.
      For example, content of script file:
      #!/bin/bash
      aticonfig --enable-monitor=crt1,tmds1
      xrandr -s 3200x1200
      exit
      Note: To display all possible resolutions, run "xrandr" in konsole.
   5. Save the script file to your desired directory. Example: /usr/lib/powersave/scripts/. This is the same directory with thinkpad_acpi_events.
   6. Run in console "chmod +x (name of script file)
   7. Go to /usr/lib/powersave/scripts.
   8. Open "thinkpad_acpi_events" file with a text editor.
   9. Look for "HOTKEY="Fn+F6"" text.
  10. Add the following lines "run_on_xserver "/usr/lib/powersave/scripts/" (name of script file)
      &". Then add ";;" at the next line. It should look like this:
      4102) HOTKEY="Fn+F6"
      run_on_xserver "/usr/lib/powersave/scripts/(name of script file) " &
      ;;
  11. Exit and save the thinkpad_acpi_events script.
  12. Fn+F6 should now be able to switch from LCD to CRT+DVI as Big Desktop.

To go back to LCD, press Fn+F7.

<...>
Remove garbage files in /var/lib/xdm/authdir/authfiles/.

   1. In a terminal window, type su (switch user) command to obtain root privileges.
   2. Type rm /var/lib/xdm/authdir/authfiles/*
   3. Go to K Menu > Logout, and select Restart Computer.



also, one problem that I had was getting the external monitor to work at all if I didn't boot with it connected.  This can be remedied with:

```

aticonfig --query-monitor

```
and 
```

aticonfig --enable-monitor=crt1,lvds

```

Regards,

  - Brian

---

