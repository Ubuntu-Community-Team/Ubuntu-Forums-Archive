---
title: "disabled the touchpad/trackpad when mouse is detected"
date: 2012-05-01
forum: Hardware
---

### Post by youWho on 2012-05-01
The problem was that no matter what preferences settings I tried it seemed to be impossible to disable the touchpad, and if my hand accidentally touched the touchpad while writing the cursor would jump to some random place. Since I'm not a touch typist I'd be half way through a sentence before I'd realize it too. Real pain in the booty.

I happen to have a Sony Vaio VPCF116FX but I think you can adapt this to just about any computer. I should add that I'm using Ubuntu Studio (Natty, 64 bit). And by the way I'm not using Unity.

I wrote the following simple script, which I saved as a file called "touchpad":

```
#!/bin/bash
set -o pipefail    # so exit status of a pipeline is of last command that exited with non-0 status

# chage these to the names of your touchpad/trackpad and mouse, as given by xinput:
PAD="PS/2 Mouse"
MOUSE="PIXART USB OPTICAL MOUSE"

case "$1" in
    "off" ) xinput set-prop "$PAD" "Device Enabled" 0 ;;
    "on"  ) xinput set-prop "$PAD" "Device Enabled" 1 ;;
    ""    ) 
        if xinput list-props "$MOUSE" 2>/dev/null | egrep -q 'Enabled.*1$' ; then 
            xinput set-prop "$PAD" "Device Enabled" 0
        fi
    ;;
esac

```The strings that get assigned to the variables "PAD" and "MOUSE" should be changed as needed. You can find out what to use by doing this in a terminal:

xinput list

In my case the relevant lines of output were:

&#9121; Virtual core pointer id=2 [master pointer (3)]
&#9116; &#8627; Virtual core XTEST pointer id=4 [slave pointer (2)]
&#9116; &#8627; PIXART USB OPTICAL MOUSE id=10 [slave pointer (2)]
&#9116; &#8627; PS/2 Mouse id=12 [slave pointer (2)]
&#9116; &#8627; AlpsPS/2 ALPS GlidePoint id=13 [slave pointer (2)]


By disconnecting and reconnecting the mouse and doing that it was easy to determine that my mouse is called "PIXART USB OPTICAL MOUSE". The touchpad was not as obvious but still easy to figure out. I just tried disabling and re-enabling devices until it was clear which was the one that needed to be disabled. I did in the terminal window:

xinput set-prop "AlpsPS/2 ALPS GlidePoint" "Device Enabled" 0
xinput set-prop "PS/2 Mouse" "Device Enabled" 0

to see which would disable the touchpad. It turned out that the second one did.

xinput set-prop "PS/2 Mouse" "Device Enabled" 1

re-enables it by the way.

If after you test it and get it working for your setup, you invoke the script with "off" as an argument, like:

/wherever/you/saved/the/script/touchpad off

then it'll disable the touchpad, if it's invoked with "on" as an argument then it enables the touchpad. If it's iinvoked with *no* arguments then it tests whether the mouse you specified is there and if so it disables the touchpad, but if the mouse is not detected or is not enabled then it doesn't do anything. Please note that it tests only for the specific mouse that you ask it to check for, and only by that specific name, throwing away any error messages, so you should test that it's correctly identifying that by trying the script from the terminal. By the way if the script is invoked with any other argument than "on" or "off" then it exits without doing anything.

I then added an item to "Startup Applications" that runs the script without arguments when the computer boots. If it detects the mouse it disables the touchpad, but if the mouse is not detected then it doesn't do anything.

For convenience, I also created 2 menu item "launchers" in the Applications->System Tools menu that I have in Ubuntu Studio Natty, one to disable the touchpad and the other to enable it. Those just invoke the script with "off" or "on" as an argument.

Please note that when you save the script (just write it out as a text file wherever you want to keep it) you must change the permissions on the file such that you are allowed to execute it.

As I say I don't know anything about other configurations than Ubuntu Studio (the most important difference being maybe the fact that I don't have Unity), but I think it should be pretty easy to adapt this.

Oh I should add that I saw some scripts that others had written to enable/disable the touchpad, and so thanks too to those authors. But I don't recall exactly who they were, sorry.

---

