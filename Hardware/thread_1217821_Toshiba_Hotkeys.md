---
title: "Toshiba Hotkeys"
date: 2009-07-20
forum: Hardware
---

### Post by old_dos_guy on 2009-07-20
I just installed ubuntu 9.04 on a Toshiba Satellite 5205-S119.  The hotkeys (Fn-F1...F10) do not work.  The only one I really need is the display output control (LCD, external monitor, TV).  I will be just as happy if someone knows how to control via terminal commands.  I need to hookup a projector to the VGA port and I would like to use the built-in TV out.

---

### Post by old_dos_guy on 2009-07-20
Did I do something wrong?  I'm not feeling the ubuntu love.  I didn't expect everyone to drop what they are doing to help me, but as it turns out this is a very simple problem to solve.  I am posting the solution in case someone looking at this thread is having the same problem.  Already installed in my distro is TOSHKEY.  The command "sudo toshset" will give you the options.  "sudo toshset -video 2" gives you internal and external monitors (0=int, 1=ext, 2=both, 3=tv).  "sudo toshset -q" will give you the current settings.  If TOSHKEY isn't already installed on your distro, just google it.

---

### Post by fig_wright on 2009-07-26
I have the same issue. However, when I try toshset, I get:
```
~$ sudo toshset 
required kernel toshiba support not enabled.

```

How do I enable that support? How come it is enabled for your kenel but not my (presumably) same one?

---

### Post by old_dos_guy on 2009-07-31
Unfortunately, I am not knowledgeable enough to answer your question and for some reason (unknown to me) those who do have the knowledge are not responding to this thread.  It is possible (uneducated guess) that the acpi-support package is not installed on your system (System>>Administration>>Synaptic Package Manager scrolled down to System Administration in the window on the left and mark acpi-support if not already checked then click on Apply).

Additionally, I found an even better solution to my video issues.  I have a nvidia card in my toshiba - at another more responsive forum someone told me to go to System>>Administration>>Hardware Drivers.  Listed there are third party drivers (not actually supported by linux) - there was one listed recommended for my nvidia.  It loaded the NVIDIA X Server which gave me GUI control of my display card which included all of the video out options.

If you need to load TOSHKEY or TOSHSET, just Google either term and you should be able to find instructions to do so.  I can't really give you meaningful advice for that because I figure out it was loaded on my system before I tried any of the posted instructions.

Good luck, hopefully something I wrote helps.  Apparently this is an old issue and the old hands on this forum are too bored or annoyed to help.  Other forums are more aware of the fact that if someone is installing Linux for the first time they are dealing with many issues and could use a little help solving what might be trivial or already solved issues to experienced users.

---

