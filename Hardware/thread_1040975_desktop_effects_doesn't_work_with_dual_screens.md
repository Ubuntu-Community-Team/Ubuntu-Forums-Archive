---
title: "desktop effects doesn't work with dual screens"
date: 2009-01-16
forum: Hardware
---

### Post by charlescarroll1 on 2009-01-16
I hooked up a monitor to my laptop so I could dual screen.  Unfortunately this disabled my desktop effects and whenever I try to enable desktop effects I get an error message "desktop effects could not be enabled".  I did in fact find out that I can have the effects enabled by changing the display configuration in Catalyst Control Center to have the screens one on top of the other instead of side by side.  I really would like to have them side by side instead on top of each other.  Any suggestions?

---

### Post by bonfire89 on 2009-01-16
if anything comes up when you type

```
lspci | grep 945GM
```


you and I are looking for the same yet to be found solution.


searching  "945GM ubuntu 8.10" gives a lot of hits on google, but nothing I found yet.

I have a thread going right now about it too.



More than one person needs help on this!!!

---

### Post by muc on 2009-02-18
Hi,

I've stumbled upon this thread... and I had a similar problem once

I had an ATI card and I couldn't use both screens with compiz, only one.

start 'compiz' in a terminal and look for a line like this:
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.

if the test fails, compiz won't work

in my case the maximum texture size with the ATI was 2048, but I had 2 screens with 1280x1024 each, so technically putting them "on top" of each other would have worked :P

my solution was to get a computer with a nvidia card :)

maybe this helps you - if you still have this problem

muc

---

