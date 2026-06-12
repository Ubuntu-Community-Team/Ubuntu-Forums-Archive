---
title: "Microsoft MCE Keyboard Remote support?"
date: 2012-03-06
forum: Hardware
---

### Post by Dapennsta on 2012-03-06
I was wondering if anyone has gotten one of these to work with Ubuntu?

[http://http://wiki.xbmc.org/index.php?title=Microsoft_MCE_Keyboard_Remote]("http://http://wiki.xbmc.org/index.php?title=Microsoft_MCE_Keyboard_Remote")

I have the corresponding receiver and currently running Ubuntu 12.04. I have the media keys on the sides working using lirc (play, pause, etc.)but would really like full keyboard support. The mouse support would be nice but it's not required.

---

### Post by wyliecoyoteuk on 2012-03-06
You probably just need a keymap and to use the kernel rc6 remote control drivers

Install the ir-keytable package and see if it works.

[http://manpages.ubuntu.com/manpages/natty/man1/ir-keytable.1.html](http://manpages.ubuntu.com/manpages/natty/man1/ir-keytable.1.html)

The keytables live in

/lib/udev/rc_keymaps

---

### Post by Dapennsta on 2012-03-06
That worked perfectly, even the mouse works!

I didn't think it'd be so easy, thanks alot!

---

### Post by wyliecoyoteuk on 2012-03-07
For the sake of others, can you mark the thread  [SOLVED] please?

---

### Post by Gremlyn1 on 2012-04-05
Which keymap did you end up using?

---

### Post by roundhay on 2012-08-13
You will find the solution to get this keyboard working in 12.04 here

[http://www.pcmediacenter.com.au/forum/topic/46168-mce-keyboard-working-in-mythbuntu-1204/]("http://www.pcmediacenter.com.au/forum/topic/46168-mce-keyboard-working-in-mythbuntu-1204/")

There are a couple of typos in the code instructions but they are easy to spot.

Worked at first attempt.

---

### Post by decayingcorpse on 2013-02-21
sorry to renew old thread, but i'm having trouble getting this ruddy keyboard working on 12.04.

is there a brain-damaged method for major noobs like myself?

---

