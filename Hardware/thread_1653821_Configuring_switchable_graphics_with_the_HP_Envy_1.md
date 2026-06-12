---
title: "Configuring switchable graphics with the HP Envy 14"
date: 2010-12-27
forum: Hardware
---

### Post by Cheetah1933 on 2010-12-27
Hello there. Today I am trying to configure switchable graphics on my Envy 14 so that I can play games on it (I have WINE and everything already set up.) I have a code that supposedly should let me do that, but I honestly have no idea how it works or how I'm supposed to use it.

[http://www.phoronix.com/scan.php?page=news_item&px=Nzk1NQ](http://www.phoronix.com/scan.php?page=news_item&px=Nzk1NQ)

I figured that I figured I would post a thread here to learn how to do it, rather than do it myself and having to post a help thread about why my system isn't working.

I am running Maverick Meerkat 10.10

---

### Post by gordintoronto on 2010-12-27
Have you looked at:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

If I were you, I would Google vga_switcheroo and read half a dozen articles or more.

---

### Post by ravemjr on 2010-12-27
That would've been the solution, but I can't make the commands.

I suspect that it's the kernel doesn't support vgaswitcheroo. But then again, the page says 10.10 does, while I still don't see the 'sysfs' folders required.

Tried to search for a 'vgaswitcheroo' package on Synaptics, but nothing's come up, so I ran out of ideas.

---

### Post by Cheetah1933 on 2010-12-27
> **gordintoronto said:**
> Have you looked at:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

If I were you, I would Google vga_switcheroo and read half a dozen articles or more.

I had not looked at, that seems to be exactly what I need, thank you.

---

### Post by Cheetah1933 on 2010-12-27
> **ravemjr said:**
> That would've been the solution, but I can't make the commands.

I suspect that it's the kernel doesn't support vgaswitcheroo. But then again, the page says 10.10 does, while I still don't see the 'sysfs' folders required.

Tried to search for a 'vgaswitcheroo' package on Synaptics, but nothing's come up, so I ran out of ideas.

Are you running 10.10? I found the folder just fine.

---

### Post by ravemjr on 2011-01-02
> **Cheetah1933 said:**
> Are you running 10.10? I found the folder just fine.

Hmm, now I see it just fine. Must've looked without paying too much attention.

Thanks, I will try that now...

---

### Post by Marc128000 on 2011-01-17
I've made a step by step tutorial for enabling the graphics switching in Ubuntu 10.10 for the Hp Envy laptop.
[**Tutorial**]("http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html")

---

