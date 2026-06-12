---
title: "An Adventure In Non-HID Bluetooth Keyboard Pairing"
date: 2008-12-19
forum: Hardware
---

### Post by calraith on 2008-12-19
**Update:**  The keyboard is not as stable for an HTPC as I originally thought.  I'm giving up on it.  It worked for a while, stopped working, and refuses to regain its sanity.

I'm converting my desktop PC into a home theater PC.  A lot of searching (and even more lamenting my woefully malnourished wallet) went into my choice of keyboard.  I already had a bluetooth adapter attached to my desktop, so I decided to go for a bluetooth keyboard.  I wanted something very portable, but still large enough to allow touch-typing rather than having to thumb at the keys like an SMS on a smartphone.

For $30 U.S. shipped, I picked up a used Think Outside Stowaway Shasta for Blackberry bluetooth keyboard from eBay.  Apparently this keyboard has often been re-branded and tweaked for many different PDAs, and seems to be pretty generic as far as proprietary serial-communicating bluetooth keyboards go.

[[IMG]http://xs134.xs.to/xs134/08515/shasta-ipaqfoldable649.jpg.xs.jpg[/IMG]]("http://xs.to/xs.php?h=xs134&d=08515&f=shasta-ipaqfoldable649.jpg")

Mine is the one on the bottom.  :)

Here's what I've done so far to get the keyboard working.  I'm not positive that each of these steps has been necessary, but I'm open to corrections.

1. Right-click on the bluetooth tray applet and go to Preferences.  Go to the Services tab.  Make sure the Input and Serial services are check marked and running.  (The keyboard might only require Serial, but I also have a bluetooth mouse requiring the Input service.)   Go back to the main tab and leave the window open.

2. Hit the connect button on the keyboard (above the backspace key) and make sure the connect light is blinking.

3. Right-click on the bluetooth tray applet and go to Browse Device.  Highlight BT-FoldableKB and hit Connect.  In the Preferences window I left open in step 1, highlight the keyboard and click "Set as trusted."  At some point I had to enter 0000 to complete the pairing.

4. Dismiss the "unable to browse obex://whatever" window."  Open up a terminal.  Try to type something.  See nothing.  Swear.

5. Download, extract, make, and copy kbdd to /usr/local/bin.  You can get the kbdd source from the [kbdd homepage]("http://www.handhelds.org/moin/moin.cgi/kbdd").  I got it from CVS.

6. Get the keyboard's MAC address via the following command:

```
sudo hcitool scan
```7. sudo nano -w /etc/bluetooth/rfcomm.conf

```

#
# RFCOMM configuration file.
#

rfcomm0 {
    # Automatically bind the device at startup
    bind yes;

    # Bluetooth address of the device
    device 00:0F:6F:00:8B:3E;

    # RFCOMM channel for the connection
    channel    1;

    # Description of the connection
    comment "Think Outside Shasta";
}

```8. Add uinput to /etc/modules and sudo modprobe uinput

9. Create ~/btkeyboard.sh with the following contents:

```
#!/bin/bash

if [ ! -e /dev/rfcomm0 ]; then {
    sudo rfcomm bind rfcomm0
    sudo kbdd -t btfoldable -p /dev/rfcomm0 >/dev/null 2>&1
}; fi
```10. chmod 755 ~/btkeyboard.sh and add it to start automatically in the main Ubuntu menu --> Preferences --> Sessions.

11. Run kbdd using our script.

```
./btkeyboard.sh &
```I'm typing this post on my Shasta keyboard in front of a 67" television.  w00t!  The setup isn't perfect yet though.

If kbdd doesn't detect the keyboard, it usually errors saying rfcomm0 isn't making any sense or some such message. Sometimes when the keyboard goes to sleep or loses connectivity, kbdd doesn't die like I'd hoped.   In a couple of cases I've had to kill kbdd to stop my keyboard from repeating a character indefinitely.  For emergencies, I keep a bash script as follows on my desktop I can double-click when I need to force kbdd to stop its madness:

```
#!/bin/bash

sudo killall -9 kbdd
sudo kbdd -t btfoldable -p /dev/rfcomm0 >/dev/null 2>&1
```Eh, I'll think of something, unless you guys have any other ideas?  I haven't tried a SIGHUP.  That's another thought.

Other considerations:


[LIST]
[*]Range is severely limited.  I'm about 8 feet from my bluetooth receiver.  As the keyboard gets to the edge of its range, key presses get stuck unless I shove the keyboard into the air closer to the receiver for a second.  Putting my bluetooth adapter onto a USB extension cable and running the adapter front-and-center has helped.
[*]The most annoying thing, though, is that the question mark / slash key is not where a touch-typist would expect.  I keep accidentally hitting the up arrow when trying to type path names.  I fixed this by using xkeycaps (sudo apt-get install xkeycaps) to exchange the question / slash and the up arrow keys, and to write these changes to an xmodmap file which I load at startup.
[*]A minor thing is that my key bindings don't quite match what's printed on the keyboard, especially in the lower left.  The buttons labeled escape, menu, alt and fn are actually ctrl, fn, meta, and alt.  The Fn key converts the number row at the top to function keys (F11 and F12 are the - and + keys); the arrows to PgUp, PgDn, Home and End; and various other key combos I haven't played with yet.  Esc is the small, unlabelled button above the tilde.  The period and comma are labelled backwards, but kbdd apparently fixes this oddness in translation.  I like these bindings better than how the keys are labelled, so I'll probably just print myself some new labels to stick onto the keys or something.
[/LIST]

All-in-all, I consider this $30 well-spent, especially when I get some of the issues figured out.  It works, and can only work better the longer I screw with it.  And it feels like a laptop keyboard, but it folds up to the size of a passport when not in use.
[B]
Update:[/B] It stopped working, and it's being a pain in the ***.  I powered off my machine and unplugged all my cables so I could install a new TV tuner card, and the keyboard hasn't worked since.  Screw it.  I'm buying a cheapass $18 infrared keyboard / nubby-thing-for-a-pointing-device from a guy on eBay.  This is more trouble than it's worth.

---

