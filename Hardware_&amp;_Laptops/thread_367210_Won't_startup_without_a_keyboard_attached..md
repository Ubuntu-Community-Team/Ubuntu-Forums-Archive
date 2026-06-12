---
title: "Won't startup without a keyboard attached."
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by brdtt12 on 2007-02-21
I have an A Open MiniPC with ubuntu installed on it that is connected to a 42" plasma tv and is located offsite. This computer is displaying information that it downloads from a server located in my office.
My question/problem is when this computer is turned on if there is no keyboard attached it will stop during startup and say no keyboard is detected. It will sit here until a keyboard is attached. Is there a way to have the computer bypass this during startup and boot without a keyboard attached. I plan on having these computers installed in 100's of locations and would like to minimize cost per location as much as possible. Any help would be appreciated. Thanks.

---

### Post by invalid on 2007-02-21
Is Ubuntu giving you this error, or does it occur before your boot loader (ie. bios)?

I have several machines with no input devices, and on one I had to disable a setting within my bios to boot regardless of the status of the keyboard.

---

### Post by slayerboy on 2007-02-21
With most motherboards, the very first thing that happens when it boots up is POST, and this basically checks The CPU, Video card, Keyboard, and memory.  On some newer systems, you can boot the computer without a keyboard.

For more info on how a computer boots up see:
[http://www.webopedia.com/DidYouKnow/Hardware_Software/2004/BootProcess.asp](http://www.webopedia.com/DidYouKnow/Hardware_Software/2004/BootProcess.asp)

and
[http://www.pcmech.com/show/internal/1057/](http://www.pcmech.com/show/internal/1057/)

Unless, of course you are getting this message when Ubuntu is trying to start, but I don't think this is the issue.  How old is the computer, what make?

---

### Post by brdtt12 on 2007-02-22
This is occurring during POST. The computer is an A Open MiniPC with an Intel Celeron M Processor 1.6GHz. Not sure what specific motherboard it is, but this was purchased a couple of months ago. So fairly new. Not sure how to go about disabling a keyboard within bios. Thanks for the help.

---

### Post by tgm4883 on 2007-02-22
go into the bios and look for something that says

Halt on:

It will probably have a list, choose one that says all but keyboard and you should be fine.  I had to do this on my old Gateway G6-400, which is pretty old.  I would think that this feature was a standard by the time your hardware was made.

---

