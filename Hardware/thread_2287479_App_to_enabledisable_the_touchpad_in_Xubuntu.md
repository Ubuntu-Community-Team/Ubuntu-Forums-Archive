---
title: "App to enable/disable the touchpad in Xubuntu"
date: 2015-07-19
forum: Hardware
---

### Post by Allan_Larangeiras on 2015-07-19
Hi guys,

I'm a Xubuntu user for a while and one point that annoys me is the absence of a shortcut to enable and/or disable the touchpad.
Searching around i found the touchpad-indicator that almost do what i want.
So, i decided to make my own app in golang.
You can configure a keyboard shortcut that calls the app.
I've hosted the source code and binary on github.

[https://github.com/alarangeiras/touchpad-switcher](https://github.com/alarangeiras/touchpad-switcher)

Let me know if it needs some improvement.

Regards

---

### Post by sudodus on 2015-07-20
I agree, that we need a convenient app for this purpose. I made this simple function, that works in bash, and it is useful in Xubuntu and Lubuntu. It can be appended to **~/.bashrc**

```
function touchpad-toggle {

# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
    echo "touchpad OFF"
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
    echo "touchpad ON"
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
}
```

Adding the alias TT

```
alias TT='touchpad-toggle'
```

makes it more convenient to use, but I'm sure your tool is more user friendly :-)

---

