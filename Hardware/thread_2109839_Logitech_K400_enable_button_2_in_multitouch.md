---
title: "Logitech K400 enable button 2 in multitouch"
date: 2013-01-28
forum: Hardware
---

### Post by domenan on 2013-01-28
Hi all,

I bought a Logitech K400 with wireless keyboard with touchpad integrated.

The problem is that the system doesn´t recognize the middle button (button 2) done pressing with 2 fingers in the touch.

The touch is working fine. Multitouch scrolling is working.

Here is my xinput

```
$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:400e    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]

```If I run "xinput test 9" the system catch all the events a part the double touch or the triple touch.
Even xev down not catch these events.

Any idea how to enable the events?

---

### Post by domenan on 2013-01-29
I did a better research in internet and come out that the middle click function doesn't work because is not supported in the keyboard firmware.

That mean no hope to have it works. I'm so disappointed that a £ 30 device doesn't have a good multitouch implementation. I would return it if I didn't buy in the web for half price.

By the way if found a really bad work around.
I'm using the command "xdotool click 2" connected to a keyboard key.

Because I'm using fluxbox I added this line in .fluxbox/keys

```
133 :Exec xdotool click 2
``` 

In this way when I press the windows key the system emulate the middle click.

For who doesn't use the fluxbox can use the command  xbindkeys.

---

### Post by oooh on 2013-10-26
Mine worked perfect straigh away:

$ xinput 
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:4024	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; VF0700 Live! Cam Chat HD                	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]


cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
NAME="Ubuntu"
VERSION="12.10, Quantal Quetzal"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu quantal (12.10)"
VERSION_ID="12.10"

---

