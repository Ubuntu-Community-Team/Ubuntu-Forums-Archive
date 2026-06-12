---
title: "set key to run a script"
date: 2008-07-02
forum: Hardware
---

### Post by oodlesOfmoodles on 2008-07-02
I have an x61 Tablet and I'm wondering if it's possible to set the rotate key 0x6c to run a rotate script (which I have).

Is this possible?

Thanks guys!

---

### Post by phibuntu on 2008-08-28
I have the X61 myself.
I used the tool "xbindkeys" to attach the key-event 209 (which is the rotate button) to the following script using 3 as program argument:

```
#!/bin/sh
 
 output=LVDS
 if [ "$XROT_OUTPUT" ]
 then    
         output=$XROT_OUTPUT;
 fi
 devices="stylus cursor"
 
 geomnbr=0
 xrandr=normal
 wacom=normal

if [ "$1" == "-" ] || [ "$1" == "+" ] || ! [ "$1" ]; then    
         operator="$1";
         [ "$1" ] || operator='+';
         case `xrandr --verbose | grep "^$output " | sed "s/^[^ ]* [^ ]* [^ ]* ([^(]*) \([a-z]*\).*/\1/"` in
                 normal)         geom=0;;
                 left)           geom=1;;
                 inverted)       geom=2;;
                 right)          geom=3;;
         esac
         let geom=${geom}${operator}1+4
         let geom=${geom}%4
else    
         geom="$1"
fi
 
case $geom in
         1)      wacom=2; xrandr=left ;;
         2)      wacom=3; xrandr=inverted ;;
         3)      wacom=1; xrandr=right ;;
         *)      wacom=0; xrandr=normal ;;
esac
 
echo "xrandr to $xrandr, xsetwacom to $wacom" >&2
 
if xrandr --output "$output" --rotate "$xrandr"; then
         for d in $devices
         do      
                 xsetwacom set "stylus" Rotate "$wacom"
         done
fi
 
 #workaround for linuxwacom bug
if [ "`xsetwacom get stylus Mode`" == '1' ]; then
         for d in $devices
         do      
                 xsetwacom set stylus CoreEvent "off"
                 xsetwacom set stylus Mode "off"
         done
         { sleep 1;
         for d in $devices
         do      
                 xsetwacom set stylus Mode "on"
                 xsetwacom set stylus CoreEvent "on"
         done; } &
fi
```

---

### Post by phibuntu on 2008-08-28
strange: My "rotate" button has the keycode 0xd1 ???

---

