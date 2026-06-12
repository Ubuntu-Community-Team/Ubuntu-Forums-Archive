---
title: "suddenly no sound"
date: 2024-01-19
forum: Hardware
---

### Post by profe-miguel on 2024-01-19
I've been re-installing LibreOffice and OnlyOffice.  Now I have no system sound and no sound when I plug in external speakers.  I only get sound on my USB LiveChat headphones.

When I ran [LEFT][COLOR=#000000][FONT=monospace]lspci -v, I got the expected list of controllers, but many of them had a line "access denied".[/FONT][/COLOR][/LEFT]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293312&stc=1[/IMG]Here's a screenshot of a sample.  Can I fix this?  Do I need to?

---

### Post by TheFu on 2024-01-20
Assuming PulseAudio is the sound manager, uyse the **pavucontrol** program to enable the specific hardware you want to use and disable any hardware you don't want to use.

The Ubuntu Desktop Guide may be helpful: [https://help.ubuntu.com/lts/ubuntu-help/media.html.en](https://help.ubuntu.com/lts/ubuntu-help/media.html.en) - It has sections on changing output and microphones.

---

### Post by profe-miguel on 2024-01-20
Resolved using 
pacmd to determine if I was muted.  Turn out my Sound page was opening below the System Sound monitor.  How it got muted is another question.

---

