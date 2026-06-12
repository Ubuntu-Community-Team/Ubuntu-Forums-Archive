---
title: "corrupt screen when resuming from suspend with nvidia display drivers"
date: 2017-03-21
forum: Hardware
---

### Post by lamyseba-b on 2017-03-21
Hi everybody.

I recently installed Ubuntu 16.04 on a desktop-pc that used to work fine with 12.04.
With nouveau graphic drivers (defaults in 16.04), there was a lot of display bugs, especially when transparency was involved (startup menu). But the ACPI suspend works fine.
My graphic hardware is a nvidia chipset integrated in the motherboard: GeForce 6150SE nForce 430/integrated/SSE2
So I installed nvidia drivers (tried the 304.134 and 304.135). Everything is fine, except that the display get systematically corrupt when resuming from suspend (ACPI S3)
[ATTACH=CONFIG]274255[/ATTACH]

The only way to get correct display back is to close session, or restart computer. I found out that you can also get back a correct screen with the command
```
compiz --replace
```
I need the ACPI(S3) suspend to work without corrupting my display. Can anyone help me with this?

---

### Post by lamyseba-b on 2017-04-18
As a workaround, I launch unity after resume from suspend. This reset the display and everything is ok after this. Note that in Manjaro Linux, I do not have this bug using the same nvidia drivers. But using Ubuntu, you can do:

```
sudo nano /lib/systemd/system-sleep/display_nvidia.sh
```
```
#!/bin/sh
case $1/$2 in
  pre/*)
    echo "Going to $2..."
    ;;
  post/*)
    echo "Waking up from $2...";
    /usr/bin/unity
    ;;
esac
```

This code is a bit dirty, I haven't removed the part managing "before going to sleep". (case pre/*). And the "echo" lines are not necessaries

Also, do not forget to make it executable
```
sudo chmod +x /lib/systemd/system-sleep/display_nvidia.sh
```

---

### Post by eelie on 2017-04-30
hello, I have the same problem with my NVIDIA Quadro m4000m (on 16.04 and 17.04). Does this code above work for me card/system?

---

### Post by lamyseba-b on 2017-04-30
Hi. I suppose it should. This code just relaunch unity after resume from suspend. You can do this manually to see if it works for you:
suspend, resume, then launch blindly a terminal:
CTRL+ALT+T
then type
```
unity
```
You have to type this even if you don't see anything because the screen is corrupted
if display get ok after this, then you can apply the trick I posted to do this automatically after each resume.

---

