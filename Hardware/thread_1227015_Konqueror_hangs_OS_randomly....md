---
title: "Konqueror hangs OS randomly..."
date: 2009-07-30
forum: Hardware
---

### Post by FredDie3785 on 2009-07-30
Hello.
When I'm browsing internet with Konqueror, which I think is very good browser, my cursor stops functioning properly.
I can use it only on the site which is hanged, I cannot close the browser with mouse, change the tab and everything else in the system. I can operate the system only with hotkeys.
That happens on random sites. Sometimes it's after few minutes otherwise after few hours. I've opened Konqueror with console, but it told me nothing when hanged. Here's the xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
That xorg may look weird, but it worked earlier.

---

### Post by gunksta on 2009-07-31
Interesting problem. 

I don't think the problem is hiding in your xorg file though. The fact that your mouse continues to work, etc. makes me think X is working more or less OK.

We need to figure out what process is hanging the computer. If you can switch to a tty (Ctrl-Alt-F1) OR run a process monitor NEXT to konqueror, so you can still see it when Konqi hangs, it will be easier to figure out what's going on.  If you're working with a wide-screen computer, doing the latter is easier. Just run the process monitor and make sure it puts applications in order of DESCENDING CPU usage. I suspect we will see a spike when Konqueror hangs.

There are a couple of obvious candidates to watch for. Konqi's javascript skills aren't perfect and it's possible there's some javascript on those pages that are causing it some problems (loop de loop de loop). Another obvious candidate is Flash. Although it _should_ work OK, Adobe doesn't exactly test Flash against Konqi and there is a history of problems between the two. Running 64-bit flash is one good solution (for me). But, I rarely use Konqueror for surfing the web. I tend to use FF.

---

