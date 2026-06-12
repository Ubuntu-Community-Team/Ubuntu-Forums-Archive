---
title: "Brother printer &quot;Processing - Waiting for printer to become available.&quot;"
date: 2019-11-07
forum: Hardware
---

### Post by merlin-zener on 2019-11-07
Hello everyone :)
apologies in advance if this is "one of those" questions....
I'm still at newbie level, I tend to not touch things unless they don't work, and they mostly work - until now.

The printer will not print.
Ubuntu sees it and shows it as "Brother HL-1110 series" in Printers in the Admin menu.
Properties shows it with a green tick and Printer State: Idle

But when I try to print something or click on "print test page", the status changes to "Waiting for printer to become available."

Please help - I've tried almost nothing and I'm out of ideas............

oh, what have I tried?
power cycling both the printer and the computer.
I've tried having the printer powered up before rebooting the computer, and also power cycling the printer while the computer is still running.

All help appreciated - I need to print out my resume [because... reasons...]
:)

---

### Post by Irihapeti on 2019-11-08
I ran into this when I first got my Brother printer, and I had to Google extensively before I found a solution, so, no, it has nothing to do with being a newbie.

You need to click on Additional Printer Settings in the Printers window and then double-click on your printer icon.

The important setting is Device URI. You probably have a generic URI. You should also have an option of something that looks something like this: 
```
usb://Brother/HL-1110%20series?serial=XXXXXXXXXXXX
```
Choose that one, click OK and the printer should now work.

Note: this is assuming you're using standard Ubuntu, and that the printer is connected using USB. If you're using another flavour of Ubuntu, you'll need to change the instructions accordingly, but the main issue of making sure you have the correct URI is still the same.

---

