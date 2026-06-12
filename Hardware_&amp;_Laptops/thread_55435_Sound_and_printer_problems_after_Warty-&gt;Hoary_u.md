---
title: "Sound and printer problems after Warty-&gt;Hoary upgrade"
date: 2005-08-08
forum: Hardware &amp; Laptops
---

### Post by calamari on 2005-08-08
Hi,

I got greedy for new packages (had outdated Firefox) and decided to "upgrade" from Warty to Hoary. I should have known better, and now my system is fairly hosed up. I have many problems, but here are the ones related specifically to hardware:

1) Cannot print. This forced me to boot back into Windows 98 last night to print a PDF and that seriously irked me. I lost my temper in #ubuntu.. sorry to anyone who had to see that! I have a Brother HL-1440 laser printer hooked up directly to LPT1. The add new printer dialog says it doesn't detect any printers. Worked 100% perfectly in Warty, and I don't ever remember even having to install a printer, it just worked.

2) Unless I do awful hacks, I don't have sound. Applications complain that they cannot access /dev/dsp (which seems weird because cat /dev/dsp works okay). I can manually run "esd -d /dev/dsp1 &", this gives me sound.. but I didn't have to do that in Warty, and it doesn't work for certain apps like wine, and I also get error messages in mplayer. I figured out how to set up beep-media-player to access /dev/dsp1 directly (because that seems to be where my sound is hiding out), but that's not really a solution because it means I have sound in only one application. My sound card drivers are au8830 (card is a Turtle Beach Montego II A3D). Worked perfectly under Warty by default. Can I get my sound card working as it was under Warty? In fact, I'd like to revert any "upgrades" and have it working EXACTLY like it was under Warty, if that's possible. I didn't have esd then and I don't want it now if I don't need to have it. I hear pops and glitches in my audio that I don't think I had under Warty, and I blame esd.

3) I used to be able to play midi's via my Roland Sound Canvas MPU-401 midi daughterboard with the command "pmidi -p 64:0", but I no longer can. Any ideas how to fix this?  Thankfully, kmid works, although each time I reboot I have to manually turn up the "Video" volume again to hear the MIDI sound. Why aren't my settings remembered?

If these problems are unsolvable, I'll probably need to go back to Warty. What an awesome operating system. It just worked.. although the Warty packages were getting quite stale, Hoary just seems to be a lame imitation of the once proud Warty. I'm thinking about saving any Debian .deb packages (is that possible?) and my home directory files, then reinstalling Warty again. I don't want to have to re-download all those packages again (many long hours at dialup speed.. would take days). I suspect there was probably a way I could have tapped into the newer packages and not had to screw my system over with Hoary.. but it's a little late for that now and I'd just like to get my hardware going again if possible.

Thanks a lot,
Jeff

---

### Post by calamari on 2005-08-10
1) **(Solved)** Figured out how to print again.  It turns out that it was just a poorly designed dialog box... so I needed to ignore all that printer detection stuff, it was meaningless:

Gnome Menu : System : Printing : New Printer
(*) Local Printer
(*) Use another printer by specifying a port : 
Printer Port : Parallel Port #1 : Forward
Manufacturer : Brother
Model : HL-1440 : Apply

2) **(Solved)** Rebuilt my alsa drivers, and it worked, I just needed to reboot.  esd isn't causing a problem I suppose.

3) **(Solved)** pmidi -l gives the new port: 72:0.  Why did it change?  No clue.. but pmidi works now! For some reason the Video (MIDI) sound volume is now being remembered too.  Here is a shell script to play midis from the console or Gnome (filename: playmidi):

```
#! /bin/sh
# playmidi -- Programmed by Jeffry Johnston, 2005
pkill pmidi
port=(`pmidi -l | grep :`)
pmidi -p $port "$@" &
```

Solved all myself  :-P

---

