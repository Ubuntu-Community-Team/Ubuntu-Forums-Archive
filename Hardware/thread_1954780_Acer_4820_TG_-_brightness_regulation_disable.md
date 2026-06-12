---
title: "Acer 4820 TG - brightness regulation disable"
date: 2012-04-08
forum: Hardware
---

### Post by The_ERROR on 2012-04-08
Hi

I'm having problem, that brightness regulation isn't too much good for me. Without parameters I'm having 3 steps of brightness, with acpi_backlight=vendor kernel parameter I'm having more levels, but it not allow me to use it properly. For example it starts about 1/3 of brightness level as is in windows = not exactly what I would like to have.
 
Best solution for me seems to be disable native brightness handling and mount my prepared script which will handle those by itself. So I would like to turn off native key-bindings so I would be able to use mine customized script.

```
#!/bin/sh
#
# filename: backlight.sh
# description: control the backlight brightness of a Google CR-48
#
# usage: ./backlight.sh (up|down)
#
# uses 'cat' to write values to the video backlight device's 
# brightness file.
#

# location of the brightness device file
#FILE=/sys/class/backlight/i915_backlight/brightness
FILE=/sys/class/backlight/intel_backlight/brightness
# current value
CURRENT=`cat ${FILE}`

# command, whether up or down
COMMAND="$1"
# increment up/down by this amount
INCREMENT=20
# calculate a value to go up
UP_VAL=`echo "${CURRENT} + ${INCREMENT}" | bc`
# calculate a value to go down
DOWN_VAL=`echo "${CURRENT} - ${INCREMENT}" | bc`

# do not exceed 976, if increasing brightness
if [ ${UP_VAL} -gt 976 ]; then
  UP_VAL=976
fi

# do not exceed 0, if decreasing brightness
if [ ${DOWN_VAL} -lt 0 ]; then
  DOWN_VAL=0
fi

# set the value depending on the argument to this script, or show usage info
case ${COMMAND} in
up)
  echo ${UP_VAL} > ${FILE}
  ;;
down)
  echo ${DOWN_VAL} > ${FILE}
  ;;
*)
  echo "Usage: $0 (up|down)" 1>&2
  exit 1
esac

```It changing value directly in 
```
/sys/class/backlight/intel_backlight/brightness
```based on actual value which is increased/decreased by $INCREMENT based on parameter UP/DOWN.

This script is working great for me, and I would like to use this instead of the native handling, at least till it would be fixed in kernel.

Do you have some idea how to reach those? Thanks.

---

