---
title: "What application enables touchpad on login?"
date: 2010-10-07
forum: Hardware
---

### Post by veko on 2010-10-07
What application enables touchpad on login? I have a Startup Application which disables it, but it's almost immediately enabled again.

I'm trying to do a seemingly trivial thing: to disable touchpad when an external mouse is plugged in.

The best I've managed to achieve is this script:[ http://ubuntuforums.org/showthread.php?t=1310844&page=2#18]("http://ubuntuforums.org/showthread.php?t=1310844&page=2#18"). I've added it to Gnome's Startup Applications. In Karmic it worked just fine, but in Lucid it does not (it does works from command line, but not as Startup Application). To figure out why, I added some debugging output into the script to see where it fails. Most importantly, I added this loop at the end of the script:

```

for count in  0 1 2 3 ; do
  echo "+++Check " $count  >> $HOME/test_touchpad
  xinput -list-props $DEVICE_ID | grep "Device Enabled" >> $HOME/test_touchpad
  sleep 1
done

```Output shows:

```

...
+++Touchpad is enabled
+++Another mouse found, disable touchpad
+++Check  0
    Device Enabled (142):    0
+++Check  1
    Device Enabled (142):    1
+++Check  2
    Device Enabled (142):    1
...

```So the script itself works and disables touchpad as can be seen from the output, but about one second after it finishes, touchpad is enabled again. I wonder why, and what application does that? And most importantly, how can I keep it off?

---

