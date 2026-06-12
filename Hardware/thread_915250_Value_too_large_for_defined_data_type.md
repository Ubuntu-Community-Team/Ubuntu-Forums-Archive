---
title: "Value too large for defined data type"
date: 2008-09-09
forum: Hardware
---

### Post by searles on 2008-09-09
Hello,
I'm using the current alpha of Ubuntu 8.10 (i32) on a MacBook 2nd Gen (but I don't think the problem is Apple-specific) with 2.5 GB RAM. In order to activate hibernation (like in [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)) I created a 3GB Swapfile (new partition is not an option) and everything (configuration of uswsusp) works fine but hibernation does not work. s2disk returns the message (no matter whether I use compression or not, same message for s2both)
```

$ sudo s2disk 
s2disk: Could not stat the resume device file. Reason: Value too large for defined data type

```
which is the same message I get when I try to obtain the resume offset using swap-offset:
```

$ swap-offset swapfile 
open(): Value too large for defined data type

```

I think that it's because the offset of the swapfile may not fit in a 32bit integer. Any suggestions how to resolve this?

---

### Post by archivator on 2008-12-22
I hit this exact same problem the other day. Thankfully, I know my compiler flags and managed to get a working swap-offset. 

Here's how:

1. Run **apt-get source uswsusp**
2. (I'm running jaunty, so my packages/directories might be a bit different than yours) **cd uswsusp-0.6~cvs20070618/suspend-cvs20070618**
3. Open up **Makefile** with gedit/nano/whatever and find line 19, starting with CC_FLAGS. Add **-D_FILE_OFFSET_BITS=64** to the end of that line (leaving a space before it), so that it looks like this: ```
CC_FLAGS=-I/usr/local/include -DS2RAM $(CFLAGS) -D_FILE_OFFSET_BITS=64
```
4. Save and close your editor.
5. Do a **sudo apt-get build-dep uswsusp** to download all the build dependencies. (If you don't have build-essential, now is a good time to install it)
6. **make**
7. **./swap-offset <file>** (mind the ./ - you need it to run your new version and not the one on your system PATH).

I hope that was useful ,, :)

---

