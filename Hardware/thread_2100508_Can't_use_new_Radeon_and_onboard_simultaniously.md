---
title: "Can't use new Radeon and onboard simultaniously"
date: 2013-01-02
forum: Hardware
---

### Post by BuffaloX on 2013-01-02
Can I have FGLRX for my main, and Radeon or Vesa for my secondary?
If not, can I have both on the open source Radeon driver?

The exact cards in question are Radeon 6970 and Radeon 3000.

If I try with FGLRX it doesn't work because onboard graphics is deprecated by AMD, and no alternative driver is loaded to support it.

If I disable proprietary drivers, my graphics get really really slow and there is no compositing or OpenGL, and I still can't use the onboard graphics.I tried to reinstall the radeon driver, but it didn't make any difference.

I then tried the ATI/FireGL proprietary, because I thought that might be an older driver, but that didn't work either.

I Googled as best I could, and found many asking similar questions, but no answers.
I know this is not the fault of Ubuntu or Linux, but because AMD have chosen not to support it, I know the onboard will never be fast, but I would like to be able to use it for reference, while running 3D intensive fullscreen programs on my main monitor, and not lose half the graphics processing power just to show a chart or browser window.

If anyone knows a workaround it would be much appreciated.

---

### Post by BuffaloX on 2013-01-06
I found out that the Linux kernel can't handle multiple graphics drivers simultaneously yet. So anything requiring two different drivers won't work.

But to my surprise adding an extra monitor to my primary adapter turned out to result in very little performance loss even in games. I measured it to 2% when I had a browser open on secondary monitor.

---

