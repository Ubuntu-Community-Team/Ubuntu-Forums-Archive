---
title: "thunderbird crash"
date: 2008-08-26
forum: General Help
---

### Post by namelessone on 2008-08-26
I just made a custom kernel following the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158&highlight=custom+compile+kernel+hardy"), but now Thunderbird is not working.

Every time I open it, it freezes, and I watch my cpu monitor go crazy. When I boot back into my old, slow kernel, it works fine, though.

How can I fix this?

---

### Post by mssever on 2008-08-26
> **namelessone said:**
> I just made a custom kernel following the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158&highlight=custom+compile+kernel+hardy"), but now Thunderbird is not working.

Every time I open it, it freezes, and I watch my cpu monitor go crazy. When I boot back into my old, slow kernel, it works fine, though.

How can I fix this?
You probably mis-configured your kernel. Maybe your hardware can't handle some setting.

---

### Post by namelessone on 2008-08-26
But why would it be only a single program that is misbehaving? No other application that I use on a regular basis has any troubles at all.

What makes thunderbird so different?

---

### Post by mssever on 2008-08-26
> **namelessone said:**
> But why would it be only a single program that is misbehaving? No other application that I use on a regular basis has any troubles at all.

What makes thunderbird so different?
I don't know. You didn't say what specifically you changed in your custom kernel. But the fact that you only have problems with Thunderbird on your new kernel indicates that there's a problematic interaction there. Perhaps--as I suggested earlier--you misconfigured your kernel. Perhaps Thunderbird is exercising some kernel bug that was exposed by your custom build. Perhaps your new kernel is exercising some Thunderbird bug. You haven't given nearly enough information to know--or even guess--what's happening.

---

### Post by namelessone on 2008-08-27
I have a Dell Inspiron e1505 with a intel dual core processor. I did basic stuff in the kernel--optimized it for a dual core processor, changed the frequency to 1000hz, removed support for all unwanted filesystems (andrewfs), and remevd support for all networking stuff I'll never use (isdn, token ring, everything in the wan section, 1000 gb ethernet)

I ran thunderbird from the command line, but no error messages came up as it froze.

I'll probably just end up recompiling the kernel again...I probably accidentally set some random option accidentally.

---

