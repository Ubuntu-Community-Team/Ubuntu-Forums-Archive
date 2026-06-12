---
title: "forward delete apple wireless keyboard"
date: 2012-04-29
forum: Hardware
---

### Post by jnm01 on 2012-04-29
The installation of an apple wireless keyboard was easy, and it worked great.  My frustration was that there is no forward delete key.  After spending hours trying to figure out how to get the Fn key to work, so that Fn-delete works as forward delete rather than backspace, I found a solution that is incredibly simple and works well for me:

_**Alter the behavior of the F12 key so that it becomes a forward delete key**_, putting a "backspace" key and a "forward delete" key close together on the keyboard.

*Instructions*
from terminal...

  xmodmap -pke

Find which code is connected to your F12 key (for me it was 96).  Now, reassign that key:

  xmodmap -e 'keycode 96 = Delete'

---

