---
title: "How can i prevent screen from blinking/flashing when switching between X session?"
date: 2008-10-22
forum: General Help
---

### Post by nsfnd on 2008-10-22
I have an nvidia 8800 card and an asus monitor(vw222) with native 1680x1050 resolution.
My problem is;
When i do ctrl alt F8 etc. to switch x session, linux first sets the tty console's resolution then the resolution of x session you are switching to (witch is the same resolution i use in main session).
So it goes like;
Main session 1680x1050 -> Ctrl Alt F8 -> 1280x1024 tty console -> 1680x1050 switched x session. (same refresh rate same depth as main session)

These resolution change(s) makes my screen go blank for 2-3 seconds. And i dont want this to happen.

To prevent this i wanted to set tty console resolution to 1680x1050 but i couldnt, cause my nvidia8800 doesnt have 1680x1050 in it's bios grrrr.

Id like to know if there is a way to avoid this flashing when switching between x sessions.
Thanks.

---

