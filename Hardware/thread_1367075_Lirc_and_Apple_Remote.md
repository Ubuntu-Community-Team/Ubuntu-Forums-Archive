---
title: "Lirc and Apple Remote"
date: 2009-12-29
forum: Hardware
---

### Post by permagnus on 2009-12-29
Hi,

I just bought an apple remote: [http://store.apple.com/us/product/MC377LL/A](http://store.apple.com/us/product/MC377LL/A)

I wan't to use this on with a generic ir reciever on my asus eb1012.

The reciever belongs to a generic windows media center remote and that is working perfekt.

I have been trying to create a lirc config for the apple remote and here is where my problem starts. It seems like the remote is "unstable" and a press on the meny button sends different codes depending on which button I have pressed before.

I used dmode2 to analyse the codes recieved from the remote and I do recieve codes but they are different from time to time. It is possible to se some kind of pattern and I have been able to create a lirc config that almost works. The buttons seems to register a click about 70% of the time. Some time it registers the click och the second try but not the first and so on.

Anyone who uses the remote with lirc on a non apple computer? Should I try with a different receiver?

---

### Post by permagnus on 2010-01-04
I have recorded the signals recieved using: sudo mode2 -d /dev/lirc0

You can see the result here:
[http://spreadsheets.google.com/ccc?key=0AvTiMdLE7NyrdDd1RlBuVnhxSXhZTmMtT2tMM2pSdEE&hl=en](http://spreadsheets.google.com/ccc?key=0AvTiMdLE7NyrdDd1RlBuVnhxSXhZTmMtT2tMM2pSdEE&hl=en)

Each button has been recorded three times. Anyone who could help me to
create a config for this remote?

---

### Post by isayhelloyousaygoodbye on 2010-01-20
I assume you have the second generation aluminium apple remote from Q4 2009?

You can try [http://lirc.sourceforge.net/remotes/apple/A1156](http://lirc.sourceforge.net/remotes/apple/A1156) which is for the first gen remote. Since the code includes an ID, it may not work for your remote. Also it lacks the code for the new center button.

Instead of using [http://www.lirc.org/html/mode2.html](http://www.lirc.org/html/mode2.html) to record, what happens if you use [http://www.lirc.org/html/irrecord.html](http://www.lirc.org/html/irrecord.html) ?

You might also try [http://www.lirc.org/html/irw.html](http://www.lirc.org/html/irw.html) as recommended in [http://xbmc.org/forum/showpost.php?p=398592&postcount=15](http://xbmc.org/forum/showpost.php?p=398592&postcount=15) mentioned in [http://xbmc.org/forum/showthread.php?t=65381](http://xbmc.org/forum/showthread.php?t=65381) .

If you get any results, please let me know, as I am very much interested in the key codes of the new remote (and some key combos). Thanks.

---

### Post by isayhelloyousaygoodbye on 2010-01-20
The problems are probably caused by the new remote sending *two* codes for the SELECT and Play buttons for backward compatibility:

[http://www.iospirit.com/blog/article/141/Review-Inside-the-new-Aluminum-Apple-Remote/](http://www.iospirit.com/blog/article/141/Review-Inside-the-new-Aluminum-Apple-Remote/)

---

### Post by isayhelloyousaygoodbye on 2010-01-25
I just found out that xmode2 ([http://www.lirc.org/html/xmode2.html](http://www.lirc.org/html/xmode2.html)) can be used to visualise mode2's output, which I did with a few of your recordings. Attached is a screenshot of the data from the second recording for the select/center button.

It does not look right, the high-pulses should not be as long (except for maybe two of them, see [http://www.sbprojects.com/knowledge/ir/nec.htm](http://www.sbprojects.com/knowledge/ir/nec.htm)).
So another source of error might be your hardware.

If someone happens to be able to hook up a photodiode (or possibly a red LED) to the sound input - I'd be really happy to see a recording of the commands+combos. Audacity is a decent wave editor/recorder, good for the job.
Of course, if you have a real oscilloscope or a logic analyser...

---

