---
title: "Writing a script to disable/enable the touchpad"
date: 2012-01-12
forum: Hardware
---

### Post by almikul on 2012-01-12
Hi,

I apologise if this thread is in a wrong forum section. I would like to ask for a quick example of how to write a script that would toggle the touchpad between on and off states. I can do it manually using
```
xinput set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 0
```
However, I would like the script to see what the value of "Device Enabled" is and invert it, thus achieving the toggling function. I have had some programming experience in the past, but I am just not sure how to get to this particular variable in this particular device using bash or sh script. 

Your inputs would be greatly appreciated :)

---

### Post by SteveDee on 2012-01-13
> **almikul said:**
> ...Your inputs would be greatly appreciated

I'm not a script kiddie, in fact I struggle to remember the damn syntax, as my example below will demonstrate. But at least this will bump your thread!

I ran "man xinput" and found that my touchpad id was "11" and that the properties can be read using the "--list-props" option.

The string "Device Enabled" is unique, so I've tried to pick this line out to find the touchpad state (enabled or disabled).

So my script looks like this:-
```

#!/bin/sh
TPadState=`xinput --list-props 11|grep "Device Enabled"`
echo $TPadState
if [ "$TPadState"="Device Enabled (139): 1" ]
then
	`xinput --set-prop 11 "Device Enabled" 0`
	echo "TouchPad disabled!"
else
	`xinput --set-prop 11 "Device Enabled" 1`
	echo "TouchPad enabled!"
fi

```

Unfortunately the "If" expression (as shown) is always true, and if I put spaces either side of "=" its always false....
...maybe you can make something of it.

---

### Post by almikul on 2012-01-13
SteveDee,

Thank you very much for your help! I modified your script in the following way
```
#!/bin/bash
TPadState=`xinput --list-props "ImPS/2 ALPS GlidePoint"|grep "Device Enabled"|tail -c -2`
echo $TPadState
if [ "$TPadState" = "1" ];
then
        `xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 0`
        echo "TouchPad disabled!"
else
        `xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 1`
        echo "TouchPad enabled!"
fi
```
and it worked :D As you can see, "tail -c -2" simplified this task a lot.

---

