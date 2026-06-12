---
title: "Laser Pointer - doosl"
date: 2020-03-04
forum: Hardware
---

### Post by archeryguru2000 on 2020-03-04
I recently purchased a laser presentation pointer from doosl (wireless presenter).  According to their website the Advance and Retract buttons are mapped to PageUp and PageDown; however, upon receiving the device I've now learned that these are, instead, mapped to ArrowUp and ArrowDown.  This is pesky because I use Reveal.js for my presentations and I kinda need to advance with PageDown instead of ArrowDown.  Not a big deal, I thought; I would simply remap these two buttons.  I've done this in the past for another device on a previous machine.  However, I'm really struggling here and could use some help.

Here's what I've tried thus far.

First, get the device id.
```

$: xinput

```
which returns the following (along with my other connected devices)
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Genius Wireless Mouse                   	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Genius Wireless Mouse                   	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Genius Wireless Mouse                   	id=13	[slave  keyboard (3)]

```

Okay, so far.  It's one of those three devices.  So, I test each one (idividually) to verify
```

$: xinput test 13
$: xinput test 14
$: xinput test 15

```

The only one that responds to the buttons that I would like remapped is id #13.
```

key press   111 
key release 111 
key press   116 
key release 116 

```
As such, I'd like to remap key 111 (ArrowUp) with 112 (PageUp) and key 116 (ArrowDown) with 117 (PageDown).  So, next I verify the key map with the following:
```

$: xinput get-button-map 13

```

And I'm presented with
```

device has no buttons

```

Umm, okay?  Just as a sanity check, both other id's give an expected return:
```

$: xinput get-button-map 14
1 2 3 4 5 6 7
$: xinput get-button-map 15
1 2 3 4 5 6 7 8 9 10 11 12 13

```

I tried to just throw something at to see if anything would stick,
```

$: xinput set-button-map 13 1 2 3 4 5 6 7 8 9 10 11 12 13

```
with all kinds of varying combinations to the ordering... even all 0's to disable, but to no avail.

Any help, guidance, or clarification is much appreciated.

Sincerely,
~~archery~~

---

### Post by norobro on 2020-03-04
I don't know whether this will work with your laser pointer or not but you can remap keys with xmodmap. 

To map arrowup to pageup and arrowdown to pagedown run:```
xmodmap -e "keysym Down = Next" -e "keysym Up = Prior"

```To restore:```
xmodmap -e "keycode 116 = Down" -e "keycode 111 = Up"
```

Also you can put those commands in separate files:```
keysym Down = Next
keysym Up = Prior
```
```
keycode 116 = Down
keycode 111 = Up
```
and then run "xmodmap filename"

HTH

---

### Post by archeryguru2000 on 2020-03-05
Thanks @norobro!  This is at least a work around.  The only downside is that it remaps my keyboard buttons, too.  But while giving presentations I don't think this will be an issue.  I will try wrapping this in a short script to execute while presenting and the revert the mapped keys once the presentation is over.

I'll mark this as solved as it manages to get my laser pointer used.

Thanks,
~~archery~~

---

