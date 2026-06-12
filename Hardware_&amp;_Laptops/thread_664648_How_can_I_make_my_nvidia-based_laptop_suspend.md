---
title: "How can I make my nvidia-based laptop suspend?"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2008-01-11
Here's the issue. I found this super-simple script that does in fact exactly what it says it does:

```
#!/bin/sh

# discover video card's ID
ID=`lspci | grep VGA | awk '{ print $1 }' | sed -e 's@0000:@@' -e 's@:@/@'`

# securely create a temporary file
TMP_FILE=`mktemp /var/tmp/video_state.XXXXXX`
trap 'rm -f $TMP_FILE' 0 1 15

# switch to virtual terminal 1 to avoid graphics
# corruption in X
chvt 1

# write all unwritten data (just in case)
sync

# dump current data from the video card to the
# temporary file
cat /proc/bus/pci/$ID > $TMP_FILE

# suspend
echo -n mem > /sys/power/state

# restore video card data from the temporary file
# on resume
cat $TMP_FILE > /proc/bus/pci/$ID

# switch back to virtual terminal 7 (running X)
chvt 7

# remove temporary file
rm -f $TMP_FILE

```

My symptoms are:

With the above script, everything "just works"
With suspending from gnome's shutdown/logout/suspend window (under System->Quit), the system goes into suspend fine, but when it comes back out, it get stuck on a VT without any getty running (I think it's F12). It won't accept any keyboard input and I have to do a hard power off to get it to shut down, and then reboot it to get it to come back.

My question is: how can I make the "normal" suspend procedure do this instead, so that suspend will work. I'm tried messing with every option that I can think of in the /etc/default/acpi-support file, but none seem to help. nVidia's documentation mentions that the program "vbetool" has alot to do with X not coming back after a suspend, but I also think that the initial "chvt 1" has something to do with it too...

Thanks.

---

