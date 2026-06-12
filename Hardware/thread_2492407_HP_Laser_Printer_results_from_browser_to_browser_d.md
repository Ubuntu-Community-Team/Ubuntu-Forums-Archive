---
title: "HP Laser Printer results from browser to browser differ"
date: 2023-11-09
forum: Hardware
---

### Post by markelfertig on 2023-11-09
HP Laser Printer results from browser to browser differ

I use Firefox the majority of the time, and my HP Laserjet printer works fine with it.  It also works fine with Google Chrome browser.

However, when told to print something when inside Chromiun Web Browser, it simply does nothing.

In Brave Web Browser, when told to print, it only gives the option to save a .pdf file.


Just curious why the discrepancies


[h=5][/h]

---

### Post by TheFu on 2023-11-10
Added constraints exist in the chromium snap package.  Also, Chromium doesn't get the commercial stuff that Google adds to Chrome for better or worse.  Since Google also hosts the Chromium project, this is clearly a corporate decision for differentiation reasons.  BTW, there are some other things that Chromium doesn't do that Chrome does. [https://www.computerworld.com/article/3261009/googles-chromium-browser-explained.html](https://www.computerworld.com/article/3261009/googles-chromium-browser-explained.html)

BTW, you aren't alone with Chromium.
[https://askubuntu.com/questions/1489477/chromium-browser-does-not-show-any-printers](https://askubuntu.com/questions/1489477/chromium-browser-does-not-show-any-printers)

I wish I had an easy solution for this specific issue. I seldom print, so it hasn't hit me ... well, it has, but my unrelated solution solved that issue too.

a) I installed Linux Mint instead for my desktop.  The Mint team doesn't like snaps being forced onto us, so they make non-snap programs available for many things, including Chromium.  

b) Switch to a different browser for the things you would typically use Chromium to do.  Brave is based on the same core, so it behaves much like chromium, but brave has more features/hassles around privacy and claims to be more security conscious, whatever that means.

I've used both of these options. Today, I'm using "b", though Brave is flaky sometimes and getting it working the way I prefer, inside a firejail sandbox, is less than ideal.  I switched to this mode about 6 months ago and during that time, 1 update to Brave broke my setup.  I started running Chromium under Linux Mint instead, until a few weeks later, another brave update fixed the prior issue.  I'll never know what actually changed, but that's the risk in changing software.  I only patch once a week, so when something breaks, it is pretty clear it was related to an update of some sort if it happens the first time I use the program after patching.

With brave, after you save to a PDF, just print that file from the command line.

---

