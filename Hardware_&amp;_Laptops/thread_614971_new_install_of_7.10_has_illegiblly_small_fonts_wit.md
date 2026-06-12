---
title: "new install of 7.10 has illegiblly small fonts with nvidia 540"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by mrhua on 2007-11-16
Hello!

I have used unix before at work, but I'm just taking the plunge into unix (ubuntu!) on the desktop.

I have a newish dell desktop precision 380, that has a nvidia quadro fx 540 for a video card.

The install of 7.1 went well, although it couldn't auto detect the right nvidia card.  I installed with 'vesa' drivers.

Upon first boot, it popped up a window that indicated I had a nvidia card and did I want to download proprietary nvidia drivers.  I did.  I let it do it's cool auto install, and rebooted as it recommended.

Now, every font on the screen is too small to read; too small to even make out as letters, just tiny clumps of dots for words.  I logged in, and the entire desktop menu's were the same.  The icons were of normal size; just the text is tiny.  I started firefox -- same thing, the fonts of the menu, and the contents of what I was browsing were completely illegible.

With my limited experience playing with the live CD, I got into the control panel for fonts, and I did what I thought would max every font to the max size, but, it did no good.  While I was adjusting the font size, it did show me the "sample view" getting bigger to a point where I could read the sample text, but this was just on the font control panel.

I'm proficient at a command line but I've never played with graphics/desktops/X on a unix box before.  I did some searching on "tiny fonts" in the forums here, but didn't find anything that seemed to match up exactly.

Any help or pointing me in the right direction would be muchly appreciated.

Thanks!

MrHua

---

### Post by qamelian on 2007-11-16
If you can get into the Appearance applet under System > Preferences, go to the Fonts tab. There should be a button (can't remember the label and I'm not on my Linux box right now) near the bottom that will let you into the advanced settings. I think you'll find that the wrong DPI has been set for your card. If you adjust this setting, you should see some improvement.

---

### Post by mrhua on 2007-11-16
> **qamelian said:**
> If you can get into the Appearance applet under System > Preferences, go to the Fonts tab. There should be a button (can't remember the label and I'm not on my Linux box right now) near the bottom that will let you into the advanced settings. I think you'll find that the wrong DPI has been set for your card. If you adjust this setting, you should see some improvement.

Thanks for the reply.  That is the screen I was playing on that I managed to get to.  I changed the actual font values, but, to no avail.

The problem is, of course, is that I can't read any of the text.  I guess I'll boot into the live CD, then see what the menu looks like and where the DPI setting is, then boot back into my OS and see if I can change it.

---

### Post by markp1989 on 2007-11-26
i have the same proble with my friends computer, i installed it for him, i left and it was fine after reboot, the text is tiny

---

