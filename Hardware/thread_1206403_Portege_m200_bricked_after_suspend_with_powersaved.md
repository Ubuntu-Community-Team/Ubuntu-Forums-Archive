---
title: "Portege m200 bricked after suspend with powersaved"
date: 2009-07-07
forum: Hardware
---

### Post by WMCoolmon on 2009-07-07
A few months ago, my old laptop (A Thinkpad T22) quit working, and I decided to upgrade. I bought a Portege m200 used from eBay. I was satisfied with it, so I decided to upgrade it to its max of 2GB RAM and try out a CF card with a CF-IDE adaptor to create a poor-man's solid-state disc.

The laptop had originally come with Windows XP Tablet Edition, but I didn't have an easy way of getting an install disc (though the laptop came with the CD key). So I decided to install Kubuntu 9.04 on the CF card (which was a challenge in and of itself- the m200 has no CD drive and no USB boot ability).

Once I got Kubuntu installed, I had to put up with some things not working. I was able to get the wireless networking going without more than a couple hours of fiddling around, but the function keys and standby remained disabled (even after installing FnFX).

Specifically, when I would suspend the laptop to RAM (usually by closing the lid), the m200 wouldn't actually suspend. Instead, it would show a blinking cursor and continue running at full speed. I could get out of the mode by switching to a terminal screen and back to X (Ctrl-Alt-F1 and Ctrl-Alt-F7) but this would disable wireless networking.

At the end of the academic year, I had some free time and decided to try and get suspend working. I found [these instructions on the Ubuntu wiki](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM200), which recommend installing powersaved, and decided to give it a shot.

I did `sudo apt-get install powersaved`, and was told that apmd needed to be removed, and 4-5 other packages would need to be installed. I gave apt the go-ahead and let it finish. I didn't see any messages indicating a reboot was needed, so I went ahead with a trial. I used the 'Suspend to RAM option' on the KDE menu.

The familiar blinking cursor appeared, but the laptop responded to no commands or mouse movement. The Ctrl-Alt hotkeys and Ctrl-Alt-Delete were nonresponsive, as was a soft poweroff with the power switch. So I did a hard poweroff (held the power button for a few seconds, until the laptop turned off). Then I turned it back on.

The Portege m200 has five LEDs to indicate status. One of these is a standby/power indicator. In standby, it slowly blinks amber; when the laptop is fully on, it turns green. Usually, during bootup, it's green. But when I turned the laptop on this time, the light flashed amber, as if the laptop were in standby. The fan also ran at an abnormally high speed.

To get the laptop working, I've so far tried:
- Removing and replacing the main batteries
- Running the laptop solely on the AC adaptor and solely on batteries
- Removing the clock/CMOS battery.
- Removing the miniPCI network card and what I assume is the bluetooth card.
- Swapping out the memory with the original memory the laptop came with.
- Removing the CF card and CF-IDE adaptor
- Plugging the laptop into a dock, and using the suspend button on an external keyboard.

So far, the only thing that's made any change is removing the CMOS battery - the laptop now seems to beep when it starts up or when a keyboard button is pressed.

I decided to give repairing the T22 a shot, and got it working. I plugged the CF card into it as a hard drive. Then I replaced powersaved with apmd and then tried to suspend it to RAM.

I was greeted with the blinking cursor. The standby light on the T22 also began to flash, as if it were in the process of suspending, but it remained in this state for a long time. I decided to try Ctrl-Alt-F1, and this brought me to a terminal. But when I pressed Ctrl-Alt-F7, it merely brought me back to the cursor. I did a hard power-off and powered the T22 back on, and it was fine.

I've come up with four likely causes of death for the m200:

[LIST=1]
[*]The 'used' aspect of the laptop kicked in, and it essentially died of old age
[*]The CF card drew power in a way that was never expected, and caused an early death for the laptop. I haven't found enough reported instances of people using CF cards as laptop hard disks to know whether this is likely or even plausible.
[*]Something about powersaved caused the laptop to inadvertently overclock, or otherwise put the hardware in a mode that damaged it
[*]The laptop really isn't dead, but is stuck in some kind of limbo. I've read that the m200 can retain BIOS passwords even when the clock is removed. The fact that the T22 also seemed to be stuck in some kind of midway-suspend state also seems to support this possibility.
[/LIST]

The only thing I've got left to try at this point is to hook a wire up to ground and try running it over chips that might be the BIOS to try and reset it. But I've found little information on whether that's safe or even plausible, so I'm reluctant to try that unless there's nothing left to try besides replacing the entire motherboard.

---

### Post by chaanakya_chiraag on 2010-04-16
Did you ever get it working again?  My m200 also stopped working and also displays the amber power light. Im running karmic

---

### Post by tim_termite on 2012-01-06
This is an old thread, but I have hopes to find a solutiuon for my Portege R100, which suffers from exactly the same symptoms:

- Installed Ubuntu 11.10 via USB (with Plop Boot Manager, but this is another story)
- Everything worked well until I tried enetring suspend mode
- Blinking cursor
- Pressed on/off for 5 s
- On power-on, high fan but nothing else.
- Removed all batteries, used A/C, waited all night,... to no avail.

Any suggestion how to revive the R100? - it ran so nicely under Ubuntu...

---

