---
title: "suspend works but cant shutdown afterwards"
date: 2009-10-31
forum: Hardware
---

### Post by crisponions on 2009-10-31
Running 9.10 on a dell inspiron e1705. It has an ati x1400 and I am using the built in radeon driver. Laptop suspends and resumes almost flawlessly (screen is dim on resume, but keyboard hotkey works to increase it).

Problem is, after I have resumed if I try to shutdown the laptop later, the screen freezes with diagonal lines and I have to hard power off. The laptop shuts down w/o issue if I dont suspend at some point.

Any ideas where to start looking?

---

### Post by crisponions on 2009-11-02
Anyone else having this particular issue?  Seeing lots of suspend issues with Karmic.

---

### Post by pastalavista on 2009-11-02
I've been having some suspend problems with my Acer too. It suspends just fine but can't restart the display when it resumes. I've been looking through the new Karmic files and found a new folder /etc/default. In it there's a file called 'acpi-support' which has several work-arounds for different PCs pre-listed and just needing uncommented to put into effect. You might check and see if any apply in your case. None of them helped my problem, though.

---

### Post by crisponions on 2009-11-02
Not seeing much in that file.  From what I have gathered X is actually crashing and freezing the computer.  Tonight after resuming I tried hitting ctrl-F2 to get to a console and this caused the same X crash-computer freeze that I get when I try to shutdown after a resume.

The last thing written in the logs is in Xorg.0.log

(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.
(II) Dell WMI hotkeys: Device reopened after 1 attempts.
(II) Sleep Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"

---

### Post by crisponions on 2009-12-03
Bumping this post.  4 weeks later and the issue is still there.  I am running Fedora 12 and Suse 11.2 on the same laptop and neither of these have the issue with radeon driver locking up.  

Any way to turn on a more detailed debug to find out what exactly is happening when the freeze occurs?  I can repeat it every time.

1. Suspend laptop
2. Resume laptop
3. Shutdown (or press ctrl + f2)
4. Screen freezes with diagonal, colored lines across it.  Hard reboot is required.

I must be able to suspend my laptop so if I can't get this fixed I might have to wait for 10.4 and hope its resolved :-(

---

