---
title: "Keyboard with two spacebars"
date: 2013-11-24
forum: Hardware
---

### Post by The Jinx on 2013-11-24
Hi,

I have a SteelSeries Shift keyboard which has two spacebars one for the left and right thumb.I can't seem to get the right button to register as a spacebar click and it is driving me nuts. Any help to getting this rectified would be much appreciated.

TIA,
Jinx

---

### Post by estbadarse on 2014-05-09
I do know that this is an old thread, but it is also about the fourth result on Google (depending on your search), with none of the higher ranking articles addressing/resolving this issue directly/exclusively.
I too recently came across this issue with Xubuntu 14.04.

I was able to devise solution to the issue following the and cross-referencing the articles ranked higher in a Google search.

Following [this link]("https://wiki.archlinux.org/index.php/Extra_Keyboard_Keys#Keycodes") I was able to figure out that Ubuntu is recognising the keypress as the '*Help*' key with keycode *146*

```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'

Result: 146 Help
```

Punching that into a terminal session and pressing the the keys that you want the keycodes for will get you half way to the solution.

This [next link]("http://askubuntu.com/questions/256247/left-shift-key-increase-volume-pipe-key-works-as-shift") was able to tell me how to map the keys to a different keypress, As it turns out the solution to produce the desired outcome is the first command in the answer. 

```
[FONT=Ubuntu Mono]xmodmap -e "keycode 146 = space"[/FONT]
```
The above is all that you should need to assign the right spacebar on the Steelseries Shift to a space character I would imagine that the same thing goes for the Steelseries ZBoard

---

