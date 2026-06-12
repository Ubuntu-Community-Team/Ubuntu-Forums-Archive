---
title: "Disabled trackpad while typing?"
date: 2014-10-03
forum: Hardware
---

### Post by loug28 on 2014-10-03
Hello all,

I just installed Lubuntu 14.04 onto a Gateway m3715u and when I went into settings > mouse and keyboard I noticed there is no way to 'disable trackpad' when typing.

I was wondering if there was a piece of software that I should install to get this? or a command line thing? or ANYTHING because as a writer that is a big deal to me. I went with Lubuntu because this machine is 6 years. Even XFCE caused it to shut down due to overload.

---

### Post by sudodus on 2014-10-03
Hi, I use the following: (I made TT, when there was problems with Touchpad-indicator; but I think it is working well again).

GUI:
[I][B]
Touchpad-indicator[/B][/I]

[http://ubuntuhandbook.org/index.php/2013/08/install-touchpad-indicator-in-ubuntu-13-10-saucy/](http://ubuntuhandbook.org/index.php/2013/08/install-touchpad-indicator-in-ubuntu-13-10-saucy/)

Text:
[I][B]
TT (touchpad-toggle)[/B][/I]

Append to **/etc/bash.bashrc** (for all users) or to **~/.bashrc** for only you

```
alias TT='touchpad-toggle'

###

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

####

alias TT
```

---

