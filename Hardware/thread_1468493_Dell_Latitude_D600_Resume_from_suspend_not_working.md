---
title: "Dell Latitude D600 Resume from suspend not working"
date: 2010-05-01
forum: Hardware
---

### Post by cristianrosa on 2010-05-01
Has anyone managed to get a Dell Latitud D600 resume from suspend in Lucid?
I get a blank screen (no backlight), and has to be rebooted.
This is quite a serious regression, it was working flawlessly in Karmic.
Thanks!

---

### Post by grapedaddy on 2010-05-05
On my D600, I found that it wasn't really suspended after closing the lid --the screen was just blanked, so pressing <Ctrl><Alt><F2> and then back to <Ctrl><Alt><F7> got me back to a login screen. The bad news is that since it was still running with the lid closed, it overheated. I had to change my power settings to "hibernate" instead. Although slower, that worked for me.

---

### Post by cristianrosa on 2010-05-06
I think mine does get suspended, the power led glows and fades out, and there are no cpu fan or hard disk activity. When you open the lid back, the power led will stay on but the laptop is dead. I found a bug report that may be related [#559163]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/559163")

---

### Post by NoVista on 2010-05-06
Not working here on my Dell D600, ATI 9000.
Same results as you posted.
I too think it is suspending, but unable to resume.

---

### Post by cristianrosa on 2010-05-07
Did you try to enable the pm_trace to see if you get the same problem than in the bug report?

---

### Post by grapedaddy on 2010-05-07
I just cleared up the "Mother of all can't purge fglrx" problems and got my ATI graphics working right, and now my suspend works;  it just won't resume --same as yours.

---

### Post by cristianrosa on 2010-05-08
So go and click in "This bug affects...", in the bug report so we push for a fix ;)

---

