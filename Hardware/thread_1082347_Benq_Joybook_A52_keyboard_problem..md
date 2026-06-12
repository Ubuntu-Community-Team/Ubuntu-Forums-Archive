---
title: "Benq Joybook A52 keyboard problem."
date: 2009-02-27
forum: Hardware
---

### Post by Bumpz on 2009-02-27
Hello there.
I have Benq Joybook A52, and I need to set up Linux for my studies. I shose ubuntu, cuz i have worked with it before and it seems to be good enough for my needs. When I set up Ubuntu 7.10 (that was some year ago, dont remember for sure), I had a keyboard problem - button "\" wrote symbol ">" and instead of "|" it was "<" when I pressed Shift. I did what I had to and deleted it, I thought that wen I'll need it next time, they have been fixed it.

Now I need Linux again to do some things with Terminal (needed for studies). I remembered the problem I had before, so I booted Live CD of Ubuntu 8.10 to see if it's worth of installing. Problem I mentioned before was still there. Now I need backslash button for programming, so its a huge problem for me. I tried Ubuntu 8.04 and OpenSUSE 11.0 to see if problem exists on other distros too and, unfortunately, it was there.

So, anyone have any ideas how to fix it? I would really appreaciate any help u can give me.

P.S. I'm latvian, so my english might not be perfect, but I hope that you understood what I wrote above. :)

---

### Post by Bumpz on 2009-02-27
Oh, I forgot to mention, that I tried all layouts available at Preferences>Keyboard.
When I boot my Windows Vista, Everest says that I have Generic 101- or 102- keyboard layout, OpenSUSE says that I have Generic 104- layout.
Changing keyboard would be the worst option, because Benq support in Latvia totally blows and I dont have any guarantee that new keyboard wouldnt be the same.

---

### Post by trksh22 on 2009-02-27
I have a hp kb 0602 and it has been acting weird like that too. My arrow buttons opens up a save screenshot window! Argh. I haven't yet found a solution but at least wanted to let you know that the problem is not isolated..

---

### Post by trksh22 on 2009-02-27
Here is what worked for me:

Try running the following from the command-line: gconftool-2 --recursive-unset /desktop/gnome/peripherals/keyboard

Log out and log back in. It worked for me...

---

### Post by Bumpz on 2009-02-28
Dunno, didn't work for me. Any other ideas?

---

### Post by trksh22 on 2009-02-28
Hmmmm, you should check out the IRC channel #ubuntu and let them know your problem there. Thats where I got help, and it was immediate. Let me know how it works, ok?

---

### Post by Bumpz on 2009-03-01
K, I'll have to set up mIRC then :D

---

