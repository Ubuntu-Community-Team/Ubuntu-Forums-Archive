---
title: "Graphics problem.."
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by lostintranslation on 2005-06-25
Hmph.  I'm new to Linux in general, so feel free to call me a newb, but I'm having a problem that I can't solve on my own.

Ubuntu starts, goes through all the checks, and once it gives the prompt to login, an error message appears, saying:

(not a direct quote) I cannot start/run the X drivers.  Please fix the problem and try again.

The error logs (I think) for the X program are then shown, and the only thing I could get out of those was to check the X wiki site for the latest version (which I have).

Any suggestions?  Should I put up further information?

And if so, how can I do that, since I have no clue if I can even access the internet from the Ubuntu prompt (on Windows right now).

---

### Post by askreet on 2005-06-25
When it says it cant start up it'll ask if you want to view that error message.

Look for lines with (WW) and (EE) and write them down, then post them here. We should be able to tell you whats wrong from those :D

Good luck.

---

### Post by guX on 2005-06-25
I had the same problem. Run the command "sudo dpkg-reconfigure xserver-xorg", and when it asks you which driver do you want to use, select "vesa". This solution isn't ideal, but it gives you a GUI nonetheless, and you can look at drivers afterwards.

---

### Post by lostintranslation on 2005-06-25
Okay, I copied (by hand) the errors and warnings, and am posting them.

There are two error logs, however the first has the same the errors and fatal server error as the last three in the second log.  So here are the errors and warnings from the second log, as close to ver batim as I could get.

WW  The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
WW  The directory "/usr/lib/X11/fonts/CID" does not exist.
WW  `fonts.dir' not found (or not valid) in
|       "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
|               Entry deleted from font path.
|               (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
WW  Open APM failed (/dev/apm_bios) (No such file or directory).
EE  Cannot read V_BIOS
EE  VBE initialization failed
EE  Screen(s) found, but none have a usable configuration

Fatal Server Error:
no screens found.

---

### Post by Xian on 2005-06-25
Is this after you ran the command as mentioned earlier?

```
$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by lostintranslation on 2005-06-25
I tried to reconfig but it didn't affect the problem--the same error messages appeared afterwards.

---

